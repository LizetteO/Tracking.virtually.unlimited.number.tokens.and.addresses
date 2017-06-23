---

title: Constructing reports using metric-attribute combinations
abstract: Report construction techniques are disclosed. A first data set is received. The first data set includes a plurality of tables and a plurality of keys. One or more metric-attribute combinations is identified in the first data set. One or more dashboard reports is generated based on prioritized metric-attribute combinations from the first data set.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09652516&OS=09652516&RS=09652516
owner: Birst, Inc.
number: 09652516
owner_city: San Francisco
owner_country: US
publication_date: 20090309
---
This application claims priority to U.S. Provisional Patent Application No. 61 068 531 entitled AUTOMATIC DATA WAREHOUSE GENERATION filed Mar. 7 2008 which is incorporated herein by reference for all purposes.

Traditional data mining and profiling tools require specialized training and education to use effectively. One reason is that a great deal of statistical information is generally returned to a user and it is difficult for a lay person to determine which information is potentially of interest and what the various statistics determined for the data imply about the data.

The invention can be implemented in numerous ways including as a process an apparatus a system a composition of matter a computer program product embodied on a computer readable storage medium and or a processor such as a processor configured to execute instructions stored on and or provided by a memory coupled to the processor. In this specification these implementations or any other form that the invention may take may be referred to as techniques. In general the order of the steps of disclosed processes may be altered within the scope of the invention. Unless stated otherwise a component such as a processor or a memory described as being configured to perform a task may be implemented as a general component that is temporarily configured to perform the task at a given time or a specific component that is manufactured to perform the task. As used herein the term processor refers to one or more devices circuits and or processing cores configured to process data such as computer program instructions.

A detailed description of one or more embodiments of the invention is provided below along with accompanying figures that illustrate the principles of the invention. The invention is described in connection with such embodiments but the invention is not limited to any embodiment. The scope of the invention is limited only by the claims and the invention encompasses numerous alternatives modifications and equivalents. Numerous specific details are set forth in the following description in order to provide a thorough understanding of the invention. These details are provided for the purpose of example and the invention may be practiced according to the claims without some or all of these specific details. For the purpose of clarity technical material that is known in the technical fields related to the invention has not been described in detail so that the invention is not unnecessarily obscured.

Techniques for automatically generating a database schema e.g. for a relational database and data loading procedures for a data warehouse using metadata derived from source data files are described herein. A data warehouse is a repository of all or significant portions of data collected by entities such as the various business systems of an enterprise. With a data warehouse business data captured from diverse sources can be used for subsequent analysis and access e.g. by business users.

Typically analysis of such data requires the ability to look at that data at multiple levels. Analysis is also comparative and requires the ability to look at various measures for different parts of a business to compare them vs. each other and over time. This process of hierarchical measurement and comparison naturally leads to a dimensional model. The dimensional metaphor provides a way of describing various hierarchical measurements. In the dimensional model two concepts include measures and dimensions. Measures are measurements of data such as business data. Examples of measures include revenue sales assets number of orders etc. Measures can be analyzed across dimensions. Dimensions are ways of grouping measurements. Examples of dimensions include years months product categories sales regions etc. One example of information that can be expressed using a dimensional is the monthly sales by product.

A database schema defines the structure of a database system described in a formal language supported by a database management system DBMS . In a relational database the schema defines the tables the fields in each table and the relationships between fields and tables.

A star schema is an example of the database schema for a dimensional model. In the star schema design a single object the fact table sits in the middle and is connected to other surrounding objects dimension tables . A star schema can be simple or complex. A simple star might include as little as one fact table a more complex star has multiple fact tables. The star schema also referred to as a star join schema is an example of a data warehouse schema and includes fact tables referencing any number of dimension tables. The facts that the data warehouse helps analyze are classified along different dimensions. The fact tables typically hold the main data measures while the dimension tables describe each value of a dimension and can be joined to fact tables as needed.

As described in more detail below data warehouse generation engine reads the received source data files reads metadata stored in metadata repository and automatically generates a set of schema and data loading procedures. Also as described in more detail below dashboard engine is configured to automatically evaluate the source data and or data in data warehouse and to generate applicable reports.

Examples of different types of source data files include flat files Excel spreadsheets tables in a relational database structured data files such as XML data and data obtained via a service call to another program for example a web service or a remote procedure call . In the case of flat files fields from each record may have fixed width with padding or may be delimited by whitespace tabs commas or other characters. Source data may originate from a set of operational data stores back office systems or existing data warehouses marts.

Metadata in repository is implemented using the Extensible Markup Language XML and can also make use of any other suitable language. In some embodiments the metadata for the data warehouse schema and data loading procedures is editable using Metadata Management Tool . Augmentations include but are not limited to adding column and table transformations.

Data Warehouse which is implemented in this example by a relational database is organized around dimensions and measures or facts . The relational database is a collection of data items organized as a set of tables with each table organized into columns and rows. The schema of data warehouse comprises staging tables mapped to source data files dimension and measure tables mapped to staging tables and join relationships between dimension and dimension or measure tables. In various embodiments it also contains information about the granularity of data how data may be partitioned for performance purposes and or how that data may be indexed by the underlying relational database for performance purposes.

The creation and population of the relational database based on the data warehouse schema defined in repository may be performed in any suitable manner as applicable. For example in one embodiment data warehouse generation engine interprets the logical dimensional structure in repository automatically initializes corresponding relational database and loads data from source data into database using data loading procedures in repository by calling one or more APIs e.g. in the SQL language .

As described in more detail below using editing tool a user is able to declare the grain of a source data file and label each source data element as pertaining to a logical dimension and or as a measure. Key columns are mapped by the user to their corresponding levels in the dimensional hierarchies. For example a user may map the key column Region ID in a Business dimension to a Region level in an associated Business hierarchy. The corresponding data warehouse star including staging measure and dimension tables and joins as well as loading procedures from source files to staging and staging to warehouse tables are then generated automatically. Metadata repository stores all the metadata that defines the star schema mapping and transformations of source data files to staging tables and staging tables to measures and dimension tables. Also as described in more detail below in some embodiments system automatically performs portions of this processing reducing and in some cases eliminating the need for a user to perform such tasks.

In various embodiments the infrastructure provided by portions of system is located on and or replicated across a plurality of servers rather than the entirety of system being collocated on a single platform. Such may be the case for example if the contents of database are vast and thus distributed across multiple databases and or if system is used to provide services to many users. Whenever system performs a task such as receiving information from a user producing reports etc. either a single component or a subset of components or all components of system may cooperate to perform the task.

At metadata is set up. As described in more detail below portions of the processing may be performed manually e.g. by a user or with user input and portions of the processing may also be performed automatically. Metadata is stored in a repository such as metadata repository . For each table received at two pieces of metadata are created. The grain of each table describing the set of levels that are appropriate for each file is determined. For each column in those files a target dimension and level and whether the column is measure is also determined. Finally a set of hierarchies are created and certain levels are selected to be turned into dimension tables.

At metadata that defines a corresponding schema is generated as is the database schema. First all levels of all dimensions that are designated to be dimension tables are evaluated. For each level each source staging table is examined. If the table has a grain in the dimension of the appropriate level and the level of that grain is at or above the level in question the table is a candidate. All columns are scanned to determine which could be sources for that target dimension table. Once all source tables are scanned each dimension table is created based on all the columns from all source files that are targeted to that level. All source tables are similarly scanned to determine which columns are measures and a measure table is generated for each grain.

At the warehouse is loaded. First the system scans source tables in order to move data from those tables into target dimension tables. All source records are marked with a checksum before loading so that only changed records will be moved . The system generates inserts into the target dimension table for each staging table that is a source. Additional staging tables are joined in to supply related columns not in that table e.g. higher level keys . Higher level dimension tables also serve as lookups for keys. Levels are loaded in descending order. If the dimension table is type I i.e. only current versions of each dimension record are kept then the system does an update for any non inserted dimensional records that may have changed attributes. If the dimension table is type II i.e. history is kept dimension records that have changed are flagged as retired and inserts add the new records with the changed attributes.

Next the system scans source tables to find sources for all measure grains. In the case of snapshots old records may be truncated as applicable. In the case of inserts higher level surrogate keys are looked up from the dimension tables. Natural keys which may be composed of multiple columns are transformed into simple integer surrogate keys for performance.

At source data files are read by data warehouse generation engine and a definition of each source file is automatically generated in metadata repository . The definition of a source file includes information such as format type name and data type for each column and may be modified by the user via editor .

At corresponding definitions of staging tables are automatically created in metadata repository based on source data file representations. Based on a user s input more than one staging table may be defined based on a single source data file. A user may modify the staging table definitions using metadata editor . Staging tables serve as a temporary holding or staging place for data when it is brought into a relational database for the first time.

At the user declares the grain of each staging table using the metadata editor . The grain is declared as a reference to at least one logical dimension and a level in the associated dimensional hierarchy.

At the user declares each column in a staging table to be a source to a dimension to a fact measure or to both simultaneously using metadata editor . A user may define table transformations on a staging table and column transformations for columns in a staging table. These transformations allow data in a staging table to be altered modified before it is moved to its ultimate destination the dimension and measure tables.

The data provided at portion of the process shown in is typically provided in a flat form. The target data structures to be built by system are analytical ones based on notions of a dimensional structure such as cubes hypercubes etc. Accordingly once the keys have been determined at system attempts to assemble the information into a dynamical hierarchal structure.

At each of the columns in the source data is classified as either a measure a dimension or both. By default system classifies columns as both a measure a source for metrics and a dimension a source for dimensional attributes . Typically columns populated with numeric values are classified as both measures and dimensions and columns populated with text strings are classified only as dimensions.

At joins are determined. For example two columns with the same name and same data type are considered to be the same column and can be linked.

At system for every level of data in each dimension creates a dimension table that stores dimensional attributes. System then evaluates the source tables to determine which metrics need to be generated groups them into grains and for each grain creates a fact table.

At hierarchies are determined and combined. For example at it is determined that a particular dimension table for geography at the region level can be fed from a particular table and that geography at the city level is a lower level in the hierarchy.

In the following example suppose an analyst hereinafter Alice works for a grocery store chain and has been asked to analyze checkout data collected from a sample of markets in North America over the course of one year. As described in the following example Alice wishes to identify sales patterns and information of interest and to present a set of dashboards to the grocery store chain s managers. Alice contacts system via client and uploads sales data in the form of a MICROSOFT EXCEL file that includes five spreadsheets. Alice may interact with system in either an automatic mode in which the bulk of the processing is performed automatically by system such as by using the process of or in an advanced mode described below.

In order to process source data its grain needs to be defined first. The grain of a data source defines what a data record in the source represents. It specifies the level of detail captured in a source. In system the grain is declared as a combination of hierarchy levels. System establishes relationships between multiple sources based on key columns with identical names and the grains of the sources.

Alice can define the grain of the Cart Details data source by selecting region of the interface shown in . She creates a new hierarchy known as Sales. The Card ID and Product ID columns of the Cart Details table uniquely identify records in the Cart Details table and form a Product Sale level in the Sales hierarchy.

Analogous to the actions taken by Alice in conjunction with Alice takes the following actions For the Customers data source she creates a new hierarchy named Customers with a single level Customer mapped to the column Loyalty Card ID. For the Products data source she creates a new hierarchy named Products with two levels one level Product mapped to Product ID and a level above it named Category mapped to Category ID. For the Shopping Carts data source she modifies the existing Sales hierarchy by adding a level Cart mapped to Cart ID above the existing Product Sale level. For the Stores data source she creates a new hierarchy named Stores with a single level Store mapped to Store ID. 

Once the hierarchies and levels are in place Alice uses the interface shown in to finalize the grain definition for some sources. For Cart Details she adds the following three hierarchy level combinations to the grain definition by selecting it from the two drop downs in the Define Grain section for the source Products Product Customers Customer and Stores Store. The second two are added to the grain definition to force system to create a Sales Date version of the Quantity measure.

Alice then uses the interface shown in to remove the automatically added hierarchy level combination Sales Product Sale from Shopping Carts. Next she adds Sales Cart Customers Customer and Stores Store to the grain definition.

Before proceeding to processing the data sources the properties of all columns in a data source should be defined. Alice makes the following adjustments For the data source Cart Details she indicates that the Cart ID and Product ID columns are needed as measures. She sets the hierarchy of the Quantity column to Sales and makes the level blank. For the remaining sources she sets the column properties as shown in .

Next Alice indicates to system that the grocery data should be processed through the interface shown in . System allows users to upload new snapshots of the same data sources over time. Each time a new snapshot is uploaded it is tagged with a unique load ID and date. The load date is used for time dependent analysis. When Alice opens the Process Data page shown in system sets the load date by default to the current date.

After successfully processing the uploaded data Alice is now ready to analyze the data and build reports. She begins by building a simple report that breaks out quantity sold by each product category using tools provided by system . First she opts to view the quantity of products sold by category and is presented with the report shown in .

Alice may share the report with others e.g. via interface . Alice can also manipulate the report. For example Alice can indicate to system that she would like to see Year Month data in addition to Category Name and Quantity. 

As shown in the resulting table shows a single value for Year Month across all rows. The existing Quantity measure will report the quantity sold in relation to the load date. Since Alice has so far only loaded her data a single time only one load date exists and therefore Year Month is single valued. In order to report the quantity sold in relation to the sales date system provides another version of the Quantity measure starting with the prefix Sales Date. To see it Alice removes the Sum Quantity column from the report by clicking on the Remove chart icon and adds the measure Sum from the folder Measures Quantity By Sales Date to the report. Since the dataset contains sales data for all twelve months in 2007 instead of showing a row for each month of the year across all product categories a pivot table can be used to display the report as shown in .

The following is yet another example of how a data warehouse can be automatically generated. The first step is to map in source data files for example as explained above. One example of source data include extracts of many tables in a relational database that tracks orders for a company for a given period of time. Another example in the case of a financial services company would be all trades transactions accounts and other financial information generated in the normal course of operating the business. The files serve as sources for staging tables. Staging tables are places in a relational database where raw source data can be loaded for further processing.

In some embodiments an administrator initially sets up the general hierarchies present in the data. For example the data contains information on products and product categories. Each product category is made up of several products. That relationship can be represented in a product hierarchy where the name of the hierarchy is Product the top level is Category and the bottom level is Product. Similarly if order data is received some data will pertain to the entire order like customer etc. and other data will pertain to each order line item. An order hierarchy can be erected with both levels. Using this hierarchy the system can be instructed what granularity of data is in each staging table. As one example an Orders staging table has an Order level of the Order hierarchy selected as well as the Customer level of the Customer hierarchy and the Employee level of the employee hierarchy. That is because each order record has assigned order information a specific customer and a specific employee its grain. The order item table is one level deeper and contains information at the Order Item level of the Order hierarchy.

Schema includes fact tables and dimension tables. Fact tables include metrics to be aggregated and dimension tables include ways to group or slice these facts. Using the techniques described herein fact tables are automatically generated for each grain for which there are aggregateable metrics. In addition by clicking on a checkbox for a given level in a hierarchy the system will automatically determine the table format required to build a dimension table for that level. In some embodiments it does so by first determining which columns must be present in the dimension table at this level by scanning all columns in all staging tables that are targeted to this level . Those columns and their required data types and formats as well as the keys for each level determine what is required in that table. In addition special types of dimension tables can be supported for example like below slowly changing dimension versions of dimension tables that record history and degenerate dimension tables that are stored in the fact tables themselves . All an administrator needs to do is specify the level identify the column which uniquely defines that level a level key and then check the box to have a dimension table created for that level. Once all levels in a dimension are specified the system can determine using the dimension targets in the staging tables as well as the grain levels for each staging table what columns must be placed in which instantiated dimension table. Each column must be in a table at or below the level specified for that column.

In addition metrics can be analyzed over time and there are various ways users might want to aggregate data over time. With the techniques described herein the user can specify all the different kinds of time aggregation or shifting that one desires and all the variants of the metrics that calculate these versions are generated automatically.

Once the previous have been specified an automatic schema generation tool can be run i.e. the application can be built . When that happens definitions for many tables get created all the columns in those tables are created keys are created into those tables for later access and join relationships based on the hierarchies are also setup. During an application build previously automatically built items are removed and automatically generated items are regenerated. Surrogate keys are automatically generated and added to the hierarchies after a build. In addition new metrics are created based on columns in the staging tables using the grain of the staging table data types etc. to infer metrics . Additionally individual physical mappings are also generated each metric may exist in one or more physical tables each at a different grain of aggregation .

Dimension columns are automatically created in each dimension. And dimension columns are physically mapped to tables. Suppose there is a dimension table for Order data and a dimension table for individual order line item data. The system automatically determines based on source table grain and hierarchies which columns should go where and how they should be mapped.

Finally once the schema is determined for the warehouse load processes need to be generated to populate this schema from source staging tables. Using the techniques herein an analysis is performed of each target table against every staging table and it is determined what can be loaded from where. It then automatically generates the data load queries for the database that load the target tables from the staging tables.

In addition to providing the reporting tools described above system also provides a dashboard engine that assists users such as Alice in automatically locating information that is likely to be of interest such as to the grocery store managers. As described in more detail below dashboard engine is configured to evaluate the source data provided by Alice for metrics of interest to locate metric attribute combinations such as number of products sold per region and to populate a dashboard with reports associated with the metric attribute combinations that are likely to be of interest to Alice.

The process begins at when source data is received. For example when Alice uploads source data to system both data warehouse generation engine and dashboard engine may ingest the data at the same time. In various embodiments dashboard engine receives data including as realtime data from data warehouse generation engine relational database or another component of system rather than receiving it at the time Alice provides the source data to the system. In various embodiments dashboard engine receives data from a third party and or portions of system such as the data warehouse generation engine are omitted and the techniques described herein are adapted with respect to quick reports are used on other types of data or data sets as applicable.

At metric attribute combinations are identified and at the combinations are prioritized. Portions and portions can be performed together may be performed in either order and may be performed in a variety of ways. As one example all of the metrics extracted from source data by data warehouse generation engine may first be evaluated to determine which metrics have the least uniform statistical distribution. Metric attribution combinations include at least one metric and at least one attribute but may include additional metrics and or attributes as well. One technique for determining which metrics have the least uniform distribution is kurtosis. Other techniques may also be used such as skewness.

The metrics showing the least uniform distribution e.g. the top 10 out of 100 possible metrics then have their associated attributes evaluated again to select the combinations of metrics and attributes e.g. quantity per city that are likely to be of interest to Alice. One technique for evaluating the candidate metric attribute combinations is through the use of decision trees. Generally attributes with a higher information gain relative to a chosen metric will likely be more interesting to a user than attributes having a lower information gain. Additional techniques for selecting the most significant attributes include the use of chi squared automatic interaction detector classification and regression trees entropy and any other applicable node splitting techniques.

The metric attribute combinations are ranked e.g. based on information gain and the highest ranked combinations are used to generate reports showing such information as quantity sold per region. In various embodiments multiple reports are presented on the same screen referred to herein as a dashboard. Alice can share access to the dashboard with others users and can also interact with the dashboard e.g. by adding and removing additional attributes and or metrics from inclusion in the reporting. For example suppose one report selected for display to Alice is products by region. In various embodiments Alice is provided with an interface that allows her to refine the report so that it shows products by region by time.

The following is an example of a log file generated by an embodiment of system when processing the data described in conjunction with .

2009 03 05 17 21 38 296 0800 Pool Worker 9 INFO Starting Repository c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 repository dev.xml

2009 03 05 17 21 38 906 0800 Pool Worker 9 DEBUG File Cart Details.txt Encoding UTF 8 Separator Quote IgnoredRows 0 IgnoredLastRows 0 HasHeaders true IgnoreBackslash false

2009 03 05 17 21 38 906 0800 Pool Worker 9 DEBUG File Customers.txt Encoding UTF 8 Separator Quote IgnoredRows 0 IgnoredLastRows 0 HasHeaders true IgnoreBackslash false

2009 03 05 17 21 38 906 0800 Pool Worker 9 DEBUG File Products.txt Encoding UTF 8 Separator Quote IgnoredRows 0 IgnoredLastRows 0 HasHeaders true IgnoreBackslash false

2009 03 05 17 21 38 906 0800 Pool Worker 9 DEBUG File Shopping Carts.txt Encoding UTF 8 Separator Quote IgnoredRows 0 IgnoredLastRows 0 HasHeaders true IgnoreBackslash false

2009 03 05 17 21 38 906 0800 Pool Worker 9 DEBUG File Stores.txt Encoding UTF 8 Separator Quote IgnoredRows 0 IgnoredLastRows 0 HasHeaders true IgnoreBackslash false

2009 03 05 17 21 38 937 0800 Pool Worker 9 INFO Database connection pool created for Default Connection using connection string jdbc sqlserver localhost databaseName AcomData and driver com.microsoft.sqlserver.jdbc.SQLServerDriver

2009 03 05 17 21 39 437 0800 Pool Worker 9 INFO JDBC Driver information Microsoft SQL Server 2005 JDBC Driver 1.2.2828.100

2009 03 05 17 21 40 078 0800 Pool Worker 9 INFO Creating snowflake Cart Details Cart Details Cart Details Shopping Carts 

2009 03 05 17 21 40 140 0800 Pool Worker 9 INFO Creating snowflake Cart Details Shopping Carts Cart Details Customers Customers 

2009 03 05 17 21 40 171 0800 Pool Worker 9 INFO Creating snowflake Cart Details Shopping Carts Cart Details Stores Stores 

2009 03 05 17 21 40 203 0800 Pool Worker 9 INFO Creating snowflake Cart Details Cart Details Cart Details Shopping Carts Cart Details Customers Customers 

2009 03 05 17 21 40 234 0800 Pool Worker 9 INFO Creating snowflake Cart Details Cart Details Cart Details Shopping Carts Cart Details Stores Stores 

2009 03 05 17 21 40 343 0800 Pool Worker 9 INFO Creating snowflake Cart Details Shopping Carts Cart Details Customers Customers Cart Details Stores Stores 

2009 03 05 17 21 40 421 0800 Pool Worker 9 INFO Instantiating the cache c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 cache

2009 03 05 17 21 40 421 0800 Pool Worker 9 DEBUG Creating JDBM Record Manager c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 cache cacheMaps

2009 03 05 17 21 40 578 0800 Pool Worker 9 INFO Security Settings for Passwords min 6 max 100 upper and lower case false non alphanumeric false not contain the username false

2009 03 05 17 21 40 578 0800 Pool Worker 9 DEBUG Connection allocated for thread Thread Pool Worker 9 5 main 

2009 03 05 17 21 40 656 0800 Pool Worker 9 WARN SMI USERS either does not exist or does not have 2 username password or 4 username password fullname email columns disabling DB based authentication and authorization

2009 03 05 17 21 40 656 0800 Pool Worker 9 WARN Problems encountered when trying to create DatabaseRealm using Repository only for authentication and authorization

2009 03 05 17 21 40 781 0800 Pool Worker 9 INFO Performance Model Default Performance Model reference population does not exist Default Reference Population

2009 03 05 17 21 40 859 0800 Pool Worker 9 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.TXN COMMAND HISTORY TM DATETIME COMMAND TYPE VARCHAR 30 STEP VARCHAR 30 SUBSTEP VARCHAR 255 ITERATION VARCHAR 20 STATUS INTEGER NUMROWS BIGINT NUMERRORS BIGINT NUMWARNINGS BIGINT MESSAGE VARCHAR 1000 

2009 03 05 17 21 40 875 0800 Pool Worker 9 DEBUG CREATE INDEX DX TXN COMMAND HISTORYITERATION ON S N389a3dee ce29 4e42 90ad 44970093f745.TXN COMMAND HISTORY ITERATION 

2009 03 05 17 21 40 906 0800 Pool Worker 9 INFO Elapsed Time 0 minutes 2 seconds for Repository c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 repository dev.xml

2009 03 05 17 21 41 328 0800 Pool Worker 10 INFO Set repository variable LoadDate to value 5 Mar. 2009 

2009 03 05 17 21 41 328 0800 Pool Worker 10 INFO Elapsed Time 0 minutes 0 seconds for SetVariable LoadDate 5 Mar. 2009

2009 03 05 17 21 41 328 0800 Pool Worker 10 DEBUG Connection allocated for thread Thread Pool Worker 10 5 main 

2009 03 05 17 21 41 406 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS Cart ID INTEGER Store ID INTEGER Loyalty Card ID INTEGER Sales Date DATETIME Shopping Carts 13875573 INTEGER IDENTITY LOAD ID INTEGER ST Cart Details CKSUM INTEGER ST Shopping Carts CKSUM INTEGER 

2009 03 05 17 21 41 562 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS Cart ID INTEGER Product ID INTEGER Quantity INTEGER Shopping Carts 13875573 INTEGER Cart Details200351043 INTEGER IDENTITY LOAD ID INTEGER ST Cart Details CKSUM INTEGER 

2009 03 05 17 21 41 640 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS Loyalty Card ID INTEGER Age Group NVARCHAR 8 Gender NVARCHAR 6 Customers120094747 INTEGER IDENTITY LOAD ID INTEGER ST Customers CKSUM INTEGER ST Shopping Carts CKSUM INTEGER 

2009 03 05 17 21 41 750 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS Product ID INTEGER Category ID INTEGER Product Name NVARCHAR 10 Category Name NVARCHAR 9 Products1249892458 INTEGER IDENTITY LOAD ID INTEGER ST Products CKSUM INTEGER ST Cart Details CKSUM INTEGER 

2009 03 05 17 21 41 859 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES Store ID INTEGER Region NVARCHAR 5 City NVARCHAR 15 Type NVARCHAR 11 Stores1543357431 INTEGER IDENTITY LOAD ID INTEGER ST Stores CKSUM INTEGER ST Shopping Carts CKSUM INTEGER 

2009 03 05 17 21 41 921 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES LOAD ID INTEGER Cart Details Cart Details200351043 INTEGER Cart Details Cart ID INTEGER Cart Details Product ID INTEGER Products Products1249892458 INTEGER Products Product ID INTEGER Customers Customers120094747 INTEGER Customers Loyalty Card ID INTEGER Stores Stores1543357431 INTEGER Stores Store ID INTEGER Cart Details Shopping Carts 13875573 INTEGER Time Day ID INTEGER Time Week ID INTEGER Time Month ID INTEGER Time Quarter ID INTEGER Cart ID INTEGER Product ID INTEGER Quantity INTEGER Time Sales Date Day ID INTEGER 

2009 03 05 17 21 42 062 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES LOAD ID INTEGER Cart Details Shopping Carts 13875573 INTEGER Cart Details Cart ID INTEGER Customers Customers120094747 INTEGER Customers Loyalty Card ID INTEGER Stores Stores1543357431 INTEGER Stores Store ID INTEGER Time Day ID INTEGER Time Week ID INTEGER Time Month ID INTEGER Time Quarter ID INTEGER Cart ID INTEGER Loyalty Card ID INTEGER Store IS INTEGER Time Sales Date Day ID INTEGER 

2009 03 05 17 21 42 140 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY LOAD ID INTEGER Products Products1249892458 INTEGER Products Product ID INTEGER Time Day ID INTEGER Time Week ID INTEGER Time Month ID INTEGER Time Quarter ID INTEGER Product ID INTEGER Category ID INTEGER Unit Price FLOAT 

2009 03 05 17 21 42 234 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CUSTOMERS DAY LOAD ID INTEGER Customers Customers120094747 INTEGER Customers Loyalty Card ID INTEGER Time Day ID INTEGER Time Week ID INTEGER Time Month ID INTEGER Time Quarter ID INTEGER Loyalty Card ID INTEGER 

2009 03 05 17 21 42 281 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY LOAD ID INTEGER Stores Stores1543357431 INTEGER Stores Store ID INTEGER Time Day ID INTEGER Time Week ID INTEGER Time Month ID INTEGER Time Quarter ID INTEGER Store ID INTEGER 

2009 03 05 17 21 42 312 0800 Pool Worker 10 INFO Elapsed Time 0 minutes 0 seconds for GenerateSchema 1 notime

2009 03 05 17 21 42 312 0800 Pool Worker 10 INFO Starting LoadStaging c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data 1 loadgroup ACORN databasepath c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data numrows 1

2009 03 05 17 21 42 375 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN for 1 status Running

2009 03 05 17 21 42 375 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Cart Details for 1 status Running

2009 03 05 17 21 42 390 0800 Pool Worker 10 DEBUG Deleting format files that might be lingering over from previous unsuccessful runprematurely terminated Cart Details.txt.format.

2009 03 05 17 21 42 390 0800 Pool Worker 10 DEBUG No files found with search pattern Cart Details.txt.format

2009 03 05 17 21 42 390 0800 Pool Worker 10 DEBUG Deleting tmp files that might be lingering over from previous unsuccessful runprematurely terminated Cart Details.txt.tmp.

2009 03 05 17 21 42 390 0800 Pool Worker 10 DEBUG No files found with search pattern Cart Details.txt.tmp

2009 03 05 17 21 42 390 0800 Pool Worker 10 INFO Preprocessing source file Cart Details.txt c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Cart Details.txt 

2009 03 05 17 21 42 609 0800 Pool Worker 10 INFO Successfully preprocessed source file Cart Details.txt

2009 03 05 17 21 42 656 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.ST Cart Details Cart ID Integer Product ID Integer Quantity Integer DW DM CART DETAILS SHOPPING CARTS CKSUM INTEGER DW DM PRODUCTS PRODUCTS CKSUM INTEGER DW DM CART DETAILS CART DETAILS CKSUM INTEGER 

2009 03 05 17 21 42 734 0800 Pool Worker 10 INFO Bulk loading staging table ST Cart Details from source file Cart Details.txt

2009 03 05 17 21 42 734 0800 Pool Worker 10 DEBUG BULK INSERT S N389a3dee ce29 4e42 90ad 44970093f745.ST Cart Details FROM c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Cart Details.txt.tmp WITH FORMATFILE c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Cart Details.txt.format FIRSTROW 1 ROWS PER BATCH 12438 DATAFILETYPE widechar 

2009 03 05 17 21 42 796 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Customers for 1 status Running

2009 03 05 17 21 42 796 0800 Pool Worker 10 DEBUG Deleting format files that might be lingering over from previous unsuccessful runprematurely terminated Customers.txt.format.

2009 03 05 17 21 42 796 0800 Pool Worker 10 DEBUG No files found with search pattern Customers.txt.format

2009 03 05 17 21 42 796 0800 Pool Worker 10 DEBUG Deleting tmp files that might be lingering over from previous unsuccessful runprematurely terminated Customers.txt.tmp.

2009 03 05 17 21 42 796 0800 Pool Worker 10 DEBUG No files found with search pattern Customers.txt.tmp

2009 03 05 17 21 42 796 0800 Pool Worker 10 INFO Preprocessing source file Customers.txt c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Customers.txt .

2009 03 05 17 21 42 859 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.ST Customers Loyalty Card ID Integer Age Group NVarchar 8 Gender NVarchar 6 DW DM CUSTOMERS CUSTOMERS CKSUM INTEGER 

2009 03 05 17 21 42 921 0800 Pool Worker 10 INFO Bulk loading staging table ST Customers from source file Customers.txt

2009 03 05 17 21 42 921 0800 Pool Worker 10 DEBUG BULK INSERT S N389a3dee ce29 4e42 90ad 44970093f745.ST Customers FROM c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Customers.txt.tmp WITH FORMATFILE c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Customers .txt.format FIRSTROW 1 ROWS PER BATCH 100 DATAFILETYPE widechar 

2009 03 05 17 21 42 921 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Products for 1 status Running

2009 03 05 17 21 42 921 0800 Pool Worker 10 DEBUG Deleting format files that might be lingering over from previous unsuccessful runprematurely terminated Products.txt.format.

2009 03 05 17 21 42 921 0800 Pool Worker 10 DEBUG No files found with search pattern Products.txt.format

2009 03 05 17 21 42 921 0800 Pool Worker 10 DEBUG Deleting tmp files that might be lingering over from previous unsuccessful runprematurely terminated Products.txt.tmp.

2009 03 05 17 21 42 921 0800 Pool Worker 10 DEBUG No files found with search pattern Products.txt.tmp

2009 03 05 17 21 42 921 0800 Pool Worker 10 INFO Preprocessing source file Products.txt c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Products.txt 

2009 03 05 17 21 42 968 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.ST Products Product ID Integer Category ID Integer Product Name NVarchar 10 Category Name NVarchar 9 Unit Price FLOAT DW DM PRODUCTS PRODUCTS CKSUM INTEGER 

2009 03 05 17 21 42 984 0800 Pool Worker 10 INFO Bulk loading staging table ST Products from source file Products.txt

2009 03 05 17 21 42 984 0800 Pool Worker 10 DEBUG BULK INSERT S N389a3dee ce29 4e42 90ad 44970093f745.ST Products FROM c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Products.txt.tmp WITH FORMATFILE c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Products.txt.format FIRSTROW 1 ROWS PER BATCH 20 DATAFILETYPE widechar 

2009 03 05 17 21 42 984 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Shopping Carts for 1 status Running

2009 03 05 17 21 42 984 0800 Pool Worker 10 DEBUG Deleting format files that might be lingering over from previous unsuccessful runprematurely terminated Shopping Carts.txt.format.

2009 03 05 17 21 42 984 0800 Pool Worker 10 DEBUG No files found with search pattern Shopping Carts.txt.format

2009 03 05 17 21 42 984 0800 Pool Worker 10 DEBUG Deleting tmp files that might be lingering over from previous unsuccessful runprematurely terminated Shopping Carts.txt.tmp.

2009 03 05 17 21 42 984 0800 Pool Worker 10 DEBUG No files found with search pattern Shopping Carts.txt.tmp

2009 03 05 17 21 42 984 0800 Pool Worker 10 INFO Preprocessing source file Shopping Carts.txt c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Shopping Carts.txt 

2009 03 05 17 21 43 312 0800 Pool Worker 10 INFO Successfully preprocessed source file Shopping Carts.txt

2009 03 05 17 21 43 343 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.ST Shopping Carts Cart ID Integer Store ID Integer Loyalty Card ID Integer Sales Date DateTime Sales Date Day ID INTEGER DW DM CART DETAILS SHOPPING CARTS CKSUM INTEGER DW DM CUSTOMERS CUSTOMERS CKSUM INTEGER DW DM STORES STORES CKSUM INTEGER 

2009 03 05 17 21 43 375 0800 Pool Worker 10 INFO Bulk loading staging table ST Shopping Carts from source file Shopping Carts.txt

2009 03 05 17 21 43 375 0800 Pool Worker 10 DEBUG BULK INSERT S N389a3dee ce29 4e42 90ad 44970093f745.ST Shopping Carts FROM c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Shopping Carts.txt.tmp WITH FORMATFILE c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Shopping Carts.txt.format FIRSTROW 1 ROWS PER BATCH 3000 DATAFILETYPE widechar 

2009 03 05 17 21 43 406 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Stores for 1 status Running

2009 03 05 17 21 43 406 0800 Pool Worker 10 DEBUG Deleting format files that might be lingering over from previous unsuccessful runprematurely terminated Stores.txt.format.

2009 03 05 17 21 43 406 0800 Pool Worker 10 DEBUG No files found with search pattern Stores.txt.format

2009 03 05 17 21 43 406 0800 Pool Worker 10 DEBUG Deleting tmp files that might be lingering over from previous unsuccessful runprematurely terminated Stores.txt.tmp.

2009 03 05 17 21 43 406 0800 Pool Worker 10 INFO Preprocessing source file Stores.txt c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Stores.txt 

2009 03 05 17 21 43 453 0800 Pool Worker 10 DEBUG CREATE TABLE S N389a3dee ce29 4e42 90ad 44970093f745.ST Stores Store ID Integer Region NVarchar 5 City NVarchar 15 Type NVarchar 11 DW DM STORES STORES CKSUM INTEGER 

2009 03 05 17 21 43 468 0800 Pool Worker 10 INFO Bulk loading staging table ST Stores from source file Stores.txt

2009 03 05 17 21 43 468 0800 Pool Worker 10 DEBUG BULK INSERT S N389a3dee ce29 4e42 90ad 44970093f745.ST Stores FROM c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Stores.txt.tmp WITH FORMATFILE c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data Stores.txt.format FIRSTROW 1 ROWS PER BATCH 100 DATAFILETYPE widechar 

2009 03 05 17 21 43 828 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.ST Cart Details SET DW DM CART DETAILS SHOPPING CARTS CKSUM BINARY CHECKSUM Cart ID DW DM PRODUCTS PRODUCTS CKSUM BINARY CHECKSUM Product ID D W DM CART DETAILS CART DETAILS CKSUM BINARY CHECKSUM Cart ID Product ID Quantity 

2009 03 05 17 21 43 875 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Cart Details for 1 status Complete

2009 03 05 17 21 43 921 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.ST Customers SET DW DM CUSTOMERS CUSTOMERS CKSUM BINARY CHECKSUM Loyalty Card ID Age Group Gender 

2009 03 05 17 21 43 953 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Customers for 1 status Complete

2009 03 05 17 21 44 015 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.ST Products SET DW DM PRODUCTS PRODUCTS CKSUM BINARY CHECKSUM Product ID Category ID Product Name Category Name 

2009 03 05 17 21 44 015 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Products for 1 status Complete

2009 03 05 17 21 44 062 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.ST Shopping Carts SET DW DM CART DETAILS SHOPPING CARTS CKSUM BINARY CHECKSUM Cart ID Store ID Loyalty Card ID Sales Date DW DM CUSTOMERS CUSTOMERS CKSUM BINARY CHECKSUM Loyalty Card ID DW DM STORES STORES CKSUM BINARY CHECKSUM Store ID 

2009 03 05 17 21 44 093 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Shopping Carts for 1 status Complete

2009 03 05 17 21 44 171 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.ST Stores SET DW DM STORES STORES CKSUM BINARY CHECKSUM Store ID Region City Type 

2009 03 05 17 21 44 671 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN ST Stores for 1 status Complete

2009 03 05 17 21 44 671 0800 Pool Worker 10 DEBUG Logging step LoadStaging ACORN for 1 status Complete

2009 03 05 17 21 44 687 0800 Pool Worker 10 INFO Elapsed Time 0 minutes 2 seconds for LoadStaging c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data 1 loadgroup ACORN databasepath c SMI Data 389a3dee ce29 4e42 90ad 44970093f745 data numrows 1

2009 03 05 17 21 44 687 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN for 1 status Running

2009 03 05 17 21 45 031 0800 Pool Worker 10 DEBUG SELECT COUNT FROM S N389a3dee ce29 4e42 90ad 44970093f745.ST Cart Details

2009 03 05 17 21 45 031 0800 Pool Worker 10 DEBUG SELECT COUNT FROM S N389a3dee ce29 4e42 90ad 44970093f745.ST Customers

2009 03 05 17 21 45 031 0800 Pool Worker 10 DEBUG SELECT COUNT FROM S N389a3dee ce29 4e42 90ad 449700931745.ST Products

2009 03 05 17 21 45 031 0800 Pool Worker 10 DEBUG SELECT COUNT FROM S N389a3dee ce29 4e42 90ad 44970093f745.ST Shopping Carts

2009 03 05 17 21 45 046 0800 Pool Worker 10 DEBUG SELECT COUNT FROM S N389a3dee ce29 4e42 90ad 44970093f745.ST Stores

2009 03 05 17 21 45 046 0800 Pool Worker 10 DEBUG Order of loading dimension tables Cart Details Shopping Carts Cart Details Cart Details Customers Customers Products Products Stores Stores 

2009 03 05 17 21 45 046 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Cart Details Shopping Carts for 1 status Running

2009 03 05 17 21 45 046 0800 Pool Worker 10 INFO Starting LoadWarehouse ACORN Cart Details Shopping Carts 

2009 03 05 17 21 45 046 0800 Pool Worker 10 INFO Probing staging table ST Cart Details for DISTINCT to load Cart Details Shopping Carts

2009 03 05 17 21 45 406 0800 Pool Worker 10 INFO Inserting new records into table Cart Details Shopping Carts from staging table ST Cart Details

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS Cart ID ST Shopping Carts CKSUM LOAD ID ST Cart Details CKSUM 

2009 03 05 17 21 45 453 0800 Pool Worker 10 INFO INSERTDT 1 Cart Details Shopping Carts ST Cart Details 2976 Cart ID 2976 rows inserted

2009 03 05 17 21 45 453 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Cart Details Shopping Carts

2009 03 05 17 21 45 453 0800 Pool Worker 10 INFO Probing staging table ST Shopping Carts for DISTINCT to load Cart Details Shopping Carts

2009 03 05 17 21 45 562 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CART DETAILS SHOPPING CARTSCART DETAILSDCART IDCART DETAILSDST SHOPPING CARTS CKSUM ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS Cart ID ST Shopping Carts CKSUM 

2009 03 05 17 21 45 828 0800 Pool Worker 10 DEBUG CREATE INDEX DX ST Shopping CartsCART DETAILSDCART IDCART DETAILSDDW DM CART DETAILS SHOPPING CARTS CKSUM ON S N389a3dee ce29 4e42 90ad 44970093f745.ST Shopping Carts Cart ID DW DM CART DETAILS SHOPPING CARTS CKSUM 

2009 03 05 17 21 46 031 0800 Pool Worker 10 INFO Inserting new records into table Cart Details Shopping Carts from staging table ST Shopping Carts

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS Cart ID Store ID Loyalty Card ID Sales Date ST Cart Details CKSUM LOAD ID ST Shopping Carts CKSUM 

SELECT B.Cart ID B.Store ID B.Loyalty Card ID B.Sales Date 0 1 B.DW DM CART DETAILS SHOPPING CARTS CKSUM 

2009 03 05 17 21 46 046 0800 Pool Worker 10 INFO INSERTDT 1 Cart Details Shopping Carts ST Shopping Carts 24 Sales Date Loyalty Card ID Cart ID Store ID 24 rows inserted

2009 03 05 17 21 46 046 0800 Pool Worker 10 INFO Updating table DW DM CART DETAILS SHOPPING CARTS from staging table ST Shopping Carts

2009 03 05 17 21 46 046 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce294e4290ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS SET LOAD ID 1 Store ID B.Store ID Loyalty Card ID B.Loyalty Card ID Sales Date B.Sales Date ST Shopping Carts CKSUM B.DW DM CART DETAILS SHOPPING CARTS CKSUM 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.ST Shopping Carts B ON A.Cart ID B.Cart ID AND A.ST Shopping Carts CKSUM B.DW DM CART DETAILS SHOPPING CARTS CKSUM 

2009 03 05 17 21 46 250 0800 Pool Worker 10 INFO UPDATEDT 1 Cart Details Shopping Carts ST Shopping Carts 2976 S ales Date Loyalty Card ID Store ID 2976 rows affected

2009 03 05 17 21 46 250 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Cart Details Shopping Carts

2009 03 05 17 21 46 250 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CART DETAILS SHOPPING CARTSCART DETAILSDSHOPPING CART S 13875573 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS Shopping Carts13875573 

2009 03 05 17 21 46 328 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CART DETAILS SHOPPING CARTSCART DETAILSDCART ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS Cart ID INCLUDE Shopping Carts 13875573 

2009 03 05 17 21 46 406 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Cart Details Shopping Carts for 1 status Complete

2009 03 05 17 21 46 437 0800 Pool Worker 10 INFO Finished LoadWarehouse ACORN Cart Details Shopping Carts 

2009 03 05 17 21 46 437 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Cart Details Cart Details for 1 status Running

2009 03 05 17 21 46 484 0800 Pool Worker 10 INFO Starting LoadWarehouse ACORN Cart Details Cart Details 

2009 03 05 17 21 46 484 0800 Pool Worker 10 INFO Probing staging table ST Cart Details for DISTINCT to load Cart Details Cart Details

2009 03 05 17 21 46 546 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CART DETAILS CART DETAILSCART DETAILSDCART IDCART DETAILSDPRODUCT IDCART DETAILSDST CART DETAILS CKSUM ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS Cart ID Product ID ST Cart Details CKSUM 

2009 03 05 17 21 46 578 0800 Pool Worker 10 DEBUG CREATE INDEX DX ST Cart DetailsCART DETAILSDCART IDCART DETAILSDPRODUCT IDCART DETAILSDDW DM CART DETAILS CART DETAILS CKSUM ON S N389a3dee ce29 4e42 90ad 44970093f745.ST Cart Details Cart ID Product ID DW DM CART DETAILS CART DETAILS CKSUM 

2009 03 05 17 21 46 781 0800 Pool Worker 10 INFO Inserting new records into table Cart Details Cart Details from staging table ST Cart Details

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS Cart ID Product ID Quantity LOAD ID ST Cart Details CKSUM 

2009 03 05 17 21 46 984 0800 Pool Worker 10 INFO INSERTDT 1 Cart Details Cart Details ST Cart Details 12438 Quantity Cart ID Product ID 12438 rows inserted

2009 03 05 17 21 46 984 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Cart Details Cart Details

2009 03 05 17 21 46 984 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS SET Shopping Carts 13875573 S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS. Shopping Carts 13875573 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS ON DW DM CART DETAILS CART DETAILS.Cart ID S N389a3dee ce29 4e42 90ad 449 70093f745.DW DM CART DETAILS SHOPPING CARTS.Cart ID 

2009 03 05 17 21 47 156 0800 Pool Worker 10 WARN Unable to load dimension table Cart Details Cart Details from staging table ST Shopping Carts could not find columns in staging table that map to any dimension columns except for any potential references to natural keys

2009 03 05 17 21 47 156 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CART DETAILS CART DETAILSCART DETAILSDCART DETAILS2003 51043 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS Cart Details200351043 INCLUDE Shopping Carts 13875573 

2009 03 05 17 21 47 265 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CART DETAILS CART DETAILSCART DETAILSDCART IDCART DETAILSDPRODUCT ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS Cart ID Product ID INCLUDE Cart Details200351043 Shopping Carts 13875573 

2009 03 05 17 21 47 421 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CART DETAILS CART DETAILSCART DETAILSDCART ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS Cart ID INCLUDE Cart Details200351043 Shopping Carts 13875573 

2009 03 05 17 21 47 515 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Cart Details Cart Details for 1 status Complete

2009 03 05 17 21 47 531 0800 Pool Worker 10 INFO Finished LoadWarehouse ACORN Cart Details Cart Details 

2009 03 05 17 21 47 531 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Customers Customers for 1 status Running

2009 03 05 17 21 47 546 0800 Pool Worker 10 WARN Unable to load dimension table Customers Customers from staging table ST Cart Details natural keys not available at level Customers

2009 03 05 17 21 47 546 0800 Pool Worker 10 INFO Probing staging table ST Shopping Carts for DISTINCT to load Customers Customers

2009 03 05 17 21 47 593 0800 Pool Worker 10 INFO Inserting new records into table Customers Customers from staging table ST Shopping Carts

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS Loyalty Card ID ST Customers CKSUM LOAD ID ST Shopping Carts CKSUM 

2009 03 05 17 21 47 625 0800 Pool Worker 10 INFO INSERTDT 1 Customers Customers ST Shopping Carts 100 Loyalty Card ID 100 rows inserted

2009 03 05 17 21 47 625 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Customers Customers

2009 03 05 17 21 47 625 0800 Pool Worker 10 INFO Probing staging table ST Customers for DISTINCT to load Customers Customers

2009 03 05 17 21 47 625 0800 Pool Worker 10 DEBUG CREATE INDEX DX ST CustomersCUSTOMERSDLOYALTY CARD IDCUSTOMERSDDW DM CUSTOMERS CUSTOMERS CKSUM ON S N389a3dee ce29 4e42 90ad 44970093f745.ST Customers Loyalty Card ID DW DM CUSTOMERS CUSTOMERS CKSUM 

2009 03 05 17 21 47 640 0800 Pool Worker 10 INFO Inserting new records into table Customers Customers from staging table ST Customers

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS Loyalty Card ID Age Group Gender ST Shopping Carts CKSUM LOAD ID ST Customers CKSUM 

2009 03 05 17 21 47 656 0800 Pool Worker 10 INFO INSERTDT 1 Customers Customers ST Customers 0 Loyalty Card ID Age Group Gender 0 rows inserted

2009 03 05 17 21 47 656 0800 Pool Worker 10 INFO Updating table DW DM CUSTOMERS CUSTOMERS from staging table ST Customers

2009 03 05 17 21 47 656 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS SET LOAD ID 1 Age Group B.Age Group Gender B.Gender ST Customers CKSUM B DW DM CUSTOMERS CUSTOMERS CKSUM 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.ST Customers B ON A.Loyalty Card ID B.Loyalty Card ID AND A.ST Customers CKSUM B.DW DM CUSTOMERS CUSTOMERS CKSUM 

2009 03 05 17 21 47 703 0800 Pool Worker 10 INFO UPDATEDT 1 Customers Customers ST Customers 100 Age Group Gender 100 rows affected

2009 03 05 17 21 47 703 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Customers Customers

2009 03 05 17 21 47 703 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM CUSTOMERS CUSTOMERSCUSTOMERSDCUSTOMERS120094747 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS Customers120094747 

2009 03 05 17 21 47 734 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Customers Customers for 1 status Complete

2009 03 05 17 21 47 734 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Products Products for 1 status Running

2009 03 05 17 21 47 734 0800 Pool Worker 10 INFO Probing staging table ST Cart Details for DISTINCT to load Products Products

2009 03 05 17 21 47 750 0800 Pool Worker 10 INFO Inserting new records into table Products Products from staging table ST Cart Details

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS Product ID ST Products CKSUM LOAD ID ST Cart Details CKSUM 

2009 03 05 17 21 47 765 0800 Pool Worker 10 INFO INSERTDT 1 Products Products ST Cart Details 20 Product ID 20 rows inserted

2009 03 05 17 21 47 765 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Products Products

2009 03 05 17 21 47 765 0800 Pool Worker 10 INFO Probing staging table ST Products for DISTINCT to load Products Products

2009 03 05 17 21 47 843 0800 Pool Worker 10 DEBUG CREATE INDEX DX ST ProductsPRODUCTSDPRODUCT IDPRODUCTSDDW DM PRODUCTS PRODUCTS CKSUM ON S N389a3dee ce29 4e42 90ad 44970093f745.ST Products Product ID DW DM PRODUCTS PRODUCTS CKSUM 

2009 03 05 17 21 47 890 0800 Pool Worker 10 INFO Inserting new records into table Products Products from staging table ST Products

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS Product ID Category ID Product Name Category Name ST Cart Details CKSUM LOAD ID ST Products CKSUM 

SELECT B.Product ID B.Category ID B.Product Name B.Category Name 0 1 B.DW DM PRODUCTS PRODUCTS CKSUM 

2009 03 05 17 21 47 890 0800 Pool Worker 10 INFO INSERTDT 1 Products Products ST Products 0 Product Name Category ID Category Name Product ID 0 rows inserted

2009 03 05 17 21 47 890 0800 Pool Worker 10 INFO Updating table DW DM PRODUCTS PRODUCTS from staging table ST Products

2009 03 05 17 21 47 890 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS SET LOAD ID 1 Category ID B.Category ID Product Name B.Product Name Category Name B.Category Name ST Products CKSUM B.DW DM PRODUCTS PRODUCTS CKSUM 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.ST Products B ON A.Product ID .B.Product ID AND A.ST Products CKSUM B.DW DM PRODUCTS PRODUCTS CKSUM 

2009 03 05 17 21 47 906 0800 Pool Worker 10 INFO UPDATEDT 1 Products Products ST Products 20 Product Name Category ID Category Name 20 rows affected

2009 03 05 17 21 47 906 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Products Products

2009 03 05 17 21 47 906 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM PRODUCTS PRODUCTSPRODUCTSDPRODUCTS1249892458 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS Products1249892458 

2009 03 05 17 21 47 937 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Products Products for 1 status Complete

2009 03 05 17 21 47 937 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Stores Stores for 1 status Running

2009 03 05 17 21 47 937 0800 Pool Worker 10 WARN Unable to load dimension table Stores Stores from staging table ST Cart Details natural keys not available at level Stores

2009 03 05 17 21 47 937 0800 Pool Worker 10 INFO Probing staging table ST Shopping Carts for DISTINCT to load Stores Stores

2009 03 05 17 21 47 937 0800 Pool Worker 10 INFO Inserting new records into table Stores Stores from staging table ST Shopping Carts

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES Store ID ST Stores CKSUM LOAD ID ST Shopping Carts CKSUM 

2009 03 05 17 21 47 984 0800 Pool Worker 10 INFO INSERTDT 1 Stores Stores ST Shopping Carts 100 Store ID 100 rows inserted

2009 03 05 17 21 47 984 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Stores Stores

2009 03 05 17 21 47 984 0800 Pool Worker 10 INFO Probing staging table ST Stores for DISTINCT to load Stores Stores

2009 03 05 17 21 48 015 0800 Pool Worker 10 DEBUG CREATE INDEX DX ST StoresSTORESDSTORE IDSTORESDDW DM STORES STORES CKSUM ON S N389a3dee ce29 4e42 90ad 44970093f745.ST Stores Store ID DW DM STORES STORES CKSUM 

2009 03 05 17 21 48 031 0800 Pool Worker 10 INFO Inserting new records into table Stores Stores from staging table ST Stores

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES Store ID Region City Type ST Shopping Carts CKSUM LOAD ID ST Stores CKSUM 

2009 03 05 17 21 48 046 0800 Pool Worker 10 INFO INSERTDT 1 Stores Stores ST Stores 0 Region Type Store ID City 0 rows inserted

2009 03 05 17 21 48 046 0800 Pool Worker 10 INFO Updating table DW DM STORES STORES from staging table ST Stores

2009 03 05 17 21 48 046 0800 Pool Worker 10 DEBUG UPDATE S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES SET LOAD ID 1 Region B.Region City B.City Type B.Type ST Stores CKSUM B.DW DM STORES STORES CKSUM 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.ST Stores B ON A.Store ID B.Store ID AND A.ST Stores CKSUM B.DW DM STORES STORES CKSUM 

2009 03 05 17 21 48 093 0800 Pool Worker 10 INFO UPDATEDT 1 Stores Stores ST Stores 100 Region Type City 100 rows affected

2009 03 05 17 21 48 093 0800 Pool Worker 10 INFO Updating surrogate keys for load id 1 in dimension table Stores Stores

2009 03 05 17 21 48 093 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW DM STORES STORESSTORESDSTORES1543357431 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES Stores1543357431 

2009 03 05 17 21 48 140 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Stores Stores for 1 status Complete

2009 03 05 17 21 48 140 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Cart Details Day Products Customers Stores Fact for 1 status Running

2009 03 05 17 21 48 140 0800 Pool Worker 10 INFO Starting LoadWarehouse ACORN Cart Details Day Products Customers Stores Fact 

2009 03 05 17 21 48 140 0800 Pool Worker 10 INFO Deleting any records from table Cart Details Day Products Customers Stores Fact with same load ID

2009 03 05 17 21 48 156 0800 Pool Worker 10 INFO Inserting new records into table Cart Details Day Products Customers Stores Fact from staging table ST Cart Details

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Cart Details Cart ID DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Cart Details Product ID DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Products Product ID DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Time Day ID DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Cart ID DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Product ID DW S F CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Quantity DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Cart Details Shopping Carts 13875 573 DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Cart Details Cart Details200351043 DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Products Products1249892458 DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESTime Week ID Time Month ID Time Quarter ID DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Stores Stores1543357431 DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES.Customers Customers120094747 Stores Store ID Time Sales Date Day ID Customers Loyalty Card ID LOAD ID 

SELECT B.Cart ID B.Product ID B.Product ID 39870 B.Cart ID B.Product ID B.Quantity S N 389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS. Shopping Carts 13875573 S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS.Cart Details200351043 S N389a3dee ce29 4e42 90ad 449700 93f745.DW DM PRODUCTS PRODUCTS.Products1249892458 dbo.DW DM TIME DAY.WeekID dbo.DW DM TIME DAY.Month ID dbo.DW DM TIME DAY.Quarter ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES.Stores1543357431 S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS.Customers120094747 ST Shopping Carts .Store ID ST Shopping Carts Sales Date Day ID ST Shopping Carts .Loyalty Card ID 1

LEFT OUTER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.ST Shopping Carts ST Shopping Carts ON B.Cart ID ST Shopping Carts .Cart ID 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS ON B.Cart ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS.Cart ID 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS ON B.Cart ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CAR T DETAILS.Cart ID AND B.Product ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS CART DETAILS.Product ID 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS ON B.Product ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS.Product ID 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES ON ST Shopping Carts .Store ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES.Store ID 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS ON ST Shopping Carts .Loyalty Card ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS.Loyalty Card ID 

2009 03 05 17 21 48 343 0800 Pool Worker 10 INFO INSERTF 1 Cart Details Day Products Customers Stores Fact ST Cart Details 12438 Quantity Cart ID Product ID 12438 rows inserted

2009 03 05 17 21 48 343 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESCUSTOMERSDCUSTOMERS120094747 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Customers Customers120094747 

2009 03 05 17 21 48 421 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESPRODUCTSDPRODUCTS1249892458 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Products Products1249892458 

2009 03 05 17 21 48 453 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESTIMEDDAY ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Time Day ID 

2009 03 05 17 21 48 468 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESTIMEDWEEK ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Time Week ID 

2009 03 05 17 21 48 515 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESTIMEDMONTH ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Time Month ID 

2009 03 05 17 21 48 546 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESTIMEDQUARTER ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Time Quarter ID 

2009 03 05 17 21 48 562 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESSTORESDSTORES1543357431 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Stores Stores1543357431 

2009 03 05 17 21 48 609 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESCART DETAILSDCART DETAILS200351043 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Cart Details Cart Details200351043 

2009 03 05 17 21 48 656 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESCART DETAILSDSHOPPING CARTS43875573 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORES Cart Details Shopping Carts 13875573 

2009 03 05 17 21 48 671 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW SF CART DETAILS DAY PRODUCTS CUSTOMERS STORESLOAD ID ON

2009 03 05 17 21 48 734 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Cart Details Day Products Customers Stores Fact for 1 status Complete

2009 03 05 17 21 48 734 0800 Pool Worker 10 INFO Finished LoadWarehouse ACORN Cart Details Day Products Customers Stores Fact 

2009 03 05 17 21 48 734 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Shopping Carts Day Customers Stores Fact for 1 status Running

2009 03 05 17 21 48 734 0800 Pool Worker 10 INFO Starting LoadWarehouse ACORN Shopping Carts Day Customers Stores Fact 

2009 03 05 17 21 48 734 0800 Pool Worker 10 INFO Deleting any records from table Shopping Carts Day Customers Stores Fact with same load ID

2009 03 05 17 21 48 750 0800 Pool Worker 10 INFO Inserting new records into table Shopping Carts Day Customers Stores Fact from staging table ST Shopping Carts

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Cart Details Cart ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Customers Loyalty Card ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Stores Store ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Time Day ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Cart ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Loyalty Card ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Store ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Time Sales Date Day ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Cart Details Shopping Carts 13875573 DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Time Week ID Time Month ID Time Quarter ID DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Stores Stores1543357431 DW SF SHOPPING CARTS DAY CUSTOMERS STORES.Customers Customers120094747 LOAD ID 

SELECT B.Cart ID B.Loyalty Card ID B.Store ID 39870 B.Cart ID B.Loyalty Card ID B.Store ID B.Sales Date Day ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS.Shopping Carts 13875573 dbo.DW DM TIME DAY.Week ID dbo.DW DM TIME DAY.Month ID dbo.DW DM TIME DAY.Quarter ID S N38 9a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES.Stores1543357431 S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS.Customers120094747 1

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS ON B.Cart ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CART DETAILS SHOPPING CARTS.Cart ID 

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES ON B.Store ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES.Store ID 

INNER JOIN S N389a3dee ce29 4e42 90ad 449700931745.DW DM CUSTOMERS CUSTOMERS ON B.Loyalty Card ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS.Loyalty Card ID 

2009 03 05 17 21 48 796 0800 Pool Worker 10 INFO INSERTF 1 Shopping Carts Day Customers Stores Fact ST Shopping Carts 3000 Loyalty Card ID Cart ID Store ID 3000 rows inserted

2009 03 05 17 21 48 796 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF SHOPPING CARTS DAY CUSTOMERS STORESCUSTOMERSDCUSTOMERS120094747 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES Customers Customers120094747 

2009 03 05 17 21 48 828 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF SHOPPING CARTS DAY CUSTOMERS STORESTIMEDDAY ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES Time Day ID 

2009 03 05 17 21 48 843 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF SHOPPING CARTS DAY CUSTOMERS STORESTIMEDWEEK ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES Time Week ID 

2009 03 05 17 21 48 890 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF SHOPPING CARTS DAY CUSTOMERS STORESTIMEDMONTH ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES Time Month ID 

2009 03 05 17 21 48 921 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF SHOPPING CARTS DAY CUSTOMERS STORESTIMEDQUARTER ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES Time Quarter ID 

2009 03 05 17 21 48 921 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF SHOPPING CARTS DAY CUSTOMERS STORESSTORESDSTORES15433 57431 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES Stores Stores1543357431 

2009 03 05 17 21 48 953 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF SHOPPING CARTS DAY CUSTOMERS STORESCART DETAILSDSHOPPING CARTS 13875573 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES Cart Details Shopping Carts 13875573 

2009 03 05 17 21 48 968 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW SF SHOPPING CARTS DAY CUSTOMERS STORESLOAD ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF SHOPPING CARTS DAY CUSTOMERS STORES LOAD ID 

2009 03 05 17 21 48 984 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Shopping Carts Day Customers Stores Fact for 1 status Complete

2009 03 05 17 21 48 984 0800 Pool Worker 10 INFO Finished LoadWarehouse ACORN Shopping Carts Day Customers Stores Fact 

2009 03 05 17 21 48 984 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Products Day Fact for 1 status Running

2009 03 05 17 21 48 984 0800 Pool Worker 10 INFO Deleting any records from table Products Day Fact with same load ID

2009 03 05 17 21 48 984 0800 Pool Worker 10 INFO Inserting new records into table Products Day Fact from staging table ST Products

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY DW SF PRODUCTS DAY.Products Product ID DW SF PRODUCTS DAY.Time Day ID DW SF PRODUCTS DAY.Product ID DW SF PRODUCTS DAY.Category ID DW SF PRODUCTS DAY.Unit Price DW SF PRODUCTS DAY.Products Products124989245 8 DW SF PRODUCTS DAY.Time Week ID Time Month ID Time Quarter ID LOAD ID 

SELECT B.Product ID 39870 B.Product ID B.Category ID B.Unit Price S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS.Products1249892458 dbo.DW DM TIME DAY.Week ID dbo.DW DM TIME DAY.Month ID dbo.DW DM TIME DAY.Quarter ID 1

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS ON B.Product ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM PRODUCTS PRODUCTS.Product ID 

2009 03 05 17 21 48 984 0800 Pool Worker 10 INFO INSERTF 1 Products Day Fact ST Products 20 Category ID Unit Price Product ID 20 rows inserted

2009 03 05 17 21 49 000 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF PRODUCTS DAYTIMEDDAY ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY Time Day ID 

2009 03 05 17 21 49 015 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF PRODUCTS DAYTIMEDWEEK ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY Time Week ID 

2009 03 05 17 21 49 015 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF PRODUCTS DAYTIMEDMONTH ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY Time Month ID 

2009 03 05 17 21 49 031 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF PRODUCTS DAYTIMEDQUARTER ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY Time Quarter ID 

2009 03 05 17 21 49 031 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF PRODUCTS DAYPRODUCTSDPRODUCTS1249892458 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY Products Products1249892458 

2009 03 05 17 21 49 062 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW SF PRODUCTS DAYLOAD ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF PRODUCTS DAY LOAD ID 

2009 03 05 17 21 49 062 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Products Day Fact for 1 status Complete

2009 03 05 17 21 49 078 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Customers Day Fact for 1 status Running

2009 03 05 17 21 49 078 0800 Pool Worker 10 INFO Deleting any records from table Customers Day Fact with same load ID

2009 03 05 17 21 49 093 0800 Pool Worker 10 INFO Inserting new records into table Customers Day Fact from staging table ST Customers

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CUSTOMERS DAY DW SF CUSTOMERS DAY.Customers Loyalty Card ID DW SF CUSTOMERS DAY.Time Day ID DW SF CUSTOMERS DAY.Loyalty Card ID DW SF CUSTOMERS DAY. Time Week ID Time Month ID Time Quarter ID DW SF CUSTOMERS DAY.Customers Customers120094747 LOAD ID 

SELECT B.Loyalty Card ID 39870 B.Loyalty Card ID dbo.DW DM TIME DAY.Week ID dbo.DW DM TIME DAY.Month ID dbo.DW DM TIME DAY.Quarter ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS.Customers120094747 1

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS ON B.Loyalty Card D S N389a3dee ce29 4e42 90ad 44970093f745.DW DM CUSTOMERS CUSTOMERS.Loyalty Card ID 

2009 03 05 17 21 49 093 0800 Pool Worker 10 INFO INSERTF 1 Customers Day Fact ST Customers 100 Loyalty Card ID 100 rows inserted

2009 03 05 17 21 49 093 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CUSTOMERS DAYCUSTOMERSDCUSTOMERS120094747 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CUSTOMERS DAY Customers Customers120094747 

2009 03 05 17 21 49 140 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CUSTOMERS DAYTIMEDDAY ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CUSTOMERS DAY Time Day ID 

2009 03 05 17 21 49 140 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CUSTOMERS DAYTIMEDWEEK ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CUSTOMERS DAY Time Week ID 

2009 03 05 17 21 49 140 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CUSTOMERS DAYTIMEDMONTH ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CUSTOMERS DAY Time Month ID 

2009 03 05 17 21 49 171 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF CUSTOMERS DAYTIMEDQUARTER ID ON S N389a3dee ce29 4e42 90ad 44970093045.DW SF CUSTOMERS DAY Time Quarter ID 

2009 03 05 17 21 49 187 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW SF CUSTOMERS DAYLOAD ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF CUSTOMERS DAY LOAD ID 

2009 03 05 17 21 49 187 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Customers Day Fact for 1 status Complete

2009 03 05 17 21 49 187 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Stores Day Fact for 1 status Running

2009 03 05 17 21 49 187 0800 Pool Worker 10 INFO Deleting any records from table Stores Day Fact with same load ID

2009 03 05 17 21 49 187 0800 Pool Worker 10 INFO Inserting new records into table Stores Day Fact from staging table ST Stores

INTO S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY DW SF STORES DAY.Stores Store ID DW SF STORES DAY.Time Day ID DW SF STORES DAY.Store ID DW SF STORES DAY.Time Week ID Time Month ID Time Quarter ID DW SF STORES DAY.Stores Stores1543357431 LOAD ID 

SELECT B.Store ID 39870 B.Store ID dbo.DW DM TIME DAY.Week ID dbo.DW DM TIME DAY.Month ID dbo.DW DM TIME DAY.Quarter ID S N389a3dee ce29 4e42 90ad 44 970093f745.DW DM STORES STORES.Stores1543357431 1

INNER JOIN S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES ON B.Store ID S N389a3dee ce29 4e42 90ad 44970093f745.DW DM STORES STORES.Store ID 

2009 03 05 17 21 49 203 0800 Pool Worker 10 INFO INSERTF 1 Stores Day Fact ST Stores 100 Store ID 100 rows inserted

2009 03 05 17 21 49 203 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF STORES DAYTIMEDDAY ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY Time Day ID 

2009 03 05 17 21 49 218 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF STORES DAYTIMEDWEEK ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY Time Week ID 

2009 03 05 17 21 49 234 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF STORES DAYTIMEDMONTH ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY Time Month ID 

2009 03 05 17 21 49 234 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF STORES DAYTIMEDQUARTER ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY Time Quarter ID 

2009 03 05 17 21 49 234 0800 Pool Worker 10 DEBUG CREATE INDEX MX DW SF STORES DAYSTORESDSTORES1543357431 ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY Stores Stores1543357431 

2009 03 05 17 21 49 281 0800 Pool Worker 10 DEBUG CREATE INDEX DX DW SF STORES DAYLOAD ID ON S N389a3dee ce29 4e42 90ad 44970093f745.DW SF STORES DAY LOAD ID 

2009 03 05 17 21 49 312 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN Stores Day Fact for 1 status Complete

2009 03 05 17 21 49 312 0800 Pool Worker 10 DEBUG Logging step LoadWarehouse ACORN for 1 status Complete

2009 03 05 17 21 49 328 0800 Pool Worker 10 INFO Elapsed Time 0 minutes 4 seconds for LoadWarehouse 1 loadgroup ACORN

2009 03 05 17 21 49 328 0800 Pool Worker 10 WARN Empty script group There are no scripts defined in script group ACORN

2009 03 05 17 21 49 328 0800 Pool Worker 10 INFO Elapsed Time 0 minutes 0 seconds for ExecuteScriptGroup ACORN

Although the foregoing embodiments have been described in some detail for purposes of clarity of understanding the invention is not limited to the details provided. There are many alternative ways of implementing the invention. The disclosed embodiments are illustrative and not restrictive.

