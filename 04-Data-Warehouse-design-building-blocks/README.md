### Purpose of Data Warehousing

The primary objective of a data warehouse is to enable data-driven decisions across different time horizons. A data warehouse helps organizations analyze:

1. **The Past**: Historical analysis to identify trends and patterns over time.
2. **The Present**: Real-time or near real-time analysis to monitor current operations.
3. **The Future**: Predictive analytics to forecast potential outcomes.
4. **The Unknown**: Exploratory analytics to uncover new insights and discover hidden patterns.

### Synergy Between BI and Data Warehousing

Business Intelligence (BI) and data warehousing are interdependent, evolving together:

- As **BI tools** developed, they demanded more sophisticated data warehousing solutions to handle increasingly complex queries and larger data volumes.
- In turn, **data warehousing** grew in response to the need for storing and processing vast amounts of data to provide real-time, actionable insights.

### Categories of Business Intelligence

1. **Basic Reporting**: Provides regularly generated reports for understanding business operations.
2. **OLAP (Online Analytical Processing)**: Tools that enable multidimensional analysis of data, allowing users to explore data from various perspectives.

### Dimensional Modeling

Dimensional modeling is a design technique for structuring data into fact and dimension tables, optimized for query performance:

- **Fact Tables**: Store measurable data (e.g., sales, revenue) that can be aggregated and analyzed.
- **Dimension Tables**: Contain descriptive attributes (e.g., time, product, customer) that provide context to the facts.

### Predictive and Exploratory Analytics

- **Predictive Analytics**: Uses historical data and advanced statistical models to forecast future trends.
- **Exploratory Analytics**: Involves deep dives into raw or unstructured data to uncover hidden insights.

For supporting these types of analytics, **Data Lakes** are increasingly used to store vast amounts of unstructured data, which can then be analyzed through machine learning or other advanced methods.

---

### Basic Principles of Dimensionality

When focusing on **Basic Reporting** and **OLAP**:

1. **Measurement and Context**:
   - Example question: "What is the average annual faculty salary by rank, by department, by academic year?"
   - **Measurement**: Average annual faculty salary.
   - **Context**: Rank, department, academic year.
   
2. **Understanding "By" and "For"**:
   - **By**: Groups data by values in a dimension (e.g., grouping data by department).
   - **For**: Filters data for specific values in a dimension (e.g., filtering for a specific department).

---

### Facts vs. Fact Tables vs. Dimensions vs. Dimension Tables

1. **Facts**: Numeric measurements or metrics (e.g., salary, sales volume).
   - **Fact Tables**: Store these metrics and allow aggregation for analysis.
   
2. **Dimensions**: Descriptive attributes that provide context for facts (e.g., department, product category).
   - **Dimension Tables**: Store these attributes, which provide the context to the facts in fact tables.

#### Star vs. Snowflake Schema

1. **Star Schema**:
   - Structure: All dimension hierarchy levels are in a single table.
   - Joins: Fewer joins due to the simpler design.
   - Storage: Requires more storage due to redundancy in the dimension tables.
   - Normalization: De-normalized, making it faster for queries but less efficient in storage.
   
2. **Snowflake Schema**:
   - Structure: Each level of the hierarchy is in its own table, leading to a more normalized design.
   - Joins: Requires more joins due to splitting of dimension tables.
   - Storage: Uses less storage since redundant data is minimized.
   - Normalization: More normalized, improving storage efficiency but leading to more complex queries.

### Example Comparison of Star vs. Snowflake Schema

- **Star Schema Example**:
  - Fact Table: Budget Fact
  - Dimension Tables: 
    - Academic Department DIM
    - Time DIM
    - Expense Category DIM

- **Snowflake Schema Example**:
  - Fact Table: Budget Fact
  - Dimension Tables:
    - Academic Department DIM
    - College DIM (related to Academic Department)
    - Semester DIM (related to Time DIM)
    - Academic Year DIM (related to Semester DIM)
    - Expense Category DIM
    - OPEX/CAPEX DIM (related to Expense Category)

### Additivity in Facts

1. **Additive Facts**: Can be summed up across any dimension. Example: Total Sales.
2. **Non-Additive Facts**: Cannot be summed up (e.g., ratios or averages), often used to store calculated metrics.
3. **Semi-Additive Facts**: Can be summed for some dimensions, but not others. Example: Account balance (can sum across time but not across different accounts).

---

### Database Keys in Data Warehousing

Keys are essential for defining relationships between tables and ensuring data integrity:

1. **Primary Keys**: Unique identifiers for rows in a table.
2. **Foreign Keys**: Primary keys from other tables that create relationships between tables.

#### Natural vs. Surrogate Keys

- **Natural Keys**: Come from source systems (e.g., Employee ID). These may have business meaning but can lead to data integrity issues.
- **Surrogate Keys**: System-generated keys that have no business meaning but are used to establish relationships across tables without risking data integrity issues.

**Key Design Recommendations**:
- **Use Surrogate Keys** as primary and foreign keys for consistency and data integrity.
- **Natural Keys** can be kept as secondary keys in dimension tables for reference, but they should not be used as primary keys in fact tables due to potential issues in historical tracking.

---

### Conclusion

The design and structure of a data warehouse depend on its purpose, whether it's for simple reporting, OLAP, or advanced analytics such as predictive and exploratory analysis. Understanding the differences between fact tables, dimension tables, schemas, and the role of keys in relational databases will guide decisions about how to best organize and manage your data for optimal performance and scalability.
