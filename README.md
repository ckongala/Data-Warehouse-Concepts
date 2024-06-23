Data Warehouse Concepts


**What is Data Warehouse:**<br>
	A data warehouse is typically built on top of some type of a database, so you can think of a data warehouse as the usage and the database as the platform.<br>
	It's also important to note that the data inside of a data warehouse comes from elsewhere(Operational system or External Source).<br>
	we don't create data for the firsttime in data ware house, transaction occur and are recoded in various OS, and their data is subsequently sent down to the data warehouse..<br>
	Data is copied, not moved. have rules to how we build and orginize our data warehouse..<br>
		**rule1:** Data from number of different source..<br>
		**rule2:** It should be subject oriented. (to re-orgnize the data by subject)..<br>
		**rule3:** Time Varient,(Store historical data).<br>
		**rule4:** Non-Volatile (periodically load data into data warehouse)..<br>
		Finally we all are doing this for support data-driven decision-making..<br>

**Reason for BUild Ware House:**.<br>
	**1.Support Making decions in a data-driven manner.** .<br>
		Data warehouse helps us make decisions based on data..<br>
		We need a view into the past, present, and future (or what we predict about the future) in different areas of our organization..<br>
		It even allows us to explore the unknown by using powerful analytics to discover interesting and important insights from large amounts of data..<br>
**	2. One-Stop Shopping:**.<br>
		All necessary data is stored in one location rather than being scattered across various transactional and operational applications..<br>
		This simplifies data-driven decision-making, which used to be tedious and problematic due to data being spread out..<br>
	When we combine these views of our business data, we have what is known as Business Intelligence (BI)..<br>
	Before data warehouses, data-driven decision-making involved retrieving data from multiple sources or extract files, which was time-consuming and challenging. With data warehousing, we integrate all data into one place, making it easier to focus on data analysis rather than data gathering and integration..<br>
	

  
**Compare a Data Warehouse to a Data lake:**.<br>
	Data Warehouse: Built on a relational database like Microsoft SQL Server, Oracle, or IBM's Db2(Sometimes built on a multidimensional database (cube)),Relational databases are versatile and used for transactional systems and applications, not just data warehousing..<br>
	Data Lake: Built on a big data environment, Supports rapid intake of new and changed data, Works with a variety of data types, .<br>
		Three V's of Big Data:.<br>
			**Volume**: Large amounts of data..<br>
			**Velocity**: Rapid intake of data..<br>
			**Variety**: Different types of data..<br>
	SQL (the standard relational database language) can be used for both traditional BI (business intelligence) and big data environments. This means traditional BI can be done with either a data warehouse or a data lake..<br>
	In summary, data warehouses and data lakes both support data-driven decision making, and their synergies enhance business intelligence capabilities..<br>
	
**Compare a Data Warehouse to a Data virtualization:**.<br>
**Data Virtualization:**.<br>
		Instead of copying data, access it from its original locations as needed for reports and analytics..<br>
		Unlike data warehousing, no data is copied into a separate database..<br>
		Acts as a read-only distributed database, accessing original data locations when needed..<br>
	Data virtualization can complement data warehousing and data lakes to enhance data-driven decision making through business intelligence and analytics..<br>

**Simple End-to-End Data Warehousing:**.<br>
	**Key Points:**.<br>
		Data Warehouse Construction:.<br>
			A data warehouse is built by pulling data from other applications and systems. We identify our data sources and the data warehouse itself..<br>
		**ETL Process:**.<br>
			ETL stands for Extract, Transform, and Load. ETL is a critical aspect of data warehousing, moving data from sources to the warehouse..<br>
		**Data Marts:**.<br>
			After data is in the warehouse, it can be further copied into smaller environments called data marts. Data marts are subsets of the data, tailored for specific groups of users or business functions. .<br>
  **Analogy:**.<br>
  	Think of data sources as suppliers..<br>
  	The data warehouse acts as a wholesaler that collects data from various suppliers..<br>
  	Data marts are like retailers, providing specific data subsets to users..<br>
	
