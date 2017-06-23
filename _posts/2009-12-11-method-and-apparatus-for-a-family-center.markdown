---

title: Method and apparatus for a family center
abstract: A family center system and method is provided that allows receiving from a registered family member a family message intended for other registered family members and determines, based on a set of rules, to which of other registered family members to push the family message, mode of transport by which to push the family message, and the schedule according to which to push the family message. A technique involving a tile is provided that allows displaying a unified view of information onto a plurality of registered devices, regardless of device platform and/or communications network. The system and method provides a variety of services to registered family members and allows third party application plug-in for offering third party services. The system and method receives a SMS message and stores such message as a family message for subsequent access or family message treatment.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08463872&OS=08463872&RS=08463872
owner: Broadsoft Casabi, LLC
number: 08463872
owner_city: Gaithersburg
owner_country: US
publication_date: 20091211
---
This application is a continuation in part of co pending U.S. patent application Ser. No. 11 745 888 filed 8 May 2007 now abandoned which is a continuation in part of co pending U.S. patent application Ser. No. 11 175 991 U.S. Pat. No. 7 975 011 filed 5 Jul. 2005 which claims priority to U.S. provisional patent application Ser. No. 60 585 375 filed 2 Jul. 2004 each of which is incorporated herein in its entirety by this reference thereto.

The invention relates to a communications architecture. More particularly the invention relates to services provided in connection with a proxy based communications architecture.

In today s world personal computers cell phones smart phones even televisions and the like provide services and content beyond the original purposes of these devices. For example a personal computer doesn t simply compute but opens browsers to remotes web sites for users to browse. As another example as well as talking on cell phones users can send Short Message Service SMS messages across mobile networks or browse the Internet. It is not uncommon for a single user to own or have access to a variety of such devices. However when the single user desires to use any of the devices the single user is required to become familiar with the particular platforms and run time applications associated with each of the devices. Such requirement is a direct result of the limitations of the hardware and software of each of the devices. For example if a user desires to open an address book from his or her PC the user must be familiar with the particular address book application on the PC. If the user desires to open an address book on his or her smart phone the user must be familiar with the particular address book application on the smart phone that is most likely different from the address book application on the user s PC. Further if the user needs to receive a message from a family member the family member has to guess the location of the user and or which device the user is likely to use. For example suppose the user is a parent and the family member is the parent s child. Suppose further that at some later point in time the child will call the parent to request that the parent pick him or her up from a friend s house. As in a typical family the child does not know the exact location of the parent. The parent may be at home may be outside gardening or may even be grocery shopping. Typically then the child has to guess the location of the parent and then guess to which device the parent is likely to have access. For example the child may send an SMS message to the parent s cell phone. Thus the parent may or may not view the message in a timely manner depending on whether the parent has access to his or her cell phone at that time. The parent may have gone upstairs to a different part of the house to read his or her email on a PC and left his or her cell phone in the kitchen downstairs. Thus the parent reading emails on the PC will not receive the message that requests pick up from the child in a timely manner that is until the parent learns that a message has been sent to his or her cell phone. Thus it is a disadvantage to both the parent and child that the parent sitting at the PC was not able to receive some type of notification on the PC as well as the cell phone that his or her child needs to be picked up. It would be advantageous for a message sender to send a single message from one device and have that message be delivered to many devices regardless of the different types of platforms of the devices and regardless of the different networks over which the content of the message needs to be sent. It further would be advantageous for the receiver of the message to get notification of the message at any of his or her devices and in a view that is independent of the particular type of device at which the receiver views the message that is in a unified view across the different types of devices.

A family center system and method is provided that allows receiving from a registered family member a family message that is intended for other registered family members and determines based on a set of rules to which of the other registered family members to push the family message the mode of transport by which to push the family message and the schedule according to which to push the family message. In addition a technique involving a tile is provided that allows displaying a unified view of information including family message information onto any of a plurality of registered devices regardless of device platform and or communications network. In addition the family center system and method provides a variety of family center services to registered family members as well as allows third party application plug in for offering third party services to registered family members. In addition the family center system and method allows receiving a SMS message and storing the SMS message as a family message for subsequent access such as for example for subsequent pushing to the appropriate device according to the appropriate mode of transport and schedule.

The following definitions are provided to clarify particular terminology used within the discussion hereinbelow and are not meant to be limiting. It should be clear to one skilled in the art that other terms could be used to convey the same understanding and can be considered within the scope and spirit of the claimed subject matter.

fcMessage Family Message FM or message The basic type of message that gets sent between fcMembers through the Family Center 

fcApplication or FC Application fcApplication is a component or process that runs on a particular device. fcApplication may be recognized as one or more client components that work in conjunction with FC which may be recognized as one or more core server components. fcApplication may be delivered via web client DECT smart phone and the like. In an embodiment fcApplication provides the user interface to the outside world. fcTile or Tile A consistent display element that provides user actionable data that can be presented on the fcApplication home screen User Any entity e.g. person who interacts with the fcApplication FamilyID The identifier id that uniquely identifies the family instance ServiceID The id assigned given to a specific web service to identify that service and associated privileges Notifications Event notifications are sent for event creation updates and cancellations and Reminders Event reminders are sent to remind family members than an upcoming event is arriving. Overview

A family center system and method is provided that allows receiving from a registered family member a family message that is intended for other registered family members and determines based on a set of rules to which of the other registered family members to push the family message the mode of transport by which to push the family message and the schedule according to which to push the family message. In addition a technique involving a tile is provided that allows displaying a unified view of information including family message information onto any of a plurality of registered devices regardless of device platform and or communications network. In addition the family center system and method provides a variety of family center services to registered family members as well as allows third party application plug in for offering third party services to registered family members. In addition the family center system and method allows receiving a SMS message and storing the SMS message as a family message for subsequent access such as for example for subsequent pushing to the appropriate device according to the appropriate mode of transport and schedule.

An embodiment of a family center system and method can be described with reference to a functional block diagram showing a proxy based family center communications architecture according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

Thus referring to and in accordance with an embodiment a family center system is provided and allows receiving from a registered family member for example from a PC Web Client a family message that is intended for other registered family members. Family center system determines based on a set of rules to which of the other registered family members e.g. a television TV and a smart phone to push the family message. The determination takes into consideration the mode of transport required by TV e.g. over a carrier network and smart phone e.g. over a mobile network by which to push the family message. The determination also takes scheduling into consideration. For example family center system may determine to send the family message to TV first and then after a specific time family center system sends the family message to smart phone .

In an embodiment family center system may determine to send the family message in the form of a tile to both smart phone and TV . For an example of received tile refer to . is a screen shot of a family center application home screen showing twelve displayed tiles according to an embodiment. A tile positioned in the top row and in the upper left corner originated from an iPhone. Tile displays a family message that originated from the iPhone. In this example the content of tile says Family message sent from iPhone client. What s up doc As well tile displays in a title bar a date and time at which the family message was sent. Tile also shows that this particular family message is the second out of two 2 2 for this particular user or family member.

As the name suggests tiles can be manipulated in a variety of ways such as for example reordering tiles on the screen by drag and drop causing an individual tile to disappear and effectively move to a next page and so on. The multitude of features of tiles is discussed in further details throughout and in particular hereinbelow in the section Tiles.

In an embodiment family center system may receive a request from one of the registered devices e.g. PC Web client for a family center service e.g. Calendar . For an example of a family center calendar service refer to . is a screen shot of a family center application showing a family center calendar page.

As well family center system may receive a request from one of the registered devices e.g. PC Web Client to deliver content from an external source e.g. from one of the third party applications . In this example at PC Web Client control goes to a designated URL and content that is associated with the designated URL is presented in a separate window on PC Web Client .

As well in an embodiment family center system may receive a family message from an SMS Mobile Phone in the form of an SMS message and store the SMS message as a first family message for subsequent access such as for example for subsequent pushing to the appropriate device according to the appropriate mode of transport and schedule.

At a high level family center system provides a hosted solution to users to receive complete communications and services. However in an embodiment family center system contains a plurality of components or processes to achieve providing a hosted solution to users. Particular components or processes of family center system according to an embodiment are described hereinbelow. It should be appreciated that any of such particular components or processes can be implemented purely in hardware e.g. as special purpose hardwired circuitry or in software. It should be appreciated that the use of the terms component or process herein may refer to either hardware or software and is not limited to referring only to hardware or to software.

In family center system contains one or more interface APIs . Interface APIs allow other components or processes within family center system to communicate with a variety of entities. In an embodiment and as shown in interface APIs communicate with the following external entities third party applications carrier applications and carrier resources . Such interface APIs enable external entities to define and address tiles through family center system such that family center system is able to deliver such tiles to specific registered families within family center system . A tile is a consistent display element that provides user actionable data that can be presented on a family center application fcApplication home screen and is discussed in detail hereinbelow. Interface APIs also contain APIs that define an interface between an fcApplication and family center system . Such interface APIs may also be used to define a tile.

In an embodiment and also as shown in Interface APIs interface with the following devices smart phone an enhanced media terminal adapter eMTA TV a custom device and PC Web Client . For example interface APIs allows any of devices that are registered with family center system to send a family message to family center system such that family center system ensures the family message is propagated to one or more registered family members.

Interface APIs allows the family message to propagate in the form of a tile to any configured registered device. In an embodiment a configured registered device contains part or all of a family center application e.g. fcApplication.

It should be appreciated that when the SMS mobile phone does not host an fcApplication but is registered with family center system family center system may send information reflecting a family message to SMS mobile phone in SMS message format. In addition family center system may still send information reflecting the family message to any of devices in the form of a tile.

Further details about the use of interface APIs between family center system and external devices as well as devices registered with family center system can be found in the appropriate sections hereinbelow. For example further details can be found in the Tiles section.

Interface APIs allow family center system to communicate with external entities and the registered devices over a variety of networks. It should be appreciated that in an embodiment such communication is bi directional. As an example interface APIs allow communication with smart phone and SMS mobile phone over a mobile network . Interface APIs allow communication with eMTA and TV over a carrier network . Interface APIs allow communication with custom device and PC Web Client over the Internet . An example of custom device is a tablet e.g. an eight inch screen that sits on a kitchen counter that contains a copy of fcApplication or part of such application that is associated with the tablet so that customer device is in communication with family center system . Another example of custom device is a digital picture frame.

It should be appreciated that fcApplication may also run natively on a PC not shown . For example fcApplication may be implemented using Adobe AIR . Thus in this example fcApplication may be referred to as an AIR client. The look and feel of fcApplication as an AIR client may be similar to fcApplication as the web client however as an AIR client fcApplication is present on the PC desktop without need for a browser.

It should be appreciated that in an embodiment a DECT phone connects to eMTA that is in communication with family center system over carrier network . An exemplary DECT phone is a particular handset to which communications services are brought to individuals and is discussed in the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007. As well any other type of voice service that is able to be in communication with eMTA may also be in communication with family center system over carrier network .

Similarly TV is in communication with family center system by TV being in communication with its set top box that is in communication with carrier network that is in communication with family center system . Thus family center system can push content to the screen of TV through the path described hereinabove and a television viewer can communicate with family center system via the same path as the path is bi directional.

In an embodiment smart phone communicates with family center system by first communicating over mobile network which then communicates with Internet back to family center system e.g. over the top application. Thus smart phone communicates with family center system using Internet . It should be appreciated that interface APIs may communicate directly with SMS mobile phone over mobile network .

It should be appreciated that the types of devices and communications networks discussed above are illustrative and are not meant to be limiting. One skilled in the art can readily understand that other types of devices and communications networks can be employed and still be within the scope and spirit of the claimed subject matter.

Family center system provides a variety of services to users. For example family center system provides voice mail SMS an address book local directory search email a calendar task or To Do s lists and the like. In an embodiment and referring to family center system contains the following components or processes Voice Mail SMS Address Book Local Search Email and Calendar .

An exemplary Voice Mail service Address Book service Local Search service and SMS or Instant Message service can be found in the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007.

Further detailed descriptions of Address Book Local Search and Calendar can be found hereinbelow in individual sections under the title of the same name.

It should be appreciated that the types of services discussed above are illustrative and are not meant to be limiting. One skilled in the art can readily understand that additional or different services may be provided and be within the scope and spirit of the claimed subject matter.

Family center system contains a tile handler component . Tile handler allows the placement of tiles on the home screen of an fcApplication as follows. For example tile handler allows the placement of tiles on the home screen of fcApplication on PC Web client . In an embodiment tile handler receives a particular API from a source such as a third party application and based on information contained in the API creates a particular JavaScript Object Notation JSON document that is associated with the API and pushes the JSON document to PC Web Client . In another embodiment tile handler creates an XML data structure that reflects the information contained in the API and pushes the XML data structure to the particular registered device such as PC Web Client . It should be appreciated that one skilled in the art can use any other data structure format with which to send the information contained in the API and that the JSON document and XML data structure are by way of example and are not meant to be limiting.

In an embodiment family center system provides one or more components that manage a registered DECT phone A. In an embodiment family center system contains the following components for managing DECT phone A a DECT phone manager a session border controller SBC and a Session Initiation Protocol SIP soft switch where SBC is a standard third party system that manages connections to generic SIP devices. In an embodiment the functionality of DECT phone A is simple such as displaying screens or determining when a key on DECT phone A is pressed. For example such components may control the user interface on DECT phone A. In an embodiment SIP soft switch allows voice calls to be placed between one or more DECT phones that are registered to a same family. Exemplary DECT phone functionality is discussed in the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007.

In an embodiment family center system contains a voice to text converter component . Voice to text converter converts voice input stream to text output. Third party voice to text converters are readily available on the market and may be used within family center system . As an example a family member may pick up DECT phone A and as he or she is getting ready to leave the house sends a family message from DECT phone A intended for delivery to the other family members. The family message which is in the form of a voice message is sent through eMTA over carrier network to family center system . At family center system voice to text converter converts the voice stream from the family message to text. Then family center system stores the converted family message FM2 in a family center component which is discussed in further detail hereinbelow for subsequent processing such as being propagated to the other family members. Thus as illustrated in this example a user can talk into a device to leave a message that is intended for the family and doesn t have to take the time to type out the message or select or type in the names or addresses of all the intended recipients.

In an embodiment a media server is provided that can convert input media of a variety of formats into a different type of media also of a variety of formats. For example suppose a family member creates a family message in a media that DECT phone A cannot interpret. Family system determines that such family message needs to be converted to a format that DECT phone A can interpret before pushing the family message to DECT phone A. Family center system gives control to media server which converts the family message to a format that DECT phone A can interpret such that the converted family message subsequently gets pushed or streamed directly to DECT phone A.

In another example in an embodiment voice mail messages are recorded and played back in mp3. However such voice mail messages are stored in family center in a format that is different from mp3. Thus when a family member while connected to PC Web Client for example desires to listen to a voice mail message from the family center application media server converts the voice mail message that was stored to mp3 and delivers the mp3 content to PC Web Client for the family member.

It should be appreciated that an example media server is described in the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007.

It should further be appreciated that the particular details described above are illustrative and are not meant to be limiting. It is readily apparent that one skilled in the art can contemplate adding a wide variety of devices and third party applications that can communicate with family center system and still be within the scope and spirit of the claimed subject matter.

In an embodiment family center system contains a family center application component that is in communication with a database component. It should be appreciated that family center and database may be an application and repository that work together in such a way that one skilled in the art can understand that referring to family center may imply referring to database and that referring to database may imply referring to family center . One skilled in the art can understand that in an embodiment database may be any third party database on the market and is used as a tool.

Family center contains and handles data that embodies the notion of a family and all the attributes of a family according to an embodiment. As well family center contains and handles data that embodies the notion of a group and all the attributes of a group according to an embodiment. In an embodiment the family is a type of group.

For example and referring to family center contains a data structure that represents a registered family and contains informational data about the family family instance . In the example family instance is a member of a group instance which is also a data structure. Also in this example and in accordance with an embodiment family center contains data reflecting two registered family members family member A and family member B. Family member A and family member B are members of family instance data .

An example of an attribute of family instance is a list of one or more devices that are registered to the particular family. For example smart phone SMS mobile phone DECT phone A TV custom device and PC Web Client may each be a registered device of family instance .

It should be appreciated that certain functionality of Group according to an embodiment are described hereinbelow in particular detail. For example Group functionality is described in detail in the context of Address Book and Family Calendar. However one skilled in the art can readily appreciate that the particular details are not meant to be limiting and are for illustrative purposes. Thus while not described in particular detail the notion of group can be used in other applications such as for example group messaging through SMS or other means. As an example a particular fcMember may create a group of individual members labeled Soccer team and then send an SMS message to the entire group by sending the SMS message to Soccer team as opposed to sending a particular SMS message to each individual member of Soccer team.

In an embodiment family center system contains a family message handler that handles family messages. In an embodiment family message handler handles scheduling routing and transporting of family messages and a data definition of the family message. In an embodiment the particular definition of family message is stored in database . A particular family message is associated with a family and is independent of any type of transport. Family message handler handles a family message based on attributes of family instance and specific rules not shown . Such rules may reside in database for example and may be retrieved by family message handler whenever needed by family message handler . For example family message handler determines based on rules and family attributes which devices e.g. which devices are registered to the family to push the particular family message. Continuing with the example above family message handler determines to send the family message to smart phone SMS mobile phone DECT phone A TV custom device and PC Web Client because each of such devices are registered with family center system .

In an embodiment family message handler determines when to send a particular family message to a particular registered device based on a particular family member s configurations. For example family member A may contain data reflecting that smart phone is not to receive any family messages after 10 pm and to resume receiving family messages at 7 am. Thus when family message handler receives a family message at 10 30 pm family message handler determines not to send family message to smart phone .

An example of family message handler determining transport is as follows. Continuing with the example above family message handler receives a family message. Family message handler determines the family message is to be sent to SMS mobile phone which does not host any processes such as fcApplication for example that is associated with family center system . SMS mobile phone contains standard mobile phone functionality. Thus family message handler determines to send the family message to SMS mobile phone using SMS .

It should be appreciated that in an embodiment lists e.g. a list of family messages or a list of tasks can be sent via SMS to family members. As well in an embodiment when a task is added to a list such task that is associated with the list is sent via SMS to family members having the list.

As well family message handler determines that the family message is to be sent to smart phone . In this example smart phone contains a copy of or part of a copy of fcApplication which allows for example tiles to be displayed on the screen. Thus in this situation family message handler determines to use a different transport mechanism to deliver the family message to smart phone than SMS . Family message handler determines to send the family message to smart phone using a particular protocol that fcApplication can interpret.

In an embodiment family message handler uses family message protocol as a transport scheme by which to send family messages to registered devices that contain fcApplication or part of fcApplication. In an embodiment family message protocol contains a list of family messages that are intended to be displayed by fcApplication. In the embodiment such list of family messages are provided to fcApplication in a JSON document or other data structure format such as XML.

Thus in an embodiment sending a family message depends on the device. When the family message is sent to a standard phone that is not configured with any part of the family center application family message handler causes the family message to be sent over SMS. When the family message is sent to a DECT phone family message handler causes the family message to be sent over SIP. When the family message is sent to a device running fcApplication family message handler causes the family message to be sent using family message protocol .

In an embodiment family message handler may send notifications of a new family message to a registered device and not deliver the family message to the registered device. In this case the particular device may have access to the family message that is stored in the family center such that the family message can be viewed by a user at the registered device.

An example of a screen shot of a family message according to an embodiment can be found in . shows the user interface of the running fcApplication and an opened tile that contains a family message. In this example the family message was sent by Jon and the content says can I get .

A mother sits down at PC Web Client and opens up the family center application thereon e.g. the copy of fcApplication residing on PC Web Client .

The mother desires to send a family message from PC Web Client . An example screen shot of a window for entering a new message can be found in . shows the input object on top of the family center application . In the example and according to an embodiment the mother can type in her family message or record her family message and send it along. Referring to in response to the mother creating the family message at PC Web Client family center generates and stores a copy of the family message . Family message handler detects family message is newly created and stored in family center . Family message handler determines to whom and how to propagate family message . Family message handler checks family members and family member devices that are registered with the family. In this example family message handler determines that family member A has registered SMS mobile phone . Thus family message handler packages data that is associated with family message into an SMS message not shown . Family message handler then passes the SMS message to SMS which then causes the SMS message to be sent over mobile network to SMS mobile phone . Also in the example another family member e.g. family member B has registered his or her smart phone e.g. smart phone . Family message handler packages data that is associated with family message as an over the top smart phone application and sends the over the top smart phone application over Internet to mobile network to smart phone . Also in the example a third family member is sitting in front of a television such as TV . The third family member not shown created configuration data that indicates to family message handler to show received family messages on the screen of TV . Thus family message handler packages data that is associated with family message into a format that TV can interpret and present on the screen. Then family message handler sends the packaged family message through an API at interface APIs over carrier network to TV .

Thus this example demonstrates how family messaging according to an embodiment can be a one to many messaging scheme.

Also in this example a receiver of the family message decides to reply to the family message. For example the family member at SMS mobile device replies to the family message. SMS mobile device generates an SMS message that gets sent over mobile network through the appropriate APIs at interface APIs to family center and is stored as family message .

In an embodiment family message handler does not send a family message back to the sender. Thus in the example family message handler determines not to send family message to SMS mobile phone because family message was sent from SMS mobile phone . However family message handler packages and sends family message to the remaining family members as specified.

This section describes a home screen login screen and registration process of the FC application according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

In an embodiment the Home Screen is the home page for the FC and displays tile notifications and alerts provides access to core FC applications also referred to herein as processes or components and quick access to key core FC application views. The Home Screen includes the Login Screen which provides security to protect user access to a family s FC account.

In an embodiment the display time day of week and date are displayed in the upper right hand corner and are persistent in all views.

In an embodiment branding is displayed in the upper left hand corner and is persistent in all views. The display may be customizable for carrier branding.

An example screen shot of an implementation of a Home view can be seen in . It should be appreciated that such implementation is by way of example and is not meant to be limiting.

In an embodiment six major tabs are shown across the top allowing quick access to the core FC applications and are persistent in all views such as but not limited to 

In an embodiment a Display Settings link is presented in the upper right hand corner next to login logout link for the user to access particular settings for particular core FC Applications. From the home screen a user may click on a new family message to create a new FM to be delivered to the configurable devices belonging to the family .

An example screen shot showing a Family Center Calendar according to an embodiment can be found in . The month view is selected in the left panel . A quick view option for upcoming events shows that there are two upcoming events . Displayed on top of the calendar on the right panel are two opened events A and B each presenting details of the particular event.

In an embodiment the right hand view of the application displays tiles. Refer to the Tile section hereinbelow for details on tile features and functionality.

In an embodiment in the right pane for initial startup new users can click on start up tiles to go through a type of introductory or walkthrough process that helps explain the following features 

It should be appreciated that such tiles described hereinabove are dismissed manually by the user. As well it should be appreciated that such tiles can be retrieved via settings. See Settings section hereinbelow for details.

Widget Dock e.g. the pop up application bar on the bottom of the window view displays system defined third party widgets e.g. applications in the widget dock and is persistent in all views.

In an embodiment the user and carrier have the ability to manage applications for the Widget Dock e.g. pop up bar as follows 

The following discussion outlines a registration flow according to an embodiment when the user first enters the FC application. The initial login and subsequent logins appear as part of the application. In an embodiment it is assumed that the user receives his or her login and password information from the carrier and that the login and password are provisioned prior to the user starting the application. In another embodiment the application requests the login or phone number and password from the user. In another embodiment an error message for incorrect entries directs the user to call or contact the carrier to verify login name and password. In another embodiment the application requests that the user enter in an email address e.g. for purposes of password retrieval and zip code. The user may be prompted to enter in the email address twice to confirm. Once the user completes the registration process the user enters into the FC application. It is contemplated that the user may enter in the application as a family member during the registration process or may enter in the application as a family member after the registration process.

In an embodiment the login screen is a screen that requests a username name and password. Upon subsequent entries may 

This section describes and outlines an fcTile definition and APIs to generate and display presentation within a web client according to an embodiment. It should be appreciated that fcTile and tile are used herein interchangeably. It should be appreciated that the particular details referred to hereinbelow are illustrative only and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

In an embodiment fcTiles are displayed within the home screen of the fcApplication. fcTiles are either locally generated by the fcApplication based on information associated with message types or they are generated based on a specific fcTile packet being pushed to the client.

fcTiles provide interaction with other fcApplication data e.g. voicemail playback or provide interaction with third party web services e.g. home security.

The fcTile defines both graphical information and functional information. The complete definition of an fcTile is encapsulated within a data structure such as a JSON document or XML for example and pushed to the fcApplication. The fcApplication displays the fcTile manages background functions on behalf of the fcTile e.g. auto update and handles the user interaction and display of information.

The third party applications can place or cause the placement of fcTiles on the home screen of the fcApplication through an API into the FC system FC e.g. into a hosted component in the FC system. That is a third party application may post a tile to the FC system. Such API contains information that describes a particular tile in detail and also particular delivery options of the tile such as to which clients time of day and so forth.

Then based on the information contained in the first API FC creates a data structure element such as an associated JSON document or XML structure reflecting or containing information in the API and pushes the data structure such as a JSON document to the fcApplication through a second API. Put another way the second API delivers the tile to fcApplication.

It should be appreciated that particular detailed descriptions herein of the first API and the second API are illustrative and are not meant to be limiting. One skilled in the art can readily appreciate that a wide variety of particular functions parameters attributes and elements of such APIs can be contemplated or used and still be within the spirit and scope of the claimed subject matter.

It should further be appreciated that while the use of JSON document used hereinbelow is for illustrative purposes and is not meant to be limiting. One skilled in the art can appreciate that any other data structure such as an XML data structure can be used and be within the spirit and scope of the subject matter as claimed.

A user interacts with an fcTile by clicking it. The type of tile defines the subsequent interaction options.

There are multiple types of fcTiles. Each type has a specific set of feature capabilities. The fcApplication manages how those capabilities are presented to the user.

As mentioned hereinabove there are two main but separate APIs that control or manage fcTile operation. The first API provides the external interface e.g. from third party applications to FC for defining fcTiles and addressing fcTiles to specific registered families within FC. The second API defines the interface between the fcApplication and FC that is used to define the fcTile. In an embodiment the first and second APIs have the same structure but their respective individual elements may vary. An example embodiment of the first API can be found hereinbelow.

Information elements that are pushed to the fcApplication through other features e.g. through a core FC Application such as messaging may include some fcTile attributes. Including some fcTile attributes is desirable to inform the fcApplication how to treat specific elements. For example a family message may have a fcTile option and priority option. When fcTile Yes and a priority is given the fcApplication creates a custom fcTile specific to the family message and display it in the appropriate priority location.

fcTiles are pushed to a family instance within FC. Pushing fcTiles to family instances insures that the fcTile is delivered to the associated family account. If the fcApplication is running then the fcTile is subsequently pushed to the fcApplication and an ACK is generated in return. If the fcApplication is not running then when it starts all relevant fcTiles are sent to the fcApplication.

The following parameters and or functions define an fcTile according to an embodiment. Such particular parameters and functions are meant to be illustrative and are not meant to be limiting. One skilled in the art may contemplate different parameters and functions and still be within the scope and spirit of the claimed subject matter. In an embodiment components of the following definition are encapsulated within a JSON document and delivered to the fcApplication. Required elements in an embodiment are marked with a 

Type The type defines both presentation options as well as functionality within the fcApplication. Examples of particular types are 

In an embodiment a tile can include an executable program such as for example a .swf file. When such tile is clicked the tile opens the program within a frame of the fcApplication and runs the program. The program may pull whatever data is needed or desired to which it has access. For example the program may pull data that reflects user click events. This feature allows third party partners to easily push or publish a running application and open the application within the fcApplication.

An example screen shot of a playing video stream can be found in . shows a movie Harry Potter and the Half Blood Prince in a local frame of the right pane of the client application . In this example the playing of the video stream is a result of a user clicking a tile representing the movie causing a click event e.g. click URL and the click event causing the streaming video feed to play within the frame. An example of a tile representing the Harry Potter movie can be found in . shows the tile for playing the Harry Potter movie in the third row and first column of tiles.

Append FamilyID When this flag is set the fcApplication appends the FamilyID to the Click URL when Click URL is posted.

Impression Flag When this flag is set the fcApplication sends an impression event to FC each time the fcTile is displayed on the home screen. This allows FC to keep track of each time the tile is presented in such a way that a user can see it. If the fcTile priority causes the fcTile to be located on the second page of the home screen for example or some other page of the home screen then the fcTile generates an impression when it is moved to the home screen. Generating and Interacting with fcTiles Through Third Party API

The following section outlines the functionality available to generate fcTiles and receive input back according to an embodiment. The API from a third party communicates directly with the FC itself. FC then communicates with fcApplication on behalf of the third party application. There are instances as defined in the JSON Document wherein the fcApplication communicates directly with third party servers bypassing FC e.g. to receive video streaming and or an HTML web page.

Once FC receives the fcTile API request FC creates the fcTile saves it locally with the FC database and then sends a fcTile JSON Document that is associated with the particular fcTile to all relevant fcApplications.

It should be appreciated that SMS messages are sent to FC either from the network through SMS API or are newly created within the fcApplication. Thus in an embodiment FC receives an SMS message from the network creates an fcTile to send the content of the message within the tile to fcApplication and also sends the SMS message directly to standard mobile phones that do not run fcApplication.

Return result FC receives the fcTile request verifies the contents and returns the following results 

A static fcTile is a reduced functionality version of the full fcTile. In an embodiment the intended use is to allow third party applications to place a graphic with associated link in the MyApps pop up section of the fcApplication or any other designated place of the fcApplication. These tiles are not intended to be interactive. Such tiles are effectively a bookmark with graphic such that when clicked control goes to a designated URL with or without an appended FamilyID. In an embodiment the static fcTile requires the following subset of the full fcTile definition 

In an embodiment FC provides a web interface for managing and tracking fcTiles. Such web interface may only be available to FC system administrators. In an embodiment the web interface provides the following capabilities 

fcTile List List of all outstanding fcTiles. In an embodiment the list is sortable by FamilyID Service ID pending vs. sent etc.

Click Impression Refresh Remove Tracking In an embodiment the fcTile events including click impression refresh or remove are trackable and sortable by Service ID Family ID etc.

This section defines user settings available through the web client for Family Center according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative only and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

The Settings tab on the fcApplication provides access to configuration options associated with the family s account. An example of a screen shot of a Settings view can be found in . shows the Settings tab is highlighted to indicate that the Setting view is the current view. The right panel shows actionable data that the user can interact with or provide for setting specific settings for family messages.

Upon initialization the fcApplication requests the particular JSON Settings document that contains settings for the individual family account. In an embodiment changes are made locally within the fcApplication with the change subsequently being saved back to FC.

The Settings screen layout follows the fcApplication paradigm with left navigation pane and right full screen layout. In an embodiment the left pane main categories are as follows 

The family members category provides a technique to manage family members e.g. add edit unassign and configure settings for each fcMember. The left pane contains a list of individual fcMembers and an add option.

In an embodiment each fcMember setting includes a method for obtaining more information on the item. Possible examples include hover brings up dialog that brings up dialog. The items marked with a may be included in the family member wizard setup. In an embodiment the First Name and Color are requested to create a family member profile. In an embodiment creation of a fcMember through the wizard or settings may also create a corresponding address book entry for that fcMember. Details of certain attributes are described as follows 

Clicking the indicator brings up an empty form and allows the user to enter the parameters for a new family member. Hitting the Submit button saves the values. The process also creates an address book entry of Category Family .

Once created the Family Member entry is tied to the address book entry for the family member. Any change in either side is reflected in the other.

Family members address book entries are not delete able unless a particular member is no longer denoted as a family member.

In an embodiment within the detailed view of each family member the user is able to modify the details of the family member for example as follows 

In an embodiment the user has the option to assign an existing address book entry and make it a family member .

In an embodiment the user is able to unassign a family member i.e. denote an address book entry as no longer a family member.

The Features category provides a list of the native features of FC in the left pane. Clicking on any feature brings up its associated settings for example in the right hand pane.

In the system settings the default view may appear as a read only view with the pertinent system fields and preferences set. In an embodiment the user may need to enter the password to be able to edit any field. Passwords and PINs may be blacked out . Below are certain settings according to an embodiment 

Below is a list of configuration parameters for how voicemail messages are displayed on fcApplication and for how a user can interact with their network based voicemail according to an embodiment 

Below is a list of configuration parameters for how TEXT messages are displayed on fcApplication according to an embodiment 

Below are configuration parameters for how family messages are displayed on fcApplication according to an embodiment 

Below is a list of configuration parameters any of which may be used to set calendar display in fcApplication according to an embodiment 

A configuration parameter to set address book display in fcApplication according to an embodiment is as follows 

This section provides a technique for third party applications to enter an application name and a link to a configuration page that displays within the frame of the fcApplication. In an embodiment the fcApplication provides no unique logic for any of the application settings links the third party application provides the logic.

The Settings Document may include a name and URL for each third party settings option that may be provided.

In an embodiment FC may require changes to the features displayed on the DECT phone. An exemplary DECT phone is discussed in the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007.

This section discusses and outlines fcAddress Book features and presentation within the web client according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative only and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

The Address Book is displayed as a core application of the Family Center. The Address Book allows the user to access an address book and use it as their center of communications to initiate calls and messages and enhance existing applications.

It is assumed herein that features and functionality behaves substantially the same on the DECT phone service unless specifically noted otherwise.

In an embodiment the Address Book screen layout follows the paradigm of left navigation panel and the right main page view.

The left column panel provides quick access views of specific address book categories and the categories are as follows 

In an embodiment the address book application provides a technique for accessing and viewing address book entries and creates and manages address book entries. Below is a detailed description according to but not limited to an embodiment.

In an embodiment favorites are a user defined list of frequently accessed contacts and associated numbers i.e. Mom mobile Dad work Ted mobile etc.

A favorite entry is the contact name and preferred contact number e.g. mobile and not the address book entry e.g. Dad mobile .

Group is a category classification for address book entries to help organize address book entries into more manageable and contextually relevant views for the viewer.

 Family is a special type of group and supports the same functionality in groups and has the following functionality.

According to an embodiment a user can create custom groups and manage their entries within these groups as follows.

User clicks on to create a new group and a new group appears in the list with the title highlighted thereby prompting the user to edit. Default name may be Group where the represents a number that increases incrementally to avoid duplicate named groups.

Call Logs present a list of the most recent incoming outgoing and missed calls. The call logs may be arranged from most recent received to least recent received for example.

It should be appreciated that in an embodiment the DECT Phone UI for call logs are defined. An exemplary DECT phone is discussed in the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007. Thus in this discussion hereinbelow the following description applies only to the FC Application.

The user can create a new address book entry or add to an existing entry from other features and services within the fcApplication. For example users may receive a voicemail and text message and if there is no address book entry name associated with the number the user can opt to click on an option to create or add to existing address book entry. The address book entry form pop ups and the user can enter the pertinent information. In an embodiment such functionality is available from the following services 

This section defines and describes a Family Center calendar features and functionality according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative only and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

The Family Center Calendar is an on line scheduling tool for creating and managing a family calendar. It provides the tools for users to do the following 

In another embodiment to do list is functionally separated from and taken out of Family Center Calendar. In an embodiment to do list can be accessed by a top level tab on the Home page. It should be appreciated that while the functionality of the to do list is described in part as being within Family Center Calendar one skilled in the art can recognize that all or part of such functionality is not limited to operating from within Family Center Calendar and can operate at a higher level independent of Family Center Calendar.

The calendar provides multiple views to achieve more granularity to better manage the family calendar. The views are split into two major groups quick access items in the left hand pane and major views and navigation elements in the right hand pane.

In an embodiment the left pane view provides access to different time based views of the calendar. The left pane view may include any of 

Along the top of the right view users may be able to control the calendar view by month and by week by family members navigate forward and backwards within the calendar and perform basic calendar functions.

Default View in an embodiment is the Calendar view by Week and view by all family members with Today s date is the default view which is highlighted.

The Calendar automatically accounts for leap years and uses the system zip code to determine the time zone.

In an embodiment users can enter events via four methods. One skilled in the art can readily appreciate that such methods are by means of illustration and are not meant to be limiting. Other methods may be used that are within the spirit and scope of the claimed subject matter. The methods are described in further detail hereinbelow.

Users can enter the details of an event by filling out a form with predefined field designations. The user is not required to fill out all the fields of the event form. The date and time are pre populated as defined by the context above and defaults to members as participants. If no fields are populated other than the date and time and the default members then no event is created.

A user can sync events between his Family Calendar and his Outlook account. This sync functionality allows the user to keep both his personal professional calendar and his family calendar coordinated and separate.

When a user is on his Family Calendar account he can configure his Calendar settings to automatically add family events to which he is invited both individual and family events to his personal calendar. Similarly when a user is using his personal calendar and creates an event he has the option to include the event and populate his individual family member calendar within the Family Calendar.

Any changes to an event such as edits and deletion or cancellation of an event appears in both calendars that are updated in real time e.g. after the edit is made in one calendar and saved the other calendar is notified and makes the appropriate changes in its calendar. The goal is to have the events designated to be shared on the family calendar be coordinated with the user s Outlook calendar. It should be appreciated that based on technical implementation the features UI may change.

A user can populate his Family Calendar with events from his personal calendar or calendars from other sources such as schools sports teams clubs and other organizations. This feature is a one way import.

According to an embodiment there are two ways to import a file. A user can click on import from the calendar view and be prompted to either a select a third party provider e.g. Outlook Plaxo Google Yahoo or b select a file to import. It is contemplated that different formats are supported as support becomes available for ensuring growth and scalability.

To help family members coordinate and stay updated the calendar sends notifications to configured family members via text message upon the creation modification and deletion of an event. No tile is created.

The Family Calendar pushes a tile notification to the home screen before the event as defined by the event notification configuration hereinabove and sends a text to participating family member s .

The Family Calendar provides an added feature in notification and support for special events such as birthdays and anniversaries. For example a user can designate an event as a special event within the event details as a checkbox and the application sends a countdown tile notification to the home screen and sends a text message and email at one or more defined time periods to periodically remind the family of the upcoming event. It should be appreciated that special events can be edited the same as a regular event but the user sees additional configuration options for special events.

In an embodiment the family calendar stores event information for each family calendar for three 3 years past and three 3 years forward from the present year.

In an embodiment Calendar can create a personalized calendar view for an individual within the family. For example Dad can register a third party application e.g. his iPhone with FC system and indicate that he desires to have a personalized calendar view. For example he may select a box that then causes the personalized calendar view functionality to apply his calendar related events. Thus after registering the iPhone with personalized calendar view turned on Dad then receives only those calendar events that are marked for the family or for Dad. It should be appreciated that choosing a personalized calendar view may appear as the opposite feature of a user publishing events from his or her personal calendar to FC system. It should be appreciated that by way of personalized calendar view the user e.g. Dad can manage his or her calendar from his or her device e.g. from third party iPhone application and FC system synchronizes such third party calendar application with his or her personalized view of the FC calendar.

This section describes Local Directory Search LDS Features and Functionality according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative only and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

The FC Local Directory Search LDS provides users with a local search resource to find local businesses and services and it becomes their default family yellow pages . Integrated with enhanced functionality such as click to call and mapping the Local Directory Search is a powerful directory search tool that allows users to quickly fulfill their local search needs.

It is contemplated that LDS may provide additional features such as recommendations personalized offers and coupons together with on line advertising e.g. banner ads and sponsored links.

LDS follows the existing view paradigm wherein the left pane creates quick access to links that expedite the search process for popular and recent searches. The right pane allows the user to conduct a more detailed and customized search with enhanced search result listings and details.

The left pane quick access provides a listing of quick links to popular searches recent searches recommendations targeted offers and coupons.

The right pane provides the user the UI to perform a local search. In the right pane a persistent search box the default search start page search results and search details are displayed.

In an embodiment search results requirements fall into two categories the search results page and the details of a specific search result.

The search results page displays the list of search results based on the user s search keyword and defined search criteria. In addition this page may render sponsored links positioned within the search results page and visibly distinguishable from the search results.

Following are sample examples of criteria for displaying a list of search results according to an embodiment 

User can sort results by distance by ratings and alphabetically. List is sorted by distance by default from closest to furthest. To sort the user can click on the relevant header title.

In an embodiment three contextually relevant sponsored links e.g. paid search links appear after the top three search results. UI treatment of the presentation or functionality of sponsored links clearly distinguishes the sponsored links from the search results.

An example of a search results screen shot can be found in . is a search results view of the client application and shows categories saved searches and notepad options in the left pane. The right pane shows search results for pizza delivery san diego and radius 5 m . Three items each representing a particular pizzeria are displayed. The first item represents Papa John s Pizza the second item represents Roundtable Pizza and the third item represents Domino s Pizza. It should be appreciated that each of the items show a phone icon whereby a user can click the phone icon and initiate a phone call to the particular pizzeria.

It is contemplated that the FC Local Directory Search supports on line advertising and provides a portfolio of advertising products from standard ad vehicles such as banner advertising to the ability to support features such as click to call .

This section describes and outlines messaging inbox management and associated messaging features for voicemail family messaging and text messaging according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative only and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

The inbox is the central FC messaging hub wherein users can retrieve messages e.g. voicemail family messages and text messages manage their inbox and initiate new messages.

In an embodiment the Inbox screen layout follows the paradigm of left navigation pane and right full screen layout.

An example screen shot of displaying text message detail within the family center application can be found in . shows that a message tab is highlighted to indicate that the view is a message view . The left pane of the view shows that a text message category is highlighted. Highlighted text message category indicates that the right pane is showing text message details .

Displays list of all messages e.g. unread and read all message types sorted with the most recent on top.

Click on a New button to create a new message. The New button is located along the top of the right pane view.

In an embodiment Voicemail Message displays the following Sender Name Date and Time Length min sec PLAY button and delete button.

In an embodiment family messages get created and posted on all connected devices and forwarded to configured family member cell phones as text messages.

When a user sends out a family message that user is not designated to be a recipient of his or her own family message. The following conditions also apply 

In an embodiment family message functionality support is provided for but not limited to family devices such as FC application and the exemplary DECT phone as described in the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007.

In an embodiment family message communication can be done through a dedicated telephone network TN for the family or through a shared TN for multiple families. FC supports either mode. For example when a family purchases the FC service with a dedicated TN then all family messages are sent through that TN.

In an embodiment FC system can virtualize family messaging for multiple families behind a single TN. Thus many to many communication is provided by FC. Many to many communication is achieved by FC system grouping members of a family by the mobile TN of each family member. Thus when a SMS message is received on the shared TN the source of the SMS is checked. If the source matches a mobile TN configured within FC for any user the SMS is treated as an incoming family message for the family where the mobile TN is a member. Thus the family message SMS is resent only to members of that family. This feature allows a single TN to be used as a virtual TN for inter family communication. In an embodiment such functionality is performed by the FC system and service and is transparent to users.

Put another way FC system manages multiple group SMS communication through a single TN. FC system keeps the messaging straight by comparing the incoming TN on the SMS message to existing defined groups. If a match is found then the message body is sent back out only to the other members within the group. In this embodiment any need to have a dedicated TN for each family when doing SMS family messaging is removed.

In an embodiment each text message thread displays the following Sender Date and Time Stamp Text of most recently received text in the thread and ability to delete reply and forward .

This section describes including defines the To Do List features and functionality according to an embodiment. It should be appreciated that the particular details referred to hereinbelow are illustrative only and are not meant to be limiting. One skilled in the art could readily contemplate other elements or steps and still remain within the scope and spirit of the claimed subject matter.

The To Do List provides the family the ability to create and manage multiple To Do lists and tasks including the ability to distribute To Do lists via text message to family members according to an embodiment.

In an embodiment the To Do list feature is accessible as one of the top main feature tabs on the fcApplication. See the Home section hereinabove for further details.

The To Do list follows the paradigm of the left pane and right pane view discussed herein and as follows 

In an embodiment the To Do lists are accessible from DECT and mobile phone smart phone FC applications. For a description of an exemplary DECT phone refer to the instant application s co pending parent U.S. patent application Ser. No. 11 745 888 filed 8 May 2007.

In an embodiment users see a list of multiple to do lists at the top of the Left Pane View and each To Do list has its own tab. When the user clicks on a particular list tab the to do list associated with the particular list tab is displayed in the right pane view.

It should be appreciated that upon a rendered first view and upon a rendered application reset view of the To Do list a user may see the Generic To Do List View. On subsequent entries into the To Do list the To Do list application component remembers the last viewed list or causes the last viewed list to be stored and returns to that list view.

In an embodiment the user sees a mini calendar at the bottom of the left pane view with the month and year as the title. When activated the calendar is displayed showing a full month and with the current date highlighted. The user may have the ability to scroll forward and backwards to view previous and subsequent months. The default view is the current month.

In an embodiment the items from the selected To Do list are listed from oldest to newest unless reordered.

Although the invention is described herein with reference to the preferred embodiment one skilled in the art will readily appreciate that other applications may be substituted for those set forth herein without departing from the spirit and scope of the present invention. Accordingly the invention should only be limited by the Claims included below.

