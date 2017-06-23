---

title: Progress information in a service-oriented architecture
abstract: A system may include reception of an instruction to execute a business process from a client application, execution of the business process in a first software work process, and storage, during execution of the business process, of progress information associated with the business process within a memory. A system may further include reception, at a second software work process, of a request from the client application for progress information, retrieval, in the second software work process, of the progress information from the shared memory, reception, at the second software work process, of the progress information from the memory, and provision of the progress information to the client application from the second software work process.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09536222&OS=09536222&RS=09536222
owner: SAP SE
number: 09536222
owner_city: Walldorf
owner_country: DE
publication_date: 20091228
---
This application is related to U.S. patent application Ser. No. 12 647 815 filed on even date herewith and entitled Process Driven Progress Information in a Service Oriented Architecture 

Some embodiments relate to a service oriented architecture to provide software services. More specifically some embodiments relate to the provision of progress information to a service client during service fulfillment.

For example a user may manipulate a user interface of client to input an instruction e.g. update inventory . Client in response may transmit a corresponding HTTP service request to service oriented architecture as illustrated. Service oriented architecture conducts any processing required by the request e.g. updating a list of inventory and after completing the processing provides a response to client .

Client does not receive any indication from service oriented architecture during the above mentioned processing. Accordingly after inputting the instruction and before receiving the response the user is left to wonder whether any processing is occurring as a result of the instruction whether service oriented architecture is non responsive or whether a network error has occurred between client and service oriented architecture . Service requests which require lengthy processing exacerbate this dilemma.

Due to the request response nature of HTTP the foregoing cannot be addressed simply by programming service oriented architecture to send some sort of progress indicator to client . Accordingly what is needed is a system to provide meaningful progress information to a client of a service oriented architecture.

Generally business process platform may provide services to client according to some embodiments. Such services may comprise Web services and client may therefore comprise a Web client. Examples of a Web client include but are not limited to a Web browser an execution engine e.g. JAVA Flash Silverlight to execute associated code in a Web browser and a dedicated standalone application.

Business process platform includes software work process and software work process . Each of software work processes and may independently execute tasks required of business process platform . Business process platform may support more than two simultaneous software work processes according to some embodiments.

Business process platform also includes shared memory which may be implemented in Random Access Memory persistent storage e.g. hard disks and or in any other suitable electronic memory. Each of software work processes and is in i.e. capable of communication with shared memory .

Initially an instruction to execute a business process is received from a client application at S. The instruction may comprise a Web service call according to some embodiments. The instruction may be transmitted by the client application in response to user manipulation of a user interface presented by the client application.

Therefore prior to S the user navigates to user interface and completes the inputs fields thereof. The user then selects Hire Employee icon causing client to transmit an instruction to business process platform e.g. via HTTP to create a new employee. This instruction is received by business process platform at S.

The instruction may include a session identifier e.g. cookie per the HTTP protocol. Business process platform assigns the instruction to work process and the session identifier is associated with the create employee business process to be performed by work process .

Accordingly work process executes the business process at S. Execution of the business process may include but is not limited to instantiating populating and manipulating business objects within business process platform . A business object may comprise a class defining data and methods associated with a business entity. For example S may include creation of an employee business object an employment business object a work agreement business object a compensation agreement business object etc. as well as definition of dependencies therebetween.

During execution of the business process work process stores corresponding progress information in shared memory . Detailed examples of generation and storage of the progress information are provided below. According to some embodiments the progress information is stored in shared memory in association with the session identifier. Such storage enables retrieval of the progress information from shared memory based on the session identifier.

Next at S it is determined whether the business process is complete. If not flow returns to S to continue execution of the business process as described above. Stated differently flow cycles between S and S until the business process is complete.

During the aforementioned cycling between S and S progress information need not be stored into shared memory continuously. Work process may store progress information at S only upon determining based on the ongoing execution of the business process that the progress information should be updated. The updated progress information is also stored in association with the session identifier at S. It may be preferable to overwrite previously stored progress information to avoid confusion as to which is most recent.

Process continues as described above until it is determined at S that the business process is complete. In response work process may issue an instruction at S to release the area of shared memory reserved for storing progress information.

Process may be performed in parallel with process of . Generally as progress information is stored and updated in a shared memory according to process the progress information may be retrieved therefrom and provided to a client application according to process . In some embodiments the progress information is stored and updated by a first software work process e.g. work process and is retrieved and provided to the client application by a second software work process e.g. work process .

Initially at S a progress request and a session identifier are received from a client application. For example client may send a progress request and the session identifier to business process platform from the same client session used to send the instruction received at S. Client may send the progress request at a pre designated interval e.g. 1 second after sending the instruction.

Business process platform assigns the progress request to work process and at S work process retrieves the progress information from shared memory . Work process may use the received session identifier as a key to retrieve the progress information from shared memory at S.

Next at S second work process provides the progress information to the client application. Such provision may proceed according to the standard HTTP request response protocol. More specifically the progress information is sent via an HTTP response corresponding to the HTTP progress request received at S.

Flow returns from S to S to await another progress request. If another request and session identifier are received progress information is again retrieved from shared memory at S as described above. Due to concurrent execution of process the now retrieved progress information may be different from the progress information retrieved in response to the last progress request.

The now retrieved progress information is provided to the client application at S. Continuing with the present example is a view of user interface displayed by client after S according to some embodiments. User interface includes progress information window the contents of which have changed since the time represented in .

Specifically window includes the text Creating Employment Agreement . . . and progress bar is more advanced than shown in . User interface thereby provides a visual indication of advancing progress according to some embodiments. Again any other information indicative of execution progress may be provided at S and that information may be presented by the client application in any suitable manner.

Business process platform may comprise a service oriented architecture to provide services to client and to other clients according to some embodiments. Business process platform includes dispatcher process to receive HTTP requests from client and to forward the requests to appropriate work processes. For example dispatcher process may receive an HTTP request associated with user interface floorplan functionality and may dispatch the request to ABAP dialog process . Based on the type of request ABAP dialog process calls an HTTP Handler UI .

Local Client Proxy LCP Wrapper of ABAP dialog process forwards the request to an Enterprise Services Framework ESF . As is known in the art the ESF manipulates business objects BOs to provide enterprise services. The ESF may also issue requests to an Enterprise Controller Object ECO associated with the currently viewed UI floorplan. The ECO may provide additional business knowledge and functionality behind the operation of the UI floorplan.

Progress information service as will be described in detail below receives information generated by one or more BOs of process and provides the information to the ECO. Progress information service may also receive progress information from the ECO and store the progress information in shared memory. Progress information service may provide an application programming interface of static class methods to facilitate this operation according to some embodiments.

Upon receiving a request for progress information dispatcher process may dispatch the request to ABAP dialog process . In turn ABAP dialog process calls an HTTP Handler Progress . As will be described below the HTTP Handler Progress uses progress information service to retrieve the progress information from shared memory and returns the progress information to client .

Client may comprise a Web client as described above. UI controller of client may comprise a software thread to control a user interface displayed by client . Requests related to user interface functionality are passed from UI controller to HTTP connector UI communication thread and on to platform . Similarly UI controller passes requests for progress information to HTTP connector progress communication thread .

System may execute processes and according to some embodiments. In a specific example an instruction to execute a business process associated with a UI floorplan is passed from UI controller to HTTP connector UI communication thread to dispatcher process and is received by dialog process at S.

The ECO may then call an interface of progress information service to register therewith. Registration informs progress information service to provide the ECO with any progress related information received from the BOs during execution of the business process. The following interface may be used 

Next the ESF BOs and ECO of process operate to execute the business process at S. During such execution one or more BOs may generate progress related information and provide this information to progress information service via an interface such as 

Due to registration of the ECO progress information service performs a callback to the ECO upon receipt of the information from the one or more BOs. The callback may be implemented as follows 

Based on the information received in the following callback and based on its knowledge of the overall business process being executed the ECO determines at S whether progress information should be stored in shared memory . If so the ECO also determines the actual progress information to be stored. In this regard each BO is unaware of its role or its temporal position in the currently executing business process. Instead each BO simply provides low level information indicative of its current state. The ECO gathers this information via progress information service to determine progress information associated with the current process.

The ECO calls another interface of progress information service to store progress information in shared memory . The foregoing is an example of such an interface according to some embodiments 

The progress description may be dependent on the language governing the current session. Accordingly the ECO may select a particular progress description from a database or other structure depending upon the governing language.

Turning to process after receiving a request to retrieve progress information at S the HTTP Handler Progress of process may call an interface of progress information service in order to retrieve the progress information 

Once the ECO determines that the business process is completed at S the ECO may call the following interface at S to reset shared memory 

Some embodiments of the foregoing may therefore efficiently provide progress information to an end user in a service oriented architecture.

Each system described herein may be implemented by any number of devices in communication via any number of other public and or private networks. Two or more of devices of may be located remote from one another and may communicate with one another via any known manner of network s and or a dedicated connection. Moreover each device may comprise any number of hardware and or software elements suitable to provide the functions described herein as well as any other functions. Other topologies may be used in conjunction with other embodiments.

All systems and processes discussed herein may be embodied in program code stored on one or more computer readable media. Such media may include for example a floppy disk a CD ROM a DVD ROM a Zip disk magnetic tape and solid state RAM or ROM memories. Embodiments are therefore not limited to any specific combination of hardware and software.

The embodiments described herein are solely for the purpose of illustration. Those in the art will recognize other embodiments may be practiced with modifications and alterations limited only by the claims.

