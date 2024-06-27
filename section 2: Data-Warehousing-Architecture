
Data Warehousing Architecture:

	**Centralized Data Warehouse:**
		Centralized Data Warehouse: Uses a single database to support business intelligence and analytics.
		
	Data Marts:
		Data Marts: Smaller, more focused versions of a data warehouse.

	Component-Based Data Warehousing:
		Component-Based Approach: Multiple components (data warehouses and data marts) work together to form an overall data warehousing environment.Emphasizes the word environment, not a single centralized database.
		
	Architectural Options:
		Specialized Databases (Cubes): We'll briefly look at using cubes as part of your data warehousing environment.
		Operational Data Store: A variation of a data warehouse, useful for certain architectures.
		
	Staging Layer:
		Staging Layer: The initial segment of the data warehouse where data is loaded before transformation and integration.
		Types of Staging Layers:
			Persistent Staging Layer: Keeps data for future use.
			Non-Persistent Staging Layer: Temporary storage for immediate processing.
			
Build a Centralized Data Warehouse:

	Single Environment: All data from various sources feeds into a single database.
	One-Stop Shopping: All the data needed for reporting, business intelligence, and analytics is in one place, like a data supermarket.
		
	Advantages:
		Simplified Access: Easy access to all data in one location.
		
	Challenges:
		Technological Hurdles: Early relational databases were new and faced many challenges with large data volumes.
		Trial and Error: Early data warehousing was developed through trial and error, leading to mistakes in design and implementation.
		Organizational Cooperation: High level of cooperation needed across different parts of the organization, which can be difficult to achieve.
		
	To over come these challenges we go for data Lakes:
		Data Lakes:
			Built on big data technology, data lakes can be seen as a successor to traditional data warehouses.
			While data lakes are highly distributed, they often appear monolithic and centralized to users, enhancing the idea of one-stop shopping for data.

	In summary, while a centralized data warehouse offers simplicity and ease of access, it has historically faced technological and organizational challenges. 
	However, with modern advancements and the emergence of data lakes, achieving a centralized approach to data for business decision-making is becoming more feasible.

Compare a Data Warehouse to a Data Marts:
	Types of Data Marts:
		Dependent Data Marts:
			Dependent on a Data Warehouse: They draw data from the data warehouse. Without a data warehouse, they can't function.
			Uniform Data: Typically have mostly uniform data across all marts.
			Straightforward Architecture: Data flows from the warehouse to the marts in an organized manner.

		Independent Data Marts:
		   Independent from a Data Warehouse: They get data directly from source applications, not from a data warehouse.
		   No Uniformity: Data is often not uniform across marts, and key data like customers or products might be represented differently in each mart.
		   Complex Architecture: Results in a "spaghetti architecture" with multiple lines of data feeding into various marts directly from source systems.

	Comparing Data Warehouses and Independent Data Marts:
	Data Warehouse:
	  Multiple Sources: Usually have dozens or even hundreds of data sources.
	  ETL Process: Data is extracted, transformed, and loaded (ETL) directly into the warehouse.
	  Large Data Volumes: Handles very large data volumes.
	  Dimensional Organization: Data is organized dimensionally.

	Independent Data Mart:
	  Fewer Sources: Typically between 1 to 6 sources.
	  Similar to Data Warehouse: Other properties are similar to those of a data warehouse, except for the number of data sources.

	The distinction between data warehouses and independent data marts can be blurred. Both serve to organize and provide data for analysis, but their structure and sources differ. 
	Think of them as different tools in your data management toolkit, each with its own strengths and best use cases.


Decide Which Component-Based Architecture is your best fit:

	Centralized vs. Component-Based Data Warehousing:
	
	Centralized Environment:
		Advantages: Offers "one-stop shopping" for data, leveraging modern technology for success.
		Challenges: Requires high cross-organization cooperation and data governance. Small changes can have widespread effects.
	Component-Based Environment:
		Advantages: Isolates changes, allows mix-and-match technology, and can overcome organizational challenges.
		Challenges: Often leads to inconsistent data across components and difficulty in cross-integrating components.
		
	Choosing Between Centralized and Component-Based Approaches:
	
	Centralized Approach:
		Enterprise Data Warehouse (EDW): Satisfies analytical needs of the entire enterprise.
		Data Lakes: Use big data technology, appearing centralized to users but distributed underneath.
	Component-Based Approach:
		Architected Path: Integrates data warehouses and data marts, with options like dependent data marts (e.g., Corporate Information Factory).
		Non-Architected Path: Independent data marts without integration, leading to inconsistent data but simpler implementation.
		
	Types of Architected Data Warehousing:

	Dependent Data Marts:
		Example: Corporate Information Factory (CIF), which follows specific rules for data access and architecture.
	Front-End Data Marts:
		Configuration: Data marts are in front of the data warehouse, with primary analytics occurring at the data mart level.
	Data Warehouse Dimensional Bus:
		Concept: Developed by Ralph Kimball, using conformed dimensions to ensure consistency across data marts.
	Last Resort: Federated Data Warehouse:
		Description: Collection of independent data marts with no integration, leading to different answers for the same queries.
		Recommendation: Only use as a last resort due to its limitations and the proliferation of data marts.
	Summary:
		Default Choice: Aim for a centralized data warehouse for simplicity and consistency.
		Component-Based Approach: Useful for isolating changes and mixing technologies but can lead to inconsistency.
		Federated Data Warehouse: Considered outdated and should be avoided unless necessary.


Include Cubes in your Data warehouse environment:
	Cubes (Multi-Dimensional Databases):
		Not a relational database.
		Specialized database aware of data dimensions.
		Used historically as an alternative to RDBMSs.
		Cubes were a leading alternative. Products like Express, SBase, and Power Play were built on cubes. Still used, mainly for smaller scale data warehouses and data marts.
		Rigid data structure. Structural changes are complex and time-consuming. More variation compared to relational databases.
	In summary, while relational databases are the default choice, cubes provide fast query response for smaller data sets and can be a valuable part of a mixed data warehousing environment.

Include Operational Data Stores in your Data Warehousing Environment:

	An ODS focuses on current operational data, unlike a data warehouse which focuses on historical data.
	Data Feeds: ODS uses real-time data feeds from source applications, while data warehouses use batch-oriented ETL feeds.
	Primary Focus: What's happening right now, using current data integrated from various sources.
	Business Intelligence: Helps answer real-time questions, unlike historical or predictive analytics.
	ODSs were popular for operational decision-making, while data warehouses focused on strategic decisions.
	Coexistence:
		Option 1: Parallel feeds from source systems to both ODS and data warehouse.
		Option 2: Data first sent to ODS, then to the data warehouse.
	Faster, more up-to-date data warehouses with less latency have reduced the need for separate ODS.
	An ODS is crucial for real-time operational data, unlike data warehouses that focus on historical data. 
	Although their use has declined with advancements in big data and faster data warehousing, ODSs remain relevant for specific critical applications.

Explore the Role of the Staging Layer Inside a Data Warehouse:

	Staging Layer Importance:
		Every data warehouse needs a staging layer to temporarily hold incoming data from source applications.
		Think of it as a landing zone for data before it's processed and moved into the data warehouse.
		Data from source applications is quickly and non-intrusively copied to the staging layer. This process is part of the Extraction (E) in ETL (Extract, Transform, Load).
		Two Layers:
			Staging Layer: Holds raw data temporarily.
			User Access Layer: Where users access data for reports, BI, and analytics. This is what users see as the data warehouse.
		Includes star schemas, snowflake schemas, fact tables, and dimension tables.
		Focus on extracting data (E), not transforming it. Push transformations into the data warehousing environment, not the source applications.
		Inshort:-
		The staging layer is essential for handling incoming data from source applications. It temporarily holds raw data, allowing non-intrusive extraction and ensuring smooth data flow into the data warehouse. 
		This separation of extraction and transformation processes ensures efficient data management and supports robust decision-making capabilities.

Compare the two types of Staging Layers:
	Overview of Staging Layers:
		Staging Layer: Temporary holding area for incoming data from source applications before it is transformed and moved to the user access layer.
		User Access Layer: Where users access the data for reports, BI, and analytics.
		
	Non-Persistent Staging Layer:
		Data is not retained after it has been processed. The staging layer is emptied after data is moved to the user access layer.
		Adv:
			Less Storage Space: Data is not stored long-term, reducing storage requirements.
			Efficiency: Simplifies management since old data doesn't accumulate.
		DisAdv:
			Rebuilding: If the user access layer gets corrupted, data must be re-extracted from the source systems.
			Data Quality Assurance: Requires access to source systems to verify data quality, since the staging layer doesn't retain data.
			
	Persistent Staging Layer:
		Data is retained even after it has been processed and moved to the user access layer. Acts as a historical record of incoming data.
		Advantages:
			Rebuilding: If the user access layer gets corrupted, it can be rebuilt using data from the staging layer without needing to access source systems.
			Data Quality Assurance: Allows for easy comparison between the staging layer and the user access layer.
		Disadvantages:
			More Storage Space: Requires more storage since data is retained.
			Potential Uncontrolled Access: Risk of power users accessing data directly in the staging layer, bypassing governance protocols.
	Inshort:
		Both non-persistent and persistent staging layers have their own set of benefits and drawbacks. 
		The choice between them depends on factors such as storage availability, data integrity requirements, and the need for data quality assurance. 
		Understanding these differences allows us to design more effective and efficient data warehousing solutions tailored to our specific needs.
