---

title: Memory management method, and memory management apparatus
abstract: When a program execution unit of a computer executes a creation instruction of objects utilized by an execution target program in process of executing the execution target program, the program execution unit disposes a created object in an internal heap when a life period of the created object is not contained within life period of objects for root class and gets average value of life time corresponding to set of objects to which the created object belongs with reference to memory allocation information table to dispose the created object as a long-life object in an external heap when the gotten average value of life time is equal to or larger than a predetermined value. Accordingly, life time of objects is measured and long-life objects are not managed by GC, so that program utilizing objects can be executed at high speed.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08504594&OS=08504594&RS=08504594
owner: Hitachi, Ltd.
number: 08504594
owner_city: Tokyo
owner_country: JP
publication_date: 20090219
---
The present application claims priority from Japanese application JP 2008 207412 filed on Aug. 11 2008 the content of which is hereby incorporated by reference into this application.

The present invention relates to technique concerning a memory management method a memory management program and a memory management apparatus.

The garbage collection GC is technique for automatically realizing memory management for a heap area in a memory particularly release of unnecessary memory area being occupied even when specified instruction is not issued from program. The GC is automatically started and accordingly there is proposed a method that influence of load by the GC is suppressed for important control such as real time processing refer to Angelo Corsaro and Ron K. Cytron Efficient memory reference checks for real time java Proceedings of the 2003 ACM SIGPLAN conference on Language compiler and tool for embedded systems 2003 and F. Pizlo J. M. Fox D. Holmes and J. Vitek Real time Java scoped memory design patterns and semantics Proceedings of the Seventh IEEE International Symposium on Object Oriented Real Time Distributed Computing 2004 .

The internal heap is a heap area to be managed by the GC and is realized as Java Registered Trademark heap executed in Java language for example.

The external heap is a heap area not to be managed by the GC and the memory management therefor is realized by specified instruction from program manually .

The mark and sweep GC has the algorithm of marking objects from root object of program in the heap area along links successively sweeping objects which are not marked are floating in the air from the heap area and compacting hashed memory spaces in the heap area into one place.

The copying GC has the algorithm of partitioning memory space into a plurality of sections in which only one section thereof is set as a heap area to be managed by the GC constraining processing of marking objects along links within one section and copying objects connected to one another through links to another section in unit thereof.

As technique concerning securement of memory in Java language there is technique that long life object is secured in external heap so that load is suppressed from being increased due to execution of GC refer to U.S. application Ser. No. 12 038 376 for example . The life time of object means the length of the period from creation of object in memory to its release.

In other words processing load on GC is also increased due to increased objects to be managed by GC. Accordingly long life that is influence on processing load is increased objects are disposed in external heap not to be managed by GC instead of internal heap to be managed by GC so that objects to be managed by GC are suppressed and processing load on GC is also suppressed.

Objects are divided so that short life objects are disposed in internal heap and long life objects are disposed in external heap so that automatic memory management by GC and manual memory management by specified instruction can be balanced.

When the aforementioned method of dividing the heap area in accordance with life time of objects is realized the processing of measuring life time of objects is important and difficult problem.

It is necessary to consider life cycles of objects in order to judge which object lives long actually and advanced knowledge is required. Furthermore whether object lives long is often decided even depending on utilization situation and circumstances of program to be executed.

When a new program is prepared it is very difficult to make programming while which object lives long is previously considered consciously and accordingly it is difficult to prepare the program which can utilize external heap area effectively.

It is often decided depending on utilization situation and circumstances whether object lives long and object which lives long in a certain utilization situation does not necessarily live long even in another utilization situation. Accordingly even if objects are always ensured in external heap area processing load on GC cannot be necessarily suppressed from being increased.

Accordingly it is an object of the present invention to solve the above problems by measuring life time of objects not to manage long life objects by GC so that program utilizing objects can be executed at high speed.

In order to solve the above problems according to the present invention a memory management method in which a heap area in a memory to which objects are allocated is divided into an internal heap to which garbage collection GC is applied and an external heap which is managed by program specifically and an area to which object is allocated is decided on the basis of life time of object is executed by a computer and

the computer comprises an input unit a target set processing unit memory allocation data and a program execution unit in addition to the memory constituting the internal heap and the external heap 

the input unit receiving execution target program set definition data representing sets of objects utilized by the execution target program and analysis program utilizing the sets of objects represented by the set definition data 

executing the analysis program on trial to get life periods from creation time to release time in memory for the sets of objects utilized by the analysis program and calculate life times of objects on the basis of length of the gotten life periods and

storing names of sets of objects and average values of life times of objects for root class designated by the set definition data out of objects constituting the sets of the objects in a corresponding manner to each other as the memory allocation data in storage means 

the program execution unit performing when executing a creation instruction of the objects utilized by the execution target program in process of executing the execution target program the following 

disposing a created object in the internal heap when a life period of the created object is not contained within life period of the objects for root class and

getting average value of life time corresponding to set of objects to which the created object belongs with reference to the memory allocation data disposing the created object as a long life object in the external heap when the gotten average value of life time is equal to or larger than a predetermined value and disposing the created object as a short life object in the internal heap when the gotten average value of life time is smaller than the predetermined value.

According to the present invention life time of objects is measured and objects are not managed by GC properly so that program utilizing objects can be executed at high speed.

Other objects features and advantages of the invention will become apparent from the following description of the embodiments of the invention taken in conjunction with the accompanying drawings.

An external heap application support apparatus memory management apparatus according to an embodiment of the present invention is now described with reference to the accompanying drawings. The external heap application support apparatus selects object having heavy processing load on the basis of life times of objects and allocates the selected object to external heap area not to be managed by GC.

The computer is realized by computer such as personal computer PC and server and includes a memory a central processing unit CPU a storage unit an input unit an output unit and a bus for connecting them to one another.

The memory includes an execution target program a target set processing unit a constrained set processing unit a memory allocation information table memory allocation data a program execution unit a program execution environment unit and set area management API application programming interface in addition to an operating system .

The execution target program is described in object oriented language such as Java language. Object oriented class is described in source code of the execution target program and the class is materialized as object in heap area upon execution.

The execution target program utilizes a target set . The target set includes a constrained set and an unconstrained set for further information refer to .

The target set is an object group having similar life time and is a general term of the constrained set and the unconstrained set .

The constrained set is a capsuled target set and is the target set which satisfies constraints including 5 rules 1st to 5th rules described later.

The unconstrained set is the target set which does not satisfy constraints conversely to the constrained set and is a complementary set of the constrained set belonging to the target set .

The target set processing unit executes the target set mainly unconstrained set but constrained set may be possible on trial and writes its result into the memory allocation information table . In the embodiment set means a set of one or more objects created from class. Objects belonging to the same set have utilization reference relation.

The constrained set processing unit executes the constrained set on trial and writes its result into the memory allocation information table .

The memory allocation information table manages trial execution results such as life periods of sets also named life times of sets for each target set for further information refer to Table 2 .

The program execution unit executes the execution target program . At this time the target set utilized from the execution target program is allocated to heap area. The program execution unit judges whether the target set has long or short life time on the basis of life periods of sets in the memory allocation information table and selects heap area to which the target set is allocated in accordance with its judgment result.

The program execution environment unit is execution environment of the program execution unit realized as Java virtual machine VM for example and is executed on the operating system .

The program execution unit includes a memory allocation unit which includes a root class disposition unit and a member class disposition unit .

The root class disposition unit disposes root class of the target set in the heap area internal heap or external heap . One target set includes one root class. The root class is a class existing in root when utilization relation between classes is viewed as the tree structure.

The member class disposition unit disposes member classes of the target set in the heap area internal heap or external heap . One or more member classes are utilized from one root class. Accordingly one target set includes one or more member classes.

The program execution environment unit includes internal heap processing unit internal heap external heap processing unit external heap GC processing unit object information getting unit and reference information getting unit . The GC processing unit includes copying GC unit and mark and sweep GC unit .

The internal heap processing unit takes charge of memory allocation processing for the internal heap and the external heap processing unit takes charge of memory allocation processing for the external heap .

The internal heap is a heap area for which memory management is executed automatically that is heap area to be managed by GC . The internal heap is realized as Java heap for example.

The external heap is a heap area for which memory management is executed manually that is heap area not to be managed by GC and required to be subjected to memory management from program specifically .

Accordingly the internal heap and the external heap are different in the point as to whether it is managed by GC or not.

When data stored in the internal heap is increased the data is to be managed by GC and accordingly memory management is easy whereas load by processing of GC is increased.

When data stored in the external heap is increased load is not increased so much although memory management is required to be specifically performed manually.

The GC processing unit executes GC to the internal heap . The copying GC unit for executing the copying GC method and the mark and sweep GC unit for executing the mark and sweep GC method are executed according to the algorithm of GC.

The object information getting unit and the reference information getting unit monitor allocation situation of objects of the target set in the internal heap and the external heap and as a result the object information getting unit gets allocation history of objects and the reference information getting unit gets reference relation between objects.

The set area management API is utilized from execution target program and makes securement and release of set area of the target set .

The target set processing unit includes a set definition data for further information refer to Table 3 and a set trial execution unit .

The set trial execution unit includes a set object analysis unit a set analysis unit a set root class table for further information refer to Table 4 a set member class candidate table for further information refer to Table 5 and a set memory allocation information creation unit .

The constrained set processing unit includes constraint set definition data for further information refer to Table 6 a constraint format examination unit and a constraint trial execution unit .

The constraint trial execution unit includes a constraint root class disposition unit a constraint member class disposition unit a constraint utilization information table for further information refer to Table 7 and a constraint memory allocation information creation unit .

The target set is a set of objects in which the reference relation is constructed while defining the object forming root as starting point and the life periods of other objects are contained within the life period of the object forming the root.

The root class RootClass is a class forming root when the reference relation is arranged into a tree structure.

Member classes MemberClass MemberClass and MemberClass are classes except the root class and referred from the root class.

In the unconstrained set interfaces and are added to RootClass and MemberClass respectively so that utilization from external class is permitted.

The reference relation between classes is shown by mark straight line with diamond connecting between classes. Classes having diamond attached thereto are classes of reference sources. For example RootClass refers to MemberClass and MemberClass .

Painted diamond from RootClass represents composition and when object of reference source is eliminated object referred to therefrom is also eliminated.

On the other hand non painted diamond represents aggregation and when object of reference source is eliminated object referred therefrom is not eliminated.

The constrained set is a set of objects satisfying constraint of the target set . The constraint means that object except the constrained set can utilize only root class of the constrained set . Concretely in the constrained set only RootClass provides interface . Object which does not belong to the constrained set cannot utilize member classes which do not provide interface in constrained set .

Member classes cannot be utilized from object except constrained set and accordingly when root class RootClass is eliminated all member classes MemberClass MemberClass and Member Class are also eliminated.

When the rule that utilization can be made by only root class of the constrained set from object except the constrained set is applied to Java language rules are passed when all of the following first to fifth rules are satisfied.

The first rule is that all of classes composing the constrained set must declare in the same package .

The second rule is that only one of root classes of the constrained set must declare as public class in the package declared in the first rule.

The fourth rule is that method interface which declares as public of the root class of the constrained set must not return member class as return value.

The fifth rule is that field of root class and field method and constructor of member classes of the constrained set must not declare as public.

Program defined in accordance with the five rules is the target set . Grounds thereof are now described on the basis of matters derived from the rules.

According to the fifth rule object of member class can be created within root class and member class of the same package.

According to the fourth rule object of member class is not delivered to object except the constrained set and accordingly root class and member class can hold member class. Therefore the life period of member class is contained within the life period of root class.

Program defined in accordance with the five rules is the constrained set since only root class of the constrained set can utilize it from object except the constrained set . Grounds thereof are now described on the basis of matters derived from the rules.

According to the third rule type of member class cannot be utilized from object except the constrained set .

According to the fifth rule field method and constructor of member class cannot be utilized from object except the constrained set .

According to the fifth rule object of member class can be created within root class and member class of the same package.

According to the fourth rule object of member class is not delivered to object except the constrained set .

 RootClass is object of root class of the target set . MemberClass MemberClass and MemberClass are objects of member classes of the target set . OtherClass and OtherClass are objects except the target set . The target set is composed of RootClass MemberClass MemberClass and MemberClass .

Arrows of are followed successively to trace reference. To trace reference is that object referred to directly by object is searched and object referred to by the referred object is searched so that objects are searched recurrently and a target object can be found finally.

For example RootClass of the root class has the creation time of 10 00 and the release time of 10 20 so that the life time is 20 minutes.

When the creation time of a certain class is later than that of the root class and the release time of the certain class is earlier than that of the root class it is expressed that the life period of a certain class is contained within that of the root class. 

For example the life periods of member classes MemberClass MemberClass and MemberClass are contained within the life period of the root class. However the life period of OtherClass is not contained within that of the root class.

When creation and release of a certain class are repeated plural times within the life period of one root class and all of plural life periods of the certain class are contained within the life period of the root class it is defined that there is inclusion relation.

Table 1 shows an example of program describing the target set constrained set . This program is described in accordance with Java grammar.

2nd 10th 16th and 17th lines represent declaration sentences of classes RootClass MemberClass MemberClass and MemberClass .

MemberClass MemberClass and MemberClass are member classes and are package private referable to from only its own package class since modifier is omitted.

5th to 8th lines represent getData method. This getData method is public method of root class and does not return member class as return value.

14th line represents get method. This get method is method of member class and does not declare public.

The second and third rules are satisfied by declaration of modifier of each class or omission thereof.

The fifth rule is satisfied by declarations of field of root class and declarations of field constructor and get method of member class.

Table 2 shows an example of the memory allocation information table . The memory allocation information table manages name of target set root class member class average life time of root class and average area size of target set in a corresponding manner to one another.

The name of target set represents specific information of the target set forming a key of each record. The target set may be the constrained set or the unconstrained set .

The member class represents one or more member classes contained in the target set of the name of target set .

The average life time of root class represents an average life time as a result of execution concerning the root class . The average life time is information for deciding whether the target set of record is allocated to the internal heap or the external heap on the basis of comparison of a predetermined threshold and the average life time.

The average area size of target set represents an average area size allocated as a result of execution concerning the target set of the name of target set . The average area size is used as an initial value of area size ensured in the external heap when the average area size is allocated to the external heap .

Table 3 shows an example of the set definition data . The set definition data is described in accordance with XML grammar nesting structure of element tags .

2nd to 5th lines represent target set element which is a child element of root element. target set name element in 3rd line represents name of the target set and root class element in 4th line represents name of root class of the target set .

6th to 10th lines represent target set element which is a child element of root element in the same manner as 2nd to 5th lines.

Table 4 shows an example of the set root class table . The set root class table manages name of target set root class contained in the target set creation time of root class release time of root class area size of root class and member class candidate table ID in a corresponding manner to one another. The member class candidate table ID stores therein ID for specifying the set member class candidate table Table 5 in which a list of member classes utilized from corresponding root class is stored.

Table 5 shows an example of the set member class candidate table . The set member class candidate table is composed of a plurality of divided tables for each member class candidate table ID of the set root class table Table 4 . The set member class candidate table manages member class candidate creation time thereof release time thereof and area size thereof in a corresponding manner to one another.

Table 6 shows an example of the constraint set definition data . The constraint set definition data has the same format as the set definition data Table 3 . The constraint set definition data includes definition information of the constrained set while the set definition data includes definition information of the target set constrained set or unconstrained set .

2nd to 8th lines represent constrained set element which is a child element of root element. Constrained set name element in 3rd line represents name of the constrained set and root class element of 4th line represents name of root class of the constrained set . Member class elements in 5th to 7th lines represent names of member classes of the constrained set .

9th to 13th lines represent constrained set element which is a child element of root element in the same manner as 2nd to 8th lines.

Table 7 shows an example of the constraint utilization information table . The constraint utilization information table is mainly different from the set root class table Table 4 in that information stored in the constraint utilization information table is limited to the constrained set whereas information stored in the set root class table is about the target set .

The constraint utilization information table manages name of constrained set creation time of root class contained in constrained set release time of root class area size of constrained set and propriety of constrained set in a corresponding manner to one another.

The area size of constrained set represents area size occupied by objects of root class and member class of the constrained set . The propriety of constrained set represents whether the utilization method of the constrained set is valid or not.

Table 8 shows an example of the execution target program utilizing the target set containing constrained set . This program is described in accordance with Java grammar.

7th line represents that allocate method is utilized to allocate target set area containing root class designated by argument and start utilization of target set.

15th line represents that release method is utilized to release target set area designated by argument and end utilization of target set.

Table 9 shows an example of analysis program of the execution target program utilizing the target set unconstrained set . This program is described in accordance with Java grammar.

In 5th line root class of target class is created in internal heap . It is not specified that target set area is ensured and released.

Table 10 shows an example of set area management API . The set area management API is utilized from the execution target program of Table 8 and ensures and releases set area of the target set containing constrained set .

In 1st to 9th lines MemoryAllocator class is declared. The MemoryAllocator class is memory allocator which ensures and releases set area of the target set containing constrained set . Instance of memory allocator is created by newInstance method of 4th line and set area containing root class designated by argument is allocated by allocate method of 6th line. Set area allocated by allocate method is released by release method of 8th line.

In 10th to 14th lines TargetSetArea interface is declared. The targetSetArea interface prescribes set area accessed from MemoryAllocator class. getRoot method declared in 13th line is method of getting object of root class designated as argument upon calling of allocate method of 6th line.

In step S the computer receives the set definition data describing the unconstrained set utilized from the execution target program and the constraint set definition data describing the constrained set utilized from the execution target program through the input unit .

In step S the computer judges from the set definition data and the constraint set definition data received in step S whether the target set to be utilized is the constrained set or the unconstrained set . When the target set is the constrained set described in the constraint set definition data the processing proceeds to step S and when it is the unconstrained set described in the set definition data the processing proceeds to step S.

In step S the computer receives analysis program concerning the execution target program . The target set to be utilized in the analysis program of step S is the same as that in the execution target program inputted in step S. The analysis program is described without being aware of the target set to be utilized. On the other hand description representing the result of trial execution in step S described later of the analysis program is added to the execution target program and description to the effect that the set area of the target set is ensured and released by the set area management API is added thereto.

In step S the set trial execution unit executes the analysis program on trial and registers its result in the memory allocation information table . Accordingly the set trial execution unit executes processing shown in a flow chart of . In the processing of et seq. the set trial execution unit specifies whether the target set containing root class designated by the set definition data inputted in step S exists in the analysis program inputted in step S or not.

In step S the computer receives the execution target program utilizing the unconstrained set . The execution target program is a program in which specified memory management of the unconstrained set by the set area management API is added to the analysis program.

Creation of root class of the analysis program 5th line of Table 9 is changed to allocation allocate in 7th line of Table 8 of target set area of the unconstrained set specified from trial execution result described later in step S of of the analysis program and getting of root class getRoot in 5th line of Table 8 .

Clearing of reference to root class 13rd line of Table 8 and release of allocated target set area release in 15th line of Table 8 are added next to any operation of the unconstrained set 7th line of Table 9 .

In step S the constraint format examination unit formally examines whether the target set to be utilized by the execution target program inputted in step S is the constrained set or not as represented by the constraint set definition data inputted in step S. Accordingly the constraint format examination unit executes processing shown by the flow chart of .

In step S the constraint trial execution unit executes the execution target program passing the formal examination in step S on trial and registers its result in the memory allocation information table . Therefore the constraint trial execution unit executes processing shown by the flow chart of .

In step S the program execution unit executes operates the execution target program in accordance with the contents of the memory allocation information table registered in step S or S. Accordingly the program execution unit executes processing shown by the flow chart of . At this time the memory allocation unit of the program execution unit reads the life period life time of the target set constrained set and unconstrained set utilized from the execution target program from the memory allocation information table to compare it with predetermined threshold so that the memory allocation unit judges whether the target set has long or short life. When it has long life the target set area is allocated to the external heap and the target set is disposed in the target set area whereas when it has short life the target set is disposed in the internal heap .

In the processing of the objects having heavy processing load out of the objects described below can be evacuated into the external heap to thereby suppress reduction in processing performance of the computer .

In the processing of the set definition data and the constraint set definition data are received in step S and processing is branched on the basis of the set to be utilized in step S so that the single computer is adapted to select two kinds of target sets unconstrained set and constrained set to be handled. On the other hand the single computer may be structured to handle one kind of target set exclusively. In this case input step S of the constraint set definition data and branch thereof step S can be omitted.

In step S memory allocation information registered in steps S and S is gotten from the memory allocation information table .

In step S the execution target program is started to be executed in the program execution environment unit .

In step S when allocate method is executed by the execution target program being executed the processing proceeds to step S.

In step the target set area is allocated and root class is created in the target set area. That is processing of is called up using as argument the name of root class delivered by argument of allocate method. In the processing of the program execution unit instructs the root class disposition unit to create root class. When the root class disposition unit receives the instruction the root class disposition unit allocates the target set area to the external heap when the target set has long life and creates root class in the target set area. When the target set has short life the root class disposition unit creates root class in the internal heap .

In step S when release method of the execution target program is executed the processing proceeds to step S.

In step S the target set area allocated by allocate method is released. That is processing of is called up using as argument the target set area delivered by argument of release method and allocated in step S. The program execution unit instructs the root class disposition unit to release the target set area in . The root class disposition unit releases the target set area allocated to the external heap in response to the instruction.

In step S when object in New area of the internal heap becomes object to be moved to Old area by processing of copying GC unit of the program execution environment unit the processing proceeds to step S.

In step S the object of member class to be moved in step S is moved to target set area allocated to the external heap in step S. That is processing of is called up using the object to be moved as argument. The program execution unit instructs the member class disposition unit to move the object of member class to the target set area allocated to the external heap when the target set has long life.

In step S it is judged whether the name of root class delivered as argument is registered in root class column of the memory allocation information table gotten in step S or not. When it is registered Yes of step S processing subsequent to step S is executed using record of the memory allocation information table as registration record.

In step S it is judged whether the average life time of registration record is equal to or longer than the gotten execution interval of Mark and Sweep GC or not. When the judgment of step S is satisfied the processing proceeds to step S.

In step S the target set area is allocated in the external heap by means of the external heap processing unit in accordance with average area size of target set of registration record and root class delivered by argument is created in the target set area.

In step S when judgment in steps S or S is No the internal heap processing unit is used to create root class delivered by argument in the internal heap .

In step S it is judged whether the target set delivered by argument is allocated to the external heap or not allocated to the internal heap . When judgment in step S is No the target set allocated to the internal heap is released by the GC processing unit in accordance with the algorithm of GC. When judgment in step S is satisfied the processing proceeds to step S.

In step S the external heap processing unit is used to release the target set area in which the target set delivered by argument is disposed from the external heap .

In step S whether reference from object of root class disposed in external heap by allocate method to object to be moved delivered by argument is traced is inquired to the copying GC unit . When judgment in step S is satisfied the processing proceeds to step S.

In step S it is judged whether object to be moved delivered by argument is object of member class of target set containing root class of step S or not. When judgment in step S is satisfied the processing proceeds to step S.

In step S the object to be moved delivered by argument is moved to target set area in the external heap in which object of root class of step S is stored.

In step S the set object analysis unit executes analysis program of step S in the program execution environment unit on trial.

In step S the set object analysis unit gets reference relation of all objects utilized in the analysis program executed on trial through reference information getting unit and gets allocation history of all objects utilized through object information getting unit .

In step S the set analysis unit analyzes the target set on the basis of analysis result of objects by the set object analysis unit . Accordingly a subroutine shown in is called up.

In step S the set memory allocation information creation unit creates memory allocation information of the target set on the basis of analysis result of the target set by the set analysis unit and registers the memory allocation information in memory allocation information table . Accordingly a subroutine shown in is called up.

In step S the set trial execution unit supplies target set root class and member class registered in the memory allocation information table from creation result of memory allocation information by the set memory allocation information creation unit to the user.

In steps S to S the set analysis unit executes loop processing for selecting root class element in target set elements with reference to set definition data inputted in step S.

In step S allocation history of all objects created from root class defined by root class element selected by loop processing is selected RootClass in from allocation history of object gotten in step S and the selected information is stored in column concerning root class of set root class table .

In step S candidate of member class of the target set for objects selected in loop processing starting from step S is analyzed. Accordingly subroutine shown in is called up.

In step S the set analysis unit gets all objects referred to by objects of root class selected in loop processing of steps S to S from reference relation of objects gotten in step S. The set analysis unit gets not only objects referred directly to by objects of root class but also all objects traced from objects of root class. In example shown in the set analysis unit gets MemberClass MemberClass MemberClass and OtherClass from reference information getting unit .

In step S allocation history of object being selected in loop processing of steps S to S is gotten from allocation history of objects gotten in step S.

In step S it is judged whether the life period represented by creation time and release time of the gotten allocation history is contained within the life period represented by creation time and release time of root class selected in loop processing of steps S to S or not. When judgment of step S is satisfied the processing proceeds to step S.

In step S allocation history of object being selected in loop processing of steps S to S is stored in column of member class candidate of the set member class candidate table .

For example allocation history of MemberClass MemberClass and MemberClass contained Yes of step S in life period of RootClass of is stored in set member class candidate table ID 1 as candidate of member class.

On the other hand allocation history of OtherClass which is not contained No of S within the life time of RootClass of is not stored in set member class candidate table .

Furthermore OtherClass is stored in another set member class candidate table e.g. ID 2 when root class except RootClass of is selected in steps S to S and OtherClass is contained within the life period of at least one root class out of the selected root class.

In steps S to loop processing for selecting root classes of the set root class table prepared in analysis processing step S of target set by the set analysis unit one by one and preparing record added to the memory allocation information table for each selected root class is executed.

In step S target set to which selected root class belongs is registered in column of target set for added record.

In step S column of member class for added record is prepared with reference to set member class candidate table . Concretely processing of the following items 1 to 3 is executed.

In step S column of average life time of root class for added record is prepared. Concretely difference between creation time of member class candidate and release time of member class candidate corresponding thereto for each set contained in record searched in item 1 of step S is calculated as life time for each set to calculate an average value thereof as an average life time of selected root class.

In step S column of average area size of target set for added record is prepared. That is average area size of area size of target set is calculated from size of selected root class and size of extracted member class. Concretely size of root class of target set is read out from column of area size of root class of set root class table and size of member class of target set is read out from column of area size of member class candidate of set member class candidate table for each target set and both of them are added to thereby calculate the area size of target set. An average value of the area sizes of target sets calculated for each target set is calculated.

In step S column elements for added records prepared in steps S to S are written in the memory allocation information table .

In steps S to S loop processing for selecting set to be examined from the read sets one by one and examining the set is executed.

In step S subroutine for designating root class of the set to be examined as root class to be examined and verifying the root class is called up.

In step S it is judged that verification result of root class in step S is valid or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In steps S to S loop processing for selecting member class of set to be examined from the constraint set definition data one by one and verifying the member class is executed.

In step S the selected member class is designated as member class to be examined and subroutine for verifying the member class is called up.

In step S it is judged whether the verification result of member class of step S is valid or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In step S when all of verification results of root class are valid Yes of step S and all of verification results of member class are valid Yes of step S for all sets to be examined the constraint set definition data to be examined is set to valid and the processing is ended.

In step S when at least one of verification results of root class and verification results of member class is invalid No of steps S and S for one or more sets of sets to be examined the constraint set definition data to be examined is set to invalid and the processing is ended.

The set to be examined judged to be all valid in judgment of step S or S is the constrained set . On the other hand the set to be examined judged to be invalid even once in judgment of step S or S is the unconstrained set or the set except target set .

In step S the constraint format examination unit judges whether program of the root class to be examined defined in constraint set definition data exists in the execution target program inputted in step S or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In step S it is judged whether the program of root class to be examined which exists in the execution target program inputted in step S is public class or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In step S it is judged whether the program of root class to be examined contains public field or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In steps S to S loop processing for selecting public methods of the program of root class to be examined successively one by one is executed. After this loop processing is ended the processing proceeds to step S.

In step S it is judged whether return value of the selected public method is class of the same package as root class to be examined or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

As an example contrary to the fourth rule of the constrained set when the return value of the selected public method is package different from the root class No of step S and super class of member class and the public method returns the member class as return value it is contrary to the fourth rule although it may be judged to be valid as exceptional processing. The propriety contrary to the fourth rule in this case is verified by the constraint root class disposition unit described in step S of later of the constraint trial execution unit when Java program utilizing the constrained set in step S is executed on trial.

In step S the constraint format examination unit judges whether the program of member class to be examined defined in the constraint set definition data exists in the execution target program inputted in step S or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In step S it is judged whether the program of member class to be examined which exists in the execution target program inputted in step S is contained in the same package as root class or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In step S it is judged whether public field exists in the program of member class to be examined or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In steps S to S loop processing for selecting methods and constructors of the program of member class to be examined one by one is executed. After the loop processing is executed the processing proceeds to step S.

In step S it is judged whether the selected method or constructor is public declared or not. When the judgment of step S is satisfied the processing proceeds to step S.

In step S the constraint trial execution unit reads the constraint set definition data inputted in step S.

In step S the constraint trial execution unit executes the execution target program utilizing the constrained set in the program execution environment unit . Data of the trial execution result is stored in the constraint utilization information table . The trial execution processing of step S is similar to operation processing of the program execution unit . Different points between the trial execution processing and the operation processing are as follows.

In step S the constraint memory allocation information creation unit creates memory allocation information from trial execution result of step S stored in constraint utilization information table and registers the memory allocation information in the memory allocation information table . Accordingly subroutine shown in is called up.

In step S the constraint root class disposition unit judges whether the constrained set containing root class delivered by argument of allocate method is defined in the constraint set definition data or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In step S the user is warned to the effect that the constrained set is not defined and the processing is interrupted.

In step S the external heap processing unit is used to create set area in the external heap and root class delivered by argument of allocate method is created in the set area.

In step S record is added in the constraint utilization information table and creation time of root class is registered.

In step S the external heap processing unit is used to release set area in the external heap . The set area is released to thereby release root class in the set area together as well.

In step S area size of the set area upon release in step S is gotten from external heap processing unit and is registered in the constraint utilization information table as area size of the constrained set. Root class and member class of the constrained set are disposed in the set area of the external heap during execution of execution target program utilizing the constrained set . In the disposition of root class and member class when there is no space in the set area the external heap processing unit automatically extends the set area. Accordingly the area size of the set area upon release is the same as that occupied by root class and member class of the constrained set.

In step S whether there is reference from object disposed in internal heap to root class and member class of constrained set disposed in external heap upon release of set area in external heap or not is inquired to the external heap processing unit . The processing is branched in accordance with the inquiry result. When judgment of step S is satisfied there is reference the processing proceeds to step S and when it is not satisfied no reference the processing proceeds to step S.

Concrete examples of judging whether there is reference to each class or not in step S are now described.

When reference to root class of constrained set is not cleared as a result that sentence this. root null of the execution target program is not executed there exists reference from object disposed in internal heap to root class disposed in external heap .

In the exceptional processing concerning the fourth rule described in when return value of public method of root class is package different from the root class and super class of member class and the public method returns the member class as return value there exists reference from object disposed in internal heap to member class disposed in external heap .

In step S the column of propriety of constrained set in constraint utilization information table is updated to valid .

In step S the column of propriety of constrained set in constraint utilization information table is updated to invalid .

In steps S to S loop processing for selecting one or more records for each of name of constrained set of the constraint utilization information table is executed. Record added in memory allocation information table is prepared by one record for each loop.

In one loop processing when one record is selected from constraint utilization information table name of constraint set of the record exists in the constraint utilization information table solely.

In one loop processing when a plurality of records are selected from constraint utilization information table names of constrained set of the plurality of selected records are identical.

In step S it is judged whether all contents in column of propriety of constrained set of selected record are valid or not. When judgment of step S is satisfied the processing proceeds to step S and when it is not satisfied the processing proceeds to step S.

In step S whether memory allocation information of the constrained set being processed in the current loop is created or not is inquired to the user. When judgment of step S is satisfied the processing proceeds to step S.

In step S name of constrained set selected in this current loop is registered in column of target set for added record.

In step S columns of root class and member class for added record are created. Accordingly constrained set name element of constraint set definition data refer to Table 6 coincident with name of constrained set of constraint utilization information table being processed in this current loop is searched for e.g. 3rd and 10th lines .

Root class element e.g. 4th and 11th lines in searched element is registered in column of root class for added record.

Member class element e.g. 5th to 7th lines and 12th line in searched element is registered in column of member class for added record.

In step S column of average life time of root class for added record is created. Concretely difference in time between creation time of root class and release time of root class corresponding thereto contained in selected record of the constraint utilization information table is calculated to thereby calculate the life time for one record. When a plurality of records are selected in one loop processing because of the same constraint set name life times for the plurality of records are calculated and an average value of the life times is set as average life time of root class .

In step S column of average area size of target set for added record is created. Concretely an average value of area size of constrained set contained in selected record of the constraint utilization information table is set as average life time of root class .

In step S column elements for added records created in steps S to S are written in the memory allocation information table .

As described above according to the embodiment with regard to memory allocation destination of the target set utilized by the execution target program the heap area is divided into the internal heap and the external heap on the basis of life time of objects constituting the target set .

Consequently the objects having short life time are often subjected to creation processing and release processing although since the objects having short life time is allocated to the internal heap the memory management therefor is performed automatically by GC. Accordingly time and labor for memory management can be reduced by GC efficiently.

On the other hand since the objects having long life time are allocated to the external heap the objects are not managed by GC and processing load on GC can be reduced. Moreover the frequency of subjecting the objects having long life time to creation processing and release processing is reduced and accordingly even if memory management is performed by execution target program specifically time and labor for memory management are not required so much.

Accordingly the memory management method of the embodiment can utilize advantages of the internal and external heaps and in a well balanced manner.

It should be further understood by those skilled in the art that although the foregoing description has been made on embodiments of the invention the invention is not limited thereto and various changes and modifications may be made without departing from the spirit of the invention and the scope of the appended claims.

