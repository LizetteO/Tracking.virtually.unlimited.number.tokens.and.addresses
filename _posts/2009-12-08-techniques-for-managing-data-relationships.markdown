---

title: Techniques for managing data relationships
abstract: Techniques for managing data relationships are presented. A database element from a first database table is linked with a database element of a second database table via a Graphical User Interface as directed by a user. The link establishes a data relationship having attributes and properties. The relationship along with the attributes and properties are graphically presented to the user for inspection and analysis.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09514182&OS=09514182&RS=09514182
owner: Teradata US, Inc.
number: 09514182
owner_city: Dayton
owner_country: US
publication_date: 20091208
---
A portion of the disclosure of this patent document contains material that is subject to copyright protection. The copyright owner has no objection to the facsimile reproduction by anyone of the patent document or the patent disclosure as it appears in the Patent and Trademark Office patent file or records but otherwise reserves all copyright rights whatsoever. The following notice applies to the example screen shots images and source code as described below and in any drawings hereto Copyright 2009 Teradata Inc. of Miamisburg Ohio All Rights Reserved.

Enterprises are increasingly capturing storing and mining a plethora of information related to communications with their customers. Often this information is stored and indexed within databases. Once the information is indexed queries are developed on an as needed basis to mine the information from the database for a variety of organizational goals.

The enterprise data can originate from a myriad of sources and even external feeds but ultimately the goal for the enterprise is that all the data be consolidated indexed and related within a central enterprise data warehouse.

A major portion of data warehouse management is defining and managing data relationships. A data relationship is data needed to control an association of one piece of data within the data warehouse with another piece of data within the data warehouse. Often this control requires enforcement of enterprise business processes some processes are automated and some processes are manual.

In various embodiments techniques for managing data relationships are presented. According to an embodiment a method for establishing a data relationship is presented. Specifically a user is dynamically interacted with to identify a first element from a first database table and a second element from a second database table. Next the first element and the second element are linked in a third database table to create a relationship between the first element and the second element in the third database table. Finally attributes and properties of the relationship are dynamically presented to the user.

A data store as used herein may include a database a collection of databases organized as a data warehouse a directory a collection of directories cooperating with one another or various combinations of the same. According to an embodiment the data store is a Teradata warehouse product or service distributed by Teradata Inc. of Miamisburg Ohio.

The data store includes a variety of enterprise information. One type of information is referred to as an entity. An entity is something that can be uniquely identified e.g. a customer account a customer name a household name a logical grouping of certain types of customers etc. .

The use of entity and element may be used interchangeably herein and below. Additionally the use of data store and database may used interchangeably herein and below.

A table within the data store may include a schema that defines the relationship between one or more elements in the data store. For example the relationship between data store element household to element individual and to element account household individual account . The schema defines the fields or elements of the data store. The data store includes a plurality of different tables and different schema s. Schema relationships may be hierarchical or many to many relationships.

A relational object or a relationship object is a special grouping of database elements selected and defined by a user. The phrases database object relational object and relationship object may be used interchangeably herein.

Each element or relational object includes attributes and or properties. Attributes and properties are values associated with an element or object types of values metadata about values and the like. For example an attribute property of an element house may include a color type for the house such as red. Metadata may indicate the house was painted red on a certain date and by a certain company.

It is within this context that the processing associated with the data relationship establishment service is now described in detail with reference to the .

At the data relationship establishment service interacts with a user to identify a first element from a first database table and a second element from a second database table. It is noted that the first and second elements can be more than a single filed but can be composite information from the tables such that they are each viewed as database objects or relational objects.

According to an embodiment at the data relationship establishment service interacts with the user via a GUI tool that includes user guided fields to receive the first element and the second element from the user. Example screens of such a GUI tool are provided below with reference to the .

In another case at the data relationship establishment service permits the user to define the first element and the second element as selective fields from the first database table and the second database table. Here as stated above the first element is a first relationship or relational object and the second element is a second relationship or relational object. So the elements can be composite information from the databases selected by the user and essentially defined by the user.

At the data relationship establishment service links the first element and the second element in a third database table. This table is newly established by the data relationship establishment service to create a relationship between the first element and the second element.

In an embodiment at the data relationship establishment service permits the user to assign a relationship name or label for the relationship. This permits the relationship name to be integrated into other applications for future usage in an automated fashion. This also permits reuse such that users can local and retrieve particular relationships by their relationship names.

In a particular scenario at the data relationship establishment service permits the user to define the relationship as a hierarchical relationship where the first element is a parent to the second element the second element a child to the parent within the hierarchical relationship. The parent itself can be a child to another parent and the child can be a parent to another child within the hierarchical relationship.

In still another situation at the data relationship establishment service allows the user to add some of the properties or some of the attributes to the relationship. So new attributes properties can be assigned and associated with just the newly created relationship by the user.

At the data relationship establishment service dynamically presents the attributes and properties of the relationship to the user. This allows the user to interactive inspect and visualize all aspects of the relationship between the first and second elements.

According to an embodiment at the data relationship establishment service graphically depicts for the user the relationship between the first element and the second element. This graphical depiction can also include the first database table and the second database table with the attributes and the properties of the relationship. In fact the graphical depiction can be interactive so more detail can be drilled down into or less detail can be abstracted up on direction of the user.

The data relationship management service presents an alternative and in some cases an enhanced processing perspective to the data relationship establishment service represented by the method of the . Specifically the data relationship establishment service is focused on the initial creation of a data relationship and graphical presentation of that relationship along with its attributes and properties. The data relationship management service is focused on managing controlling customizing and modifying such a data relationship as was established with the data relationship establishment service of the .

At the data relationship management service receives from a user a relationship object. This can be done in a variety of manners.

For example at the data relationship management service acquires an identifier for the relationship object as a selection provided by the user within a GUI tool. This identifier can be typed into a field of the GUI or acquired via a pull down list selection and the like.

At the data relationship management service changes an attribute or property associated with the relationship object as directed by the user.

According to an embodiment at the data relationship management service adds a new attribute or a new property to the relationship object at the direction of the user.

In another case at the data relationship management service deletes an existing property or an existing attribute associated with the relationship object in response to direction provided by the user.

At the data relationship management service automatically updates a database table for the relationship object to reflect the change. The relationship object defines a data relationship between a first database object of a first database table and a second database object of a second database table. The relationship creation that embodies the relationship object was described in detail above with reference to the method of the .

In an embodiment at the data relationship management service presents a graphical view of the relationship object along with the properties and attributes in response to an instruction to do so received from the user.

In another case at the data relationship management service provides an interface screen to receive a new definition for a new relationship object that creates a new relationship between different database objects from different database tables. In other words the data relationship management service can act in a manner similar to the or as an enhanced version of the method described above with reference to the .

Similarly at the data relationship management service provides another interface screen to receive a modification to the relationship between the first database object and the second database object.

So the relationship object that embodies the relationship can be modified deleted created controlled and managed via the data relationship management service.

In an embodiment portions of the data relationship management system implements among other things the data relationship establishment service and the data relationship management service represented by the methods and of the respectively.

The data relationship management system includes a GUI tool and a relationship management service . Each of these and their interactions with one another will now be discussed in turn.

The GUI tool is implemented in a computer readable storage medium and is to execute on one or more processors of a network. Example aspects of the GUI tool were presented above with reference to the methods and of the respectively. Moreover example screen shots of the GUI tool for sample data are provided below with reference to the .

The GUI tool is configured to interact with a user for selecting a first relational object and a second relational object.

In an embodiment the first relational object is selected from a first database table and the second relational object is selected from a second database table. The first and second database tables are different from one another.

According to an embodiment the GUI tool is also configured to permit the user to modify the relationship discussed below with reference to the relationship management service via interactions with the relationship management service .

Also in some cases the GUI tool is further configured to permit the user to create new relationships via interactions with the relationship management service. This was discussed above with reference to the methods and of the respectively.

In still other scenarios the GUI tool is configured to permit the user to delete the relationship again discussed below via interactions with the relationship management service .

The relationship management service is implemented in a computer readable storage medium and is to execute on one or more processors of the network. Processing aspects of the relationship management service were presented above with reference to the methods and of the respectively.

The relationship management service is configured to interface and interact with the GUI tool to detect a user command to establish a relationship between the first relational object and the second relational object.

The Relational Object component of the holds the actual master table names used to build the data relationship.

The Relational Object Key Type component of the includes the various keys links that any particular master table for which the relationship data is being captured built.

The Relational Object Key Description component of the includes the Key link details like the column names both logical and physical and in case of composite the sequence number is used to identify the sequences to that are defined. A table may have a single column key and multiple column keys one entry for each key column is made into this table.

The Relational Object Map component of the holds the relationship among the various relational objects defined the relationship stored is in the form of parent child.

The Relational Object Properties component of the depicts properties that are associated with the relationship that can be captured. For example approval history effective dates etc.

Consider that a user wants to link data of a Country having Country Id database element or field as its primary key with a State table having State Id database element of field as its primary key.

How do the data relationship techniques presented herein and above help the user to achieve the above use case 

1. Relational object is created using Table 1 and the primary keys column s are selected for use in data linking.

2. Relational object is created using Table 2 and the primary keys column s are selected for use in data linking.

3. A data relationship is created using these objects tables 1 and 2 assume that Table 1 is a parent table and that Table 2 is a child table.

4. Mapping data of Table 1 and Table 2 is achieved the user can select the relation and define the data for it by selecting a parent record from Table 1 and a child record from Table 2.

5. Mapping of data from Table 1 and Table 2 is created in the Table 3 Relational Object Data for only the primary keys column s which was selected by user as link column s while defining the object in step 1. There is no database operation done on the actual table Table 1 and Table 2 data.

Once the logical linking of metadata and data is established. The hierarchical data view can be constructed in a hierarchy viewer.

Now some example source code that can be used to implemented portions of the techniques presented herein are presented. It is noted that other implementations that achieve the teachings presented herein and above can be used without departing from the embodiments of the invention.

One now fully appreciates the improved techniques for managing data relationships presented herein and above. Specifically the techniques presented herein directly integrate the management and visualization of data relationships. The allows database viewers to view visualize and interact with data relationships while maintaining automated control of the underlying data of the database.

The above description is illustrative and not restrictive. Many other embodiments will be apparent to those of skill in the art upon reviewing the above description. The scope of embodiments should therefore be determined with reference to the appended claims along with the full scope of equivalents to which such claims are entitled.

The Abstract is provided to comply with 37 C.F.R. 1.72 b and will allow the reader to quickly ascertain the nature and gist of the technical disclosure. It is submitted with the understanding that it will not be used to interpret or limit the scope or meaning of the claims.

In the foregoing description of the embodiments various features are grouped together in a single embodiment for the purpose of streamlining the disclosure. This method of disclosure is not to be interpreted as reflecting that the claimed embodiments have more features than are expressly recited in each claim. Rather as the following claims reflect inventive subject matter lies in less than all features of a single disclosed embodiment. Thus the following claims are hereby incorporated into the Description of the Embodiments with each claim standing on its own as a separate exemplary embodiment.

