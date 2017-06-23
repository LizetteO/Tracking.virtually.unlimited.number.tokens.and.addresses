---

title: Software component self-scrubbing
abstract: Software components “self-scrub” to improve software reliability, serviceability and availability (RAS). Each component designates a routine to perform a component level consistency check on major data structures and to verify the state of component. This is performed as an on-going task during the life of the component. The component registers an entry point with the system to receive notification of scrubbing parameter changes. The entry point is also called with the request to perform component-scrubbing operations. The entry point functions are responsible for executing within limitations on central processing unit (CPU) usage and memory footprint when performing scrubbing operations.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08205118&OS=08205118&RS=08205118
owner: International Business Machines Corporation
number: 08205118
owner_city: Armonk
owner_country: US
publication_date: 20090723
---
The present invention relates generally to detecting errors in software module storage and execution.

Whereas the determination of a publication technology or product as prior art relative to the present invention requires analysis of certain dates and events not disclosed herein no statements made within this Background of the Invention shall constitute an admission by the Applicants of prior art unless the term Prior Art is specifically stated. Otherwise all statements provided within this Background section are other information related to or useful for understanding the invention.

The effects of software errors can lay undetected for considerable lengths of time before they are detected. Many errors may manifest themselves in slight errors in results which may or may not be readily noticeable by the consumers of the outputs of the erred software modules.

When errors are finally discovered many times difficult forensic work must be performed to determine when the error first occurred in order to determine the full impact of the error over the undetected period of time.

There is a need therefore for a technology which detects these errors earlier improves the ability to recover and makes the problems easier to service.

Software components self scrub to improve software reliability serviceability and availability RAS . Each component designates a routine to perform a component level consistency check on major data structures and to verify the state of component. This is performed as an on going task during the life of the component. The component registers an entry point with the system to receive notification of scrubbing parameter changes. The entry point is also called with the request to perform component scrubbing operations. The entry point functions are responsible for executing within limitations on central processing unit CPU usage and memory footprint when performing scrubbing operations.

The inventors of the present invention have recognized and solved problems previously unrecognized by others in the art of early detection of errors which may occur in software modules and data structures stored in computer readable memory.

In our use of the term scrubbing we are referring to a process of examining the consistency of a software component and its associated data structures excluding any processes which attempt to correct or fix an error discovered within the software component or its data structures. This term should not be confused with data cleansing.

For example software component scrubbing examines past sequences of component executions to make sure certain sequences have been properly executed and that those executed components modified the proper areas of memory. Scrubbing may also verify that all dynamic links and references such as links to Dynamic Linked Library DLL components are valid e.g. each component referred to by a link is present consistent etc. . This term is prevalently used within the AIX UNIX and LINUX operating system arts for example.

Software component scrubbing is performed to improve software RAS. A configurable amount of system resources are dedicated to perform error checking on software component integrity and health. This allows for earlier detection of errors. Reliability is improved by detecting latent errors in the system. Serviceability is improved by detecting problems earlier and closer to their source. Availability can be improved since when problems are detected early there is a better chance for recovery.

According to our invention software component self scrubbing is implemented with a system framework as exemplified in and through program adoption of certain operations. We are using a new term self scrubbing to describe an approach and applications of that approach into technologies in which each software module is tasked with providing its own scrubbing technologies for itself and only itself. In this manner each compliant software module is provided into a system complete with scrubbing technology required for it and external or third party scrubbing technologies need not be provided or coordinated by the author publisher of the self scrubbing software components. In arrowed lines which are solid denote program flow and arrowed lines which are dashed or broken denote interface operations or co operations.

The following logical process or processes can be implemented as a combination of software and hardware such as software being executed by a microprocessor or alternatively may be implemented in part or whole in customized circuitry or electronic logic . Software component as used in this disclosure refers to an actual software module or instance of an object as stored in computer readable memory.

Self Scrubbing Self Designation. Each software component designates a routine to perform a component level consistency check on its own major data structures and to verify the state of component itself. In other words each software component designates a self scrubbing routine. The routine can be a portion of the software component itself or it can be a separate logical entity such as a separate software module in computer memory or even a separate electronic circuit. Self scrubbing is performed as an on going task during the life of the software component.

Registered Entry Points. The software component also registers entry point such as scrub ctrl with the computing system through which the software component receives notification of scrubbing parameter changes. The entry point is also called with a request to perform component scrubbing operations. Entry point functions are responsible for executing within limitations on CPU usage and memory footprint when performing scrubbing operations. They typically are given short execution intervals and are required to voluntarily give up or terminate when their execution window expires.

Self Scrubbing Framework. The self scrubbing system framework maintains a registration of all components that have registered scrubbing operations through registration of an entry point. For each registration component specific properties are maintained. Examples of component specific properties in our embodiment are 

At a system level scrubbing properties are also maintained. Examples of system properties in our embodiment are 

A scrub control command scrubsctrl is provided to manage software component scrubbing. It has the following syntax in our embodiment 

Component Commands. In our embodiment the following component commands are provided with associated parameters and valid ranges 

System Commands. Also in our embodiment system commands are provided which do not have a component name associated with them e.g. they do not apply to or affect a single component but affect overall self scrubbing system operation 

The following example of operation of our embodiment is for illustrative purposes only and should not be construed to set forth the extent or limitations of the present invention. Those ordinarily skilled in the art will readily recognize that this example scenario and operation is just one of many possible uses of the present invention.

The following example applies to an inode table which is a data structure common to Unix AIX and Linux systems. An inode contains important information pertaining to files within a file system. When a file system is created in UNIX a set amount of nodes is created as well. Usually about one percent of the total file system disk space is allocated to the inode table. The inode table contains a listing of all inode numbers for the respective file system. When users search for or access a file the UNIX system searches through the inode table for the correct inode number. When the inode number is found the command in question can access the inode and make the appropriate changes if applicable. Much more information on these well known structures and methods for use is available in Unix and AIX texts such as Speaking UNIX It s All About the inode by Adam T. Cormany of Scientific Games Corporation published by International Business Machines copyright 1994 and 2007 .

According to our invention when a filesystem component requires self scrubbing on its inode table the filesystem component registers an entry point filesystem component with the computing system providing the filesystem scrub callback.

And the filesystem component provides an inode table scrub function that checks entries in the inode table. The scrubbing function typically checks individual table entries until its execution window has expired. It then terminates until the next scrubbing callback is made.

On return the scrubber e.g. the scrub function periodically provides an indication to the system of its progress with a percent complete value. The system provides default properties for each component. These properties can also be altered on a running system with the scrubctrl command. For example the following commands request that the filesystem component is scrubbed once every 60 minutes at detail level 

Turning to an example logical process according to the present invention is shown. A self scrubbing Software Component X initially registers and entry point for its own self scrubbing routine with the framework .

During execution of Software Component X the framework maintains a plurality of error checking properties in addition to the entry point including for example monitoring the processor bandwidth consumed by Software Component X the data footprint utilized by Software Component X the calls from other components to Software Component X and the calls that Software Component X makes to other components.

When a calling or commanding system component initiates self scrubbing it obtains the registered entry point from the framework and calls the Self Scrubbing Routine with appropriate control parameters as previously described.

Self Scrubbing Routine then accesses and analyzes the error checking properties for Software Component X including for example the processor bandwidth consumed by Software Component X the data footprint utilized by Software Component X the calls from other components to Software Component X and the calls that Software Component X makes to other components. Any of these properties which are out of limits are then reported to the calling or commanding system component.

The calling or commanding system component may then use these results from the Self Scrubbing Routine to prepare and output a report to a user or administrator and to automatically schedule appropriate corrective action such as re allocation of system resources initiation of a repair or upgrade order and restarting of Software Component X.

Whereas at least one embodiment of the present invention incorporates uses or operates on with or through one or more computing platforms and whereas many devices even purpose specific devices are actually based upon computing platforms of one type or another it is useful to describe a suitable computing platform its characteristics and its capabilities.

Therefore it is useful to review a generalized architecture of a computing platform which may span the range of implementation from a high end web or enterprise server platform to a personal computer to a portable PDA or wireless phone.

In one embodiment of the invention the functionality including the previously described logical processes are performed in part or wholly by software executed by a computer such as personal computers web servers web browsers or even an appropriately capable portable computing platform such as personal digital assistant PDA web enabled wireless telephone or other type of personal information management PIM device. In alternate embodiments some or all of the functionality of the invention are realized in other logical forms such as circuitry.

Turning to a generalized architecture is presented including a central processing unit CPU which is typically comprised of a microprocessor associated with random access memory RAM and read only memory ROM . Often the CPU is also provided with cache memory and programmable FlashROM . The interface between the microprocessor and the various types of CPU memory is often referred to as a local bus but also may be a more generic or industry standard bus.

Many computing platforms are also provided with one or more storage drives such as hard disk drives HDD floppy disk drives compact disc drives CD CD R CD RW DVD DVD R etc. and proprietary disk and tape drives e.g. Iomega Zip and Jaz Addonics SuperDisk etc. . Additionally some storage drives may be accessible over a computer network.

Many computing platforms are provided with one or more communication interfaces according to the function intended of the computing platform. For example a personal computer is often provided with a high speed serial port RS 232 RS 422 etc. an enhanced parallel port EPP and one or more universal serial bus USB ports. The computing platform may also be provided with a local area network LAN interface such as an Ethernet card and other high speed interfaces such as the High Performance Serial Bus IEEE 1394.

Computing platforms such as wireless telephones and wireless networked PDA s may also be provided with a radio frequency RF interface with antenna as well. In some cases the computing platform may be provided with an infrared data arrangement IrDA interface too.

Computing platforms are often equipped with one or more internal expansion slots such as Industry Standard Architecture ISA Enhanced Industry Standard Architecture EISA Peripheral Component Interconnect PCI or proprietary interface slots for the addition of other hardware such as sound cards memory boards and graphics accelerators.

Additionally many units such as laptop computers and PDA s are provided with one or more external expansion slots allowing the user the ability to easily install and remove hardware expansion devices such as PCMCIA cards SmartMedia cards and various proprietary modules such as removable hard drives CD drives and floppy drives.

Often the storage drives communication interfaces internal expansion slots and external expansion slots are interconnected with the CPU via a standard or industry open bus architecture such as ISA EISA or PCI. In many cases the bus may be of a proprietary design.

A computing platform is usually provided with one or more user input devices such as a keyboard or a keypad and mouse or pointer device and or a touch screen display . In the case of a personal computer a full size keyboard is often provided along with a mouse or pointer device such as a track ball or TrackPoint . In the case of a web enabled wireless telephone a simple keypad may be provided with one or more function specific keys. In the case of a PDA a touch screen is usually provided often with handwriting recognition capabilities.

Additionally a microphone such as the microphone of a web enabled wireless telephone or the microphone of a personal computer is supplied with the computing platform. This microphone may be used for simply reporting audio and voice signals and it may also be used for entering user choices such as voice navigation of web sites or auto dialing telephone numbers using voice recognition capabilities.

Many computing platforms are also equipped with a camera device such as a still digital camera or full motion video digital camera.

One or more user output devices such as a display are also provided with most computing platforms. The display may take many forms including a Cathode Ray Tube CRT a Thin Flat Transistor TFT array or a simple set of light emitting diodes LED or liquid crystal display LCD indicators.

One or more speakers and or annunciators are often associated with computing platforms too. The speakers may be used to reproduce audio and music such as the speaker of a wireless telephone or the speakers of a personal computer. Annunciators may take the form of simple beep emitters or buzzers commonly found on certain devices such as PDAs and PIMs.

These user input and output devices may be directly interconnected to the CPU via a proprietary bus structure and or interfaces or they may be interconnected through one or more industry open buses such as ISA EISA PCI etc. The computing platform is also provided with one or more software and firmware programs to implement the desired functionality of the computing platforms.

Turning to now more detail is given of a generalized organization of software and firmware on this range of computing platforms. One or more operating system OS native application programs may be provided on the computing platform such as word processors spreadsheets contact management utilities address book calendar email client presentation financial and bookkeeping programs.

Additionally one or more portable or device independent programs may be provided which must be interpreted by an OS native platform specific interpreter such as Java scripts and programs.

Often computing platforms are also provided with a form of web browser or micro browser which may also include one or more extensions to the browser such as browser plug ins .

The computing device is often provided with an operating system such as Microsoft Windows UNIX IBM OS 2 IBM AIX open source LINUX Apple s MAC OS or other platform specific operating systems. Smaller devices such as PDA s and wireless telephones may be equipped with other forms of operating systems such as real time operating systems RTOS or Palm Computing s PalmOS .

A set of basic input and output functions BIOS and hardware device drivers are often provided to allow the operating system and programs to interface to and control the specific hardware functions provided with the computing platform.

Additionally one or more embedded firmware programs are commonly provided with many computing platforms which are executed by onboard or embedded microprocessors as part of the peripheral device such as a micro controller or a hard drive a communication processor network interface card or sound or graphics card.

As such and describe in a general sense the various hardware components software and firmware programs of a wide variety of computing platforms including but not limited to personal computers PDAs PIMs web enabled telephones and other appliances such as WebTV units. As such we now turn our attention to disclosure of the present invention relative to the processes and methods preferably implemented as software and firmware on such a computing platform. It will be readily recognized by those skilled in the art that the following methods and processes may be alternatively realized as hardware functions in part or in whole without departing from the spirit and scope of the invention.

In another embodiment of the invention logical processes according to the invention and described herein are encoded on or in one or more computer readable memories. Some computer readable memories are read only e.g. they must be initially programmed using a different device than that which is ultimately used to read the data from the memories some are write only e.g. from the data encoders perspective they can only be encoded but not read simultaneously or read write. Still some other memories are write once read many times.

Some memories are relatively fixed in their mounting mechanisms while others are removable. All computer readable memories form two types of systems when encoded with data and or computer software a when removed from a drive or reading mechanism they are memory devices which generate useful data driven outputs when stimulated with appropriate electromagnetic electronic and or optical signals and b when installed in a drive or reading device they form a data repository system accessible by a computer.

Similarly another form of computer readable memories is a flexible removable floppy disk which is inserted into a drive which houses an access head. The floppy disk typically includes a flexible magnetically encodable disk which is accessible by the drive head through a window in a sliding cover .

A Compact Disk CD is usually a plastic disk which is encoded using an optical and or magneto optical process and then is read using generally an optical process. Some CD s are read only CD ROM and are mass produced prior to distribution and use by reading types of drives. Other CD s are writable e.g. CD RW CD R either once or many time. Digital Versatile Disks DVD are advanced versions of CD s which often include double sided encoding of data and even multiple layer encoding of data. Like a floppy disk a CD or DVD is a removable memories.

Another common type of removable memories are several types of removable circuit based e.g. solid state memory devices such as Compact Flash CF Secure Data SD Sony s MemoryStick Universal Serial Bus USB FlashDrives and Thumbdrives and others. These devices are typically plastic housings which incorporate a digital memory chip such as a battery backed random access chip RAM or a Flash Read Only Memory FlashROM . Available to the external portion of the memories is one or more electronic connectors for engaging a connector such as a CF drive slot or a USB slot. Devices such as a USB FlashDrive are accessed using a serial data methodology where other devices such as the CF are accessed using a parallel methodology. These devices often offer faster access times than disk based memories as well as increased reliability and decreased susceptibility to mechanical shock and vibration. Often they provide less storage capability than comparably priced disk based memories.

Yet another type of computer readable memories device is a memory module often referred to as a SIMM or DIMM. Similar to the CF SD and FlashDrives these modules incorporate one or more memory devices such as Dynamic RAM DRAM mounted on a circuit board having one or more electronic connectors for engaging and interfacing to another circuit such as a Personal Computer motherboard. These types of memory modules are not usually encased in an outer housing as they are intended for installation by trained technicians and are generally protected by a larger outer housing such as a Personal Computer chassis.

In these manners various embodiments of the invention may be realized by encoding software data or both according to the logical processes of the invention into one or more computer readable mediums thereby yielding a product of manufacture and a system which when properly read received or decoded yields useful programming instructions data or both including but not limited to the computer readable memories types described in the foregoing paragraphs.

While certain examples and details of a preferred embodiment have been disclosed it will be recognized by those skilled in the art that variations in implementation such as use of different programming methodologies computing platforms and processing technologies may be adopted without departing from the spirit and scope of the present invention. Therefore the scope of the invention should be determined by the following claims.

