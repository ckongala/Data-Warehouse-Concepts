# Data Warehousing Architecture

## Centralized Data Warehouse
A **Centralized Data Warehouse** uses a single database to support business intelligence (BI) and analytics. All data from various sources is integrated into one place for ease of access and analysis.

---

## Data Marts
**Data Marts** are smaller, specialized versions of a data warehouse. They focus on a particular business unit or function and store a subset of the data from the central warehouse.

---

## Component-Based Data Warehousing
The **Component-Based Approach** utilizes multiple components, such as data warehouses and data marts, to form a complete data warehousing environment. This architecture emphasizes the idea of a broader environment rather than a single centralized database.

### Key Architectural Components:
1. **Specialized Databases (Cubes)**: We will briefly explore cubes, a form of multidimensional databases, used as part of the data warehousing environment.
2. **Operational Data Store (ODS)**: A variation of a data warehouse, useful in specific scenarios for integrating real-time operational data.

---

## Staging Layer in Data Warehousing
The **Staging Layer** is the initial segment of a data warehouse where data is loaded before transformation and integration into the warehouse. It ensures efficient data processing.

### Types of Staging Layers:
1. **Persistent Staging Layer**: Keeps data for future use, ensuring data integrity and easy access for recovery.
2. **Non-Persistent Staging Layer**: Temporary storage for immediate processing, purged after data is loaded.

---

## Building a Centralized Data Warehouse

### Overview:
- **Single Environment**: All data from various sources is fed into a single database.
- **One-Stop Shopping**: All data needed for reporting, BI, and analytics is centralized, simplifying access.

### Advantages:
- **Simplified Access**: Easy access to all data in one place.

### Challenges:
- **Technological Hurdles**: Early relational databases faced challenges handling large data volumes.
- **Trial and Error**: Data warehousing development faced many design and implementation mistakes initially.
- **Organizational Cooperation**: High collaboration is needed across different parts of the organization.

To overcome these challenges, **Data Lakes** can be used.

---

## Data Lakes

**Data Lakes** are built on big data technologies and can be seen as successors to traditional data warehouses. While data lakes are highly distributed, they can appear monolithic and centralized to users, enhancing the concept of one-stop data access.

---

## Data Warehouse vs. Data Marts

### Types of Data Marts:
1. **Dependent Data Marts**:
   - Depend on a central data warehouse.
   - Data is uniform and flows from the warehouse to the marts.

2. **Independent Data Marts**:
   - Get data directly from source applications, not from the data warehouse.
   - Data can vary across marts, leading to inconsistent architecture and potential issues with data quality.

---

## Comparing Data Warehouse and Independent Data Marts:

| Feature               | **Data Warehouse**                            | **Independent Data Mart**                      |
|-----------------------|-----------------------------------------------|------------------------------------------------|
| **Sources**           | Multiple sources (dozens or more)             | Few sources (1-6)                              |
| **ETL Process**       | Extract, transform, and load (ETL) data into the warehouse | ETL might not be uniform across marts         |
| **Data Volume**       | Large data volumes                            | Smaller, more focused datasets                 |
| **Organization**      | Organized dimensionally                       | Data may not be uniform across marts          |

Both **Data Warehouses** and **Independent Data Marts** serve to organize and provide data for analysis, but their architecture and data sources differ.

---

## Choosing Between Centralized and Component-Based Data Warehousing

### Centralized Approach
- **Advantages**: One-stop data access for the entire organization.
- **Challenges**: Requires high cross-organization cooperation and strong data governance. Small changes can have widespread effects.

### Component-Based Approach
- **Advantages**: Isolates changes and allows the use of different technologies.
- **Challenges**: May lead to inconsistent data across components and difficulty in integrating them.

---

## Types of Architected Data Warehousing

1. **Dependent Data Marts**: Examples include the **Corporate Information Factory (CIF)**, which integrates data marts with a well-defined architecture.
2. **Front-End Data Marts**: Data marts placed in front of the data warehouse to provide primary analytics.
3. **Data Warehouse Dimensional Bus**: Developed by **Ralph Kimball**, uses conformed dimensions for consistency across marts.
4. **Federated Data Warehouse**: A collection of independent data marts without integration. It’s considered a last resort due to its limitations.

### Summary:
- **Centralized Data Warehouse**: Best for simplicity and consistency.
- **Component-Based Approach**: Useful for isolating changes and mixing technologies but may cause inconsistency.
- **Federated Data Warehouse**: Generally outdated and should only be used when necessary.

---

## Including Cubes in Your Data Warehouse Environment

### What are Cubes (Multi-Dimensional Databases)?
Cubes are specialized databases that focus on data dimensions and allow fast queries for smaller datasets. Historically, cubes were used as alternatives to relational databases and were popular in products like **Express**, **SBase**, and **Power Play**.

While relational databases are the default, cubes can still be useful in smaller-scale data warehouses or as part of a hybrid environment for faster query responses.

---

## Including Operational Data Stores (ODS) in Your Data Warehousing Environment

An **Operational Data Store (ODS)** focuses on current, real-time operational data, unlike a data warehouse which stores historical data.

- **Data Feeds**: ODS uses real-time data feeds from source applications, while data warehouses use batch-oriented ETL feeds.
- **Focus**: ODS answers real-time questions and supports operational decision-making.
- **Coexistence**: 
  - Option 1: Parallel feeds to both ODS and data warehouse.
  - Option 2: Data is first sent to ODS and then to the data warehouse.

While the need for separate ODSs has decreased with faster data warehouses, they are still relevant for specific applications that require real-time operational data.

---

## The Role of the Staging Layer Inside a Data Warehouse

### Importance:
The **Staging Layer** temporarily holds incoming data from source applications before it is processed and moved to the data warehouse. It ensures smooth data flow and prevents disruption in the warehouse.

- **Staging Layer**: Holds raw data temporarily before transformation.
- **User Access Layer**: Where users access the data for reports, BI, and analytics.

### Types of Staging Layers:
1. **Non-Persistent Staging Layer**:
   - Data is not retained after processing.
   - **Advantages**: Requires less storage and simplifies management.
   - **Disadvantages**: Data must be re-extracted if the user access layer gets corrupted.

2. **Persistent Staging Layer**:
   - Data is retained after processing.
   - **Advantages**: Allows for easy data rebuilding and comparison for data quality assurance.
   - **Disadvantages**: Requires more storage and can lead to uncontrolled access by power users.

### Conclusion:
Both non-persistent and persistent staging layers offer benefits and challenges. The choice between them depends on factors like storage availability, data integrity, and the need for data quality assurance.

---

This improved version enhances readability and clarity by organizing information logically, adding bullet points for lists, and ensuring consistency in terminology and formatting.
