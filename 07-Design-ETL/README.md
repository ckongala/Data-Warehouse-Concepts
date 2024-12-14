### ETL Design and Architecture for Data Warehousing

When building an ETL (Extract, Transform, Load) design, it's crucial to understand the distinction between ETL architecture and ETL design. The architecture is the overall framework for the ETL processes, while the design involves the detailed implementation steps, including managing dimension and fact tables, along with handling Slowly Changing Dimensions (SCDs). This process is vital for ensuring that data is correctly loaded into the data warehouse and can be used effectively for analytics and reporting.

---

### **ETL Architecture vs. ETL Design**

- **ETL Architecture:** 
  - Refers to the overall structure and framework that defines the extraction, transformation, and loading process.
  - It outlines the flow of data, tools, technologies, and processes used to manage data movement from the source systems to the data warehouse.
  
- **ETL Design:** 
  - Refers to the detailed implementation plan of the architecture, including how individual tables (dimensions and facts) will be populated, transformed, and maintained. This includes choosing how to handle historical changes, particularly with SCD types (1, 2, and 3).

---

### **Key ETL Design Practices**

1. **Limiting Incoming Data:**
   - Only process new or modified records to avoid unnecessary data processing and improve performance.
   
2. **Processing Dimension Tables First:**
   - Dimension tables should be processed before fact tables to ensure that any changes in the dimensions are captured before the fact data is loaded.

3. **Parallel Processing:**
   - Implement parallel processing where possible to speed up the ETL process by running multiple transformations concurrently. This can help especially when dealing with large datasets.

---

### **ETL Process for Dimension Tables**

Dimension tables are critical for providing context to fact tables and typically follow a star schema. Snowflake schemas are more complex and require processing multiple related dimension tables.

**ETL Process Overview:**
1. **Data Preparation:**
   - Filter incoming data to include only new and modified records. This minimizes the volume of data to process.
   - **Change Data Capture (CDC)** can be used to identify the changes at the source system level. CDC methods include:
     - **Timestamp Comparison:** Compare the timestamp of the incoming data with the timestamp of the last ETL run.
     - **Database Logs:** Use transaction logs to identify changes if timestamps are not available.
     - **Direct Comparison:** Compare incoming data with existing records in the data warehouse if no other CDC method is available.

2. **Transformation:**
   - Standardize and clean the data according to the common transformation model (e.g., cleaning inconsistent formats, applying business rules).
   
3. **Processing Dimension Tables:**
   - **New Rows:** Insert new rows into the dimension tables where no prior record exists.
   - **Type 1 Changes:** Apply in-place updates when the incoming data corrects previous errors (overwrites the existing data).
   - **Type 2 Changes:** Add new rows when there are significant changes, maintaining historical data (inserting a new record to capture the change and marking the previous record as expired).

---

### **Processing SCD Type 1 Changes**

**Type 1 changes** involve overwriting the existing record with new values, essentially correcting or replacing the old data without preserving historical values.

**Steps for Processing Type 1 Changes:**

1. **Data Preparation:**
   - Only process new or modified records.
   - Apply necessary transformations to clean and standardize the data.
   - Add surrogate keys for new records (alongside natural keys).

2. **Processing Type 1 Changes:**
   - When a Type 1 change occurs, a simple **SQL update** statement is used to overwrite the old value with the new one.
   - The previous value is lost because historical data is not retained.

**Example SQL for Type 1 Update:**

```sql
UPDATE Customer_DIM
SET Address = 'New Address'
WHERE Customer_ID = 101;
```

This overwrites the old address with the new one, and no historical value is preserved.

---

### **Processing SCD Type 2 Changes**

**Type 2 changes** track changes over time by inserting a new row for every change, which helps maintain historical accuracy. This approach is crucial for reporting over time, as it allows the data warehouse to reflect changes as they occurred.

**Steps for Processing Type 2 Changes:**

1. **Incoming Data:**
   - Identify the natural key (e.g., **Student_ID: TYOUN21**) from the incoming data.

2. **Generate New Surrogate Key:**
   - Use the natural key to generate a new surrogate key in the data warehouse to uniquely identify this new version of the record.

3. **Insert New Row:**
   - Insert a new row into the dimension table with the updated data and the newly generated surrogate key.
   - The new row will also include effective dates and a current flag to indicate whether it’s the most recent version.

**Example SQL for Type 2 Insert:**

```sql
-- Insert new record with updated data
INSERT INTO Customer_DIM (Customer_ID, Customer_Name, Address, Effective_Date, Expiration_Date, Current_Flag)
VALUES (101, 'John Doe', 'New Address', '2024-12-14', NULL, TRUE);

-- Expire the old record
UPDATE Customer_DIM
SET Expiration_Date = '2024-12-13', Current_Flag = FALSE
WHERE Customer_ID = 101 AND Current_Flag = TRUE;
```

This ensures that the data history is maintained, and the current record is marked as the most recent one.

---

### **ETL for Fact Tables**

Fact tables store quantitative data used for analysis, such as sales transactions, revenue, or performance metrics. The ETL process for fact tables typically uses an **append model** where new rows are added for each new set of transactional data.

**ETL Process Overview for Fact Tables:**

1. **Process Dimension Tables First:**
   - Ensure all dimension tables are updated first, especially handling Type 1 and Type 2 changes to ensure the latest surrogate keys are available for fact table processing.

2. **Fact Table ETL:**
   - **Append Model:** Add new rows to the fact table with each new set of incoming data. Each fact row is typically linked to the appropriate dimension rows via surrogate keys.
   
3. **Handling Surrogate Keys:**
   - Ensure that the correct surrogate keys are assigned to the fact table rows. These keys should correspond to the most recent dimension records (taking into account effective dates and the current flag for Type 2 changes).

**Relevant Date Usage:**
   - The transaction date (e.g., **payment date**) or another business-relevant date should be used to identify which version of a dimension key is associated with each fact record.

**Handling Multiple Versions:**
   - For Type 2 SCDs, ensure that the fact table rows reference the correct dimension version, considering the effective and expiration dates of the dimension records.

**Example SQL for Fact Table Insert:**

```sql
-- Inserting new fact record
INSERT INTO Sales_FACT (Transaction_ID, Customer_ID, Product_ID, Sale_Amount, Transaction_Date)
VALUES (101, 101, 202, 500, '2024-12-14');
```

---

### **Key Takeaways for ETL Process in Data Warehousing:**

1. **Dimension Processing:** 
   - Always process dimension tables first, handling Type 1 and Type 2 changes appropriately to ensure data integrity before dealing with fact tables.
   
2. **Surrogate Key Management:** 
   - Ensure surrogate keys are correctly assigned, especially when handling Type 2 changes or when updating fact tables with the latest dimension data.

3. **ETL Tool Assistance:**
   - Use ETL tools to automate and streamline the ETL process, especially for managing SCDs. These tools can provide built-in functions to handle Type 1, Type 2, and other changes more effectively.

By understanding the complexities of ETL processes—particularly how to handle dimension and fact tables, as well as managing historical data with SCDs—you can build an efficient and scalable data warehouse that supports accurate reporting and analytics over time.
