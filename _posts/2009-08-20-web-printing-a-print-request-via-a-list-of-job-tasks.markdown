---

title: Web printing a print request via a list of job tasks
abstract: One embodiment is a method that analyzes a print request that is transmitted over an internet and received at a cloud print system. The method then executes with priorities a list of job tasks to print the print request at a web-enabled printer.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09052848&OS=09052848&RS=09052848
owner: Hewlett-Packard Development Company, L.P.
number: 09052848
owner_city: Houston
owner_country: US
publication_date: 20090820
---
The present application cross references and claims priority to parent patent application filed with the Indian Patent Office on 7 Jul. 2009 and having Indian application number 1603 CHE 2009.

In order to print a document a user typically selects a print command from an application program to initiate print services of the operating system. The print services present a user interface in the form of a print dialog box that allows the user to select various print options such as paper source number of copies page orientation print quality etc. After the user selects the print options and commences the print operation the operating system uses a printer driver to convert the document to a PDL page description language format that is specific to the printer selected by the user. The printer driver then directs the PDL to the printer where it is rendered as a hardcopy output.

These tasks are relatively common and straightforward when the document is printed to a local printer. These tasks however become quite complicated if the user desires to print the document over the internet to a remote printer.

One embodiment is a method that analyzes a print request that is transmitted over an internet and received at a cloud print system. The method then executes with priorities a list of job tasks to print the print request at a web enabled printer.

Exemplary embodiments in accordance with the invention relate to systems and methods that analyze and process print job requests to print to a web enabled printer.

Multiple users geographically distributed throughout different parts of the world can simultaneously transmit print jobs to a cloud print system. A web service in the cloud receives the print jobs and transports them to web enabled or networked printers. The web service processes a large number of print jobs arriving from one or more users and also adapts to integrate new functionality into the web service.

A list of tasks is created for each print job and an order of precedence is assigned to each task of the print job. The precedence determines an order for executing the tasks which can be executed on a variety of different systems participating in a distributed network connected to the cloud.

Exemplary embodiments provide printing services to users who connect to the cloud through the internet. The cloud print system enables users to print from different geographical locations around the world using computers that run different operating systems such as Linux Windows etc. The printing functions provided by the cloud are equally provided to these different operating systems since the printing workflow is divided into independent functions. More specifically as discussed below print requests are divided into job lists that include multiple job tasks executed in an order according to assigned priorities.

Users are able to print emails documents photos web pages etc. from a variety of different portable devices manufactured by different companies. Mobile users can print to one or more printers from any worldwide location that provides internet access regardless of whether the user is located at home in the office on the road in a foreign country etc. The print services provided by the cloud print system are printer agnostic and driverless i.e. the computers of the users are not required to have a print driver software that converts data to be printed to a form specific to the computer . Functions of the print driver are provided by the cloud not the user computer that initiated the print job request.

As discussed below processing and executing a large number of print job requests from multiple users involves a number of sub operations. These sub operations are broadly divided into one of two types those specified by the user or specified by cloud print systems as part of the print operation. As an example an SMS notification request sent from the notification services to the user is a user specified event while counting sheets being printed is transparent to the user and a cloud system event.

The sub operations are performed in a specified order or sequence that is based in part on assigned priorities or precedents. For example sheet counting operations are performed after PostScript documents are created. As another example a document is sent to the printer only when the document is prepared for printing. Furthermore with exemplary embodiments the number of sub operations job steps for a given print job can vary depending on the type of print job platform or operating system requesting the print job etc.

Generally a print job work item is performed with the following operations handling user requests creating a job list and processing the job list. The print job request handler acts on all the user requests. The job list creator creates job steps and the job list processor executes the job steps according to the assigned priorities. These tasks are more fully discussed below.

The request handler records print requests received from users or electronic devices and responds with a job identifier job id to the user. The print job request is concluded on completion of the print job request handler and on sending a response message with the job id to the print user.

The job list creator generates and outputs a list of job steps. The order and precedence values are generated when preparing the job list. The job step list is recorded in a cell of the job record of the database.

In one exemplary embodiment the job list creator is a system wide application that periodically runs for example the program is activated every minute . The job list creator performs one or more of the following functions 

In one exemplary embodiment the job list is composed of tokens each token separated by a . The tokens from left to right give the order in which it is executed i.e. the tokens are arranged in an order according to a priority of execution .

The job list is formed by looking at all the items in the order of precedence listed in the precedence table. The highest ordered precedence item is looked for a value in the job record then the next item and so on by which the list is formed.

The precedence levels could be any in number and the number of job tasks in the system is any count. The corresponding items from the database are fetched by obtaining column name from the precedence table.

The job list processor processes the tasks as ordered in the list. This process performs various intermediate operations including sending data to the printer.

In one exemplary embodiment the job list processor is a system wide application that periodically runs for example the program is activated every minute .

The states in which the job list processor fetches can vary and are not restricted to those listed above. A fewer or greater number of steps can be added.

According to block a user transmits a print job request to the cloud print system. The print job request can be generated and transmitted from a wide variety of electronic devices including but not limited to notebook or desktop computers handheld portable devices such a mobile phone personal digital assistant etc. and electronic devices with a web browser. The print job request submission is not restricted to an electronic device with a web browser since such requests can arrive from web elements such as widgets web enabled applications etc.

By way of example a document to be printed is generated in an application program. In order to print the document a user selects a print command from the application program to initiate print services which present a user interface such as a print dialogue box or graphical user interface GUI that allows the user to select various print options such as paper source number of copies page orientation print quality etc. After the user selects the print options and confirms or selects printing the print job is transmitted from the electronic device to the cloud print system. For example the print job is wirelessly transmitted through one or more networks such as the internet to the cloud print system.

A print job request can arrive from both web forms and web applications. Print requests from a web form are transmitted to a corresponding servlet that makes a call to REST API Representational State Transfer Application Program Interface . Web applications have the ability to make direct calls to REST API.

According to block a web service receives and analyzes the print job requested from the electronic device of the user.

According to block the web service divides the print job into an ordered list of job tasks. The list is divided into three categories of jobs tasks that include pre processing operations printing the document and post processing after completion of the print job.

According to block a precedent is assigned to each of the job tasks. The precedent establishes a hierarchy or order of importance. For example each job task is assigned a number that indicates an order in which the particular task is executed. A task assigned a higher priority or precedent is executed before or over another task assigned a lower priority or precedent. Thus the higher precedence values are executed earlier in the associated job list.

As shown in table some preprocessing job tasks include converting text and document to PDF adding a job separator converting images to PCL and PostScript PCL stitching converting an image to PDF converting a PDF to PNG preview and PS or PDF print preferences. Examples of printing job tasks include posting to a queue and sending to the printer. Examples of post processing include notifying a user or administrator of a print job via SMS or email and job cleanup after a print job.

Each job task is assigned a unique identification shown at the column designated as ID and a precedent or priority shown at the column designated as Precedent . The precedent is a number that determines an order in which the job task is executed. A higher number indicates a higher priority. For example in the preprocessing category the job task of converting the document to PDF has a higher priority shown as precedent than the job task of PCL stitching shown as precedent .

In one exemplary embodiment each of the job tasks is a standalone program for example written in java . The input data to these programs are passed as command line parameters or obtained from the database. The system configuration related information is obtained from a package source. The job status is updated in the job record if job status information is not an error.

According to block the job tasks are executed according to the precedent assigned to the job tasks. As noted job tasks with a higher precedent are executed before or given priority over job tasks with a lower precedent.

According to block printing of the print job is completed on a designated printer in the network or cloud print system such as a printer of a print service provider . In one exemplary embodiment a web enabled printer is instructed to print the print job request.

According to block the user is notified when the print job is completed. For example the user is notified with text SMS or an email. The user or an administrator can also be notified if an error occurs during processing or printing of the requested print job.

In one exemplary embodiment since the job tasks execute in the context of a job a job id folder records intermediate results such as converted PS files. The job clean up operation deletes the job id folder.

Although discusses processing operations of the print job database operations also occur. Database operations involve functions such as creation of job record recording rating information creation or update of PSP records etc. The data processing for print job is fairly complex involving intense CPU Central Processing Unit and I O Input Output activities while database operations essentially involve I O activity.

The web service receiving print jobs analyzes the job request and compiles an ordered list of job tasks. These tasks are organized into job lists. The job lists are executed sequentially while tasks of a job list are executed in the order of precedence associated with each task. The tasks may be executed in parallel on a single or distributed environment. A job state machine is maintained to move to the next task on processing the current execution unit or in case of a failure the tasks are executed from the last good known state.

According to block the preprocessing operations prepare the document for printing. By way of example these tasks include but are not limited to converting the document to PDF format computing a sheet count i.e. number of pages to be printed creating a job separator stitching the job separator converting the PDF to a PCL and sending the converted PCL to a queue.

According to block after the print job is completed post processing operations occur. These operations include but are not limited to sending notification of the completed print job to the user an electronic device and or an administrator perform job cleanup i.e. post printing operations of the job house keeping activities etc. .

According to block the preprocessing operations prepare the document for printing. By way of example these tasks include but are not limited to converting the document to PS format computing the sheet count creating a job separator and sending to the queue.

According to block the post processing operations occur. By way of example these tasks include but are not limited to sending an SMS notification to the user indicating that the print job successfully completed and performing job cleanup.

According to block the first state is initialize. The print job commences with initialization. At the time of system initialization a startup component resets the job state to last good state from the present state if not already in good state. For example if the job is in PROCESSING state the system recognizes this not to be a last good state hence resets to READY . This reset ensures that the job list creator or job list processor can perform the required set of operations.

According to block the second state is available. The request received from the user is recorded or stored and is available for further processing.

According to block the fourth state is ready. The server completes preparation of the job list and the job is now ready for execution.

According to block the fifth state is processing. The server processes one or more items of the job. The processing prepares the job for printing.

According to block the sixth state is queued. The job is placed in a queue for subsequent manual or automatic printing. An error situation requiring retries will be in queued state.

In one exemplary embodiment the processing state can be reset to one of the good intermediate task. Jobs in queued state will change when the job is completed successfully or when a print retry count has reached maximum value.

According to block the seventh state is printed. The job is successfully printed or printed with an error. No more print attempts remain.

According to block the eighth state is done. The server has completed processing of all job items for the print job.

Exemplary embodiments are applied in various environments such as remote printing driverless printing assisted or manual printing i.e. queued jobs are manually sent to the printer and un assisted or automatic printing i.e. queued jobs are automatically sent to the printer . Further exemplary embodiments can be used to migrate some of the printer firmware based functionality into the cloud computing environment shown in as cloud print system . Further yet although PDF is used as an intermediate format other formats can be used such as XPS PS EMF etc.

The term cloud is a computer network accessible over the internet and or web that is dynamically scalable with virtualized resources such as printing resources. Users are not required to have knowledge or expertise in the infrastructure of the cloud that relies on the internet to satisfy the computing or printing needs of users. The cloud provides computer and or printer services with business applications that are accessible from a web browser while software and data are stored on servers in the cloud. For example a printing cloud system supports infrastructure for printer services platform for the printer services and software for the printer services.

The term Page Description Language or PDL is a language that describes an appearance of a printed page in a higher level than output bitmap. PostScript or PS is an example of a PDL.

The term Portable Document Format or PDF is a file format for document exchange that represents two dimensional documents in a manner that is independent of the application software hardware or operating system.

The term Portable Network Graphic or PNG is a bitmapped image format that uses lossless data compression.

The term Printer Command Language or PCL is a Page Description Language PDL developed by Hewlett Packard Company as a printer protocol.

The term Short Message Service or SMS is a communication service that uses standardized communication protocols to exchange short text messages between electronic devices.

The term world wide web or web is a system of linked hypertext documents access through the internet. Using a web browser a user can view web pages that include text images video and other media and navigate between these pages with hyperlinks.

The term web application is a software application that is accessed over one or more networks such as the internet or an intranet . For example web applications include applications accessed through a web browser.

The term web form is a form on a web page that allows a user to enter data that is sent to a server for processing.

In one exemplary embodiment one or more blocks or steps discussed herein are automated. In other words apparatus systems and methods occur automatically. The terms automated or automatically and like variations thereof mean controlled operation of an apparatus system and or process using computers and or mechanical electrical devices without the necessity of human intervention observation effort and or decision.

The methods in accordance with exemplary embodiments of the present invention are provided as examples and should not be construed to limit other embodiments within the scope of the invention. Further methods or steps discussed within different figures can be added to or exchanged with methods of steps in other figures. Further yet specific numerical data values such as specific quantities numbers categories etc. or other specific information should be interpreted as illustrative for discussing exemplary embodiments. Such specific information is not provided to limit the invention.

In the various embodiments in accordance with the present invention embodiments are implemented as a method system and or apparatus. As one example exemplary embodiments and steps associated therewith are implemented as one or more computer software programs to implement the methods described herein. The software is implemented as one or more modules also referred to as code subroutines or objects in object oriented programming . The location of the software will differ for the various alternative embodiments. The software programming code for example is accessed by a processor or processors of the computer or server from long term storage media of some type such as a CD ROM drive or hard drive. The software programming code is embodied or stored on any of a variety of known physical and tangible media for use with a data processing system or in any memory device such as semiconductor magnetic and optical devices including a disk hard drive CD ROM ROM etc. The code is distributed on such media or is distributed to users from the memory or storage of one computer system over a network of some type to other computer systems for use by users of such other systems. Alternatively the programming code is embodied in the memory and accessed by the processor using the bus. The techniques and methods for embodying software programming code in memory on physical media and or distributing software code via networks are well known and will not be further discussed herein.

The above discussion is meant to be illustrative of the principles and various embodiments of the present invention. Numerous variations and modifications will become apparent to those skilled in the art once the above disclosure is fully appreciated. It is intended that the following claims be interpreted to embrace all such variations and modifications.

