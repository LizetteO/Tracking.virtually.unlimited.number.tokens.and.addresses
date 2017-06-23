---

title: Controlling resource consumption
abstract: A method of controlling resource consumption of running processes, sub processes and/or threads (such as a database or an application transaction) in a computerized system, in which resources consumed by less important processes are freed by periodically suspending (by causing them to demand less resources) and resuming these processes transparently to other entities of the computerized system and externally to the OS without intervention in its inherent resource allocation mechanism and allowing the OS of the computerized system to allocate the free resources to other running processes.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=09582337&OS=09582337&RS=09582337
owner: Pivotal Software, Inc.
number: 09582337
owner_city: San Francisco
owner_country: US
publication_date: 20090518
---
This application is a continuation of United States Patent Application Serial No. PCT IL2007 01621 filed Dec. 27 2007 pending which application claims priority to U.S. Patent Application Ser. No. 60 871 994 filed Dec. 27 2006 both of which applications are herein incorporated by reference in their entirety.

The present invention is related to computer resources management. More particularly the invention is related to a method for providing prioritizing to important processes by controlling respective resource consumption of processes and transactions such as processes of the operating system application processes database transactions network activity I O requests and for allocating more resources to one or more processes at the expense of the others.

In any given computerized system a set of processes transactions compete for resources. For example processes that are related to the Central Processing Unit CPU Input Output I O devices the communication the computer and the user or another information processing system network resources or any other shared computer resource. A heavy process which requires many resources causes the other processes to slow down or stop e.g. not to respond due to lack of available resources. Such processes transactions may include 

All the conventional systems described above have not yet provided satisfactory solutions to the problem of dynamically prioritizing important processes executed by a computerized system and for allocating more resources to such processes.

It is therefore an object of the present invention to dynamically prioritize important processes executed by a computerized system and for allocating more resources to such processes at the expense of the others.

It is another object of the present invention to improve performance and to maintain a normal level of performance and response time to users while heavy transactions are running in the background.

It is a further object of the present invention to improve performance and to free resources for important users actions.

It is still another object of the present invention to improve performance and to improve protection and stability of applications against heavy transactions operations that may cause a Denial of Service DoS .

It is yet another object of the present invention to more effectively handle peak demands and for reducing the peak stress from the computerized system.

It is a further object of the present invention to improve performance and maintain a desired Quality of Service QoS for one or more transactions.

The present invention is directed to a method of controlling resource consumption of running processes sub processes and or threads such as a database or an application transaction in a computerized system. Accordingly resources consumed by less important processes are freed by periodically suspending by causing them to demand less resources and resuming these processes transparently to other entities of the computerized system and externally to the OS without intervention in its inherent resource allocation mechanism and allowing the OS of the computerized system to allocate the free resources to other running processes.

The amount of resources consumed by a running process is preferably controlled by repeatedly limiting its demand for system resources for a first period during which no demand is presented and a second period during which the preceding demand is resumed until the process is finished. In order to control the system resources given to a process allocation of execution time units is used instead of allocating CPU and or I O cycles.

Preferably processes are accelerated by slowing down other processes. Running processes may be accelerated or slowed down by using a GUI e.g. a sliding virtual throttle for controlling the resources allocated to them. Suspending running processes may be carried out through an inherent API a debugger or directly through the OS system calls. or by using a binary code or any other representation of a command for suspending and resuming processes.

The amount of consumed resources may be controlled for a process that is already running and consuming resources. Preferably the amount of resources consumed by an application is controlled by a set of rules which can be determined externally to this application.

The present invention is also directed to computerized system in which resource consumption of running processes sub processes and or threads are controlled by freeing resources consumed by one or more processes by periodically suspending and resuming said one or more processes and allowing said computerized system to allocate the free resources to other running processes.

The present invention is directed to a method of controlling computerized resources based on allocating chunks of execution time in order to control the system resources given to a process. Generally the method is based on stopping and resuming the transactions and processes on the fly in real time and by limiting the consumption of computer resources to some processes while allocating more resources to other transactions in the system without requiring a priority level to be determined on launching the processes.

Resource control is based on the following steps of identifying and controlling transaction process within a given environment 

In order to control the resource consumptions of a given process transaction the system is monitored by any conventional existing method. For example in an Oracle database an internal database views and delivers various factors and statistics regarding transaction such as username connected terminal transaction content amount of resources used etc. . Internal commands or even third party tools can be used for example in order to collect statistics about running processes transactions and target those that need their resources to be controlled.

The next step is to cross the statistics collected in the previous step 1 to a set of Rules. A rule is defined as a set of thresholds for each gathered statistic factor. For example if a transaction is currently active doing more than 1000 physical reads per second scanning table X or is running during the peak hours 10 00 am 4 00 pm its resource consumption is reduced to 20 . According to another example if a process is executed by the manager of an enterprise it has been running for 5 minutes and has not been completed yet while other processes were also executed by the employees then the resource consumption of the other processes of the employees is reduced to 20 . According to another example if a process is an Anti Virus that is working while Office tools are running then its resource consumption is reduced to 5 .

In this step the transaction resource consumptions is controlled by allocating chunks of execution times. The method of allocating chunks of execution according to embodiments of the present invention is based on suspending and resuming the processes which can be done in several ways in a computerized system.

Generally resource control is based on identifying the exact process thread at the operating system level that is running and managing the transaction. Then the process thread is suspended and resumed in a frequency that is defined by the rule causing the effect of slowing it down and controlling the amount of resource it uses. The following examples illustrate how to use the method proposed by the present invention in different environments.

In this example the process thread in the Operating System that performs the transaction is identified and suspended it for 4 seconds using ORADEBUG SUSPEND command through SQLPLUS utility . Then it is resumed for 1 second using ORADEBUG RESUME command. The Suspend Resume operations are repeated until the transaction is completed. The advantage in database applications is that according the proposed method a transaction is first identified in the database and then in the operating system. Then the resources allocated to this transaction are managed in the OS. The result is that the load in the database is affected without managing the database.

In this example the process thread in the Operating System that performs the transaction is identified and suspended it for 4 seconds using KILL STOP command in the shell environment . Then it is resumed for 1 second using KILL CONT command. The STOP CONT operations are repeated until the transaction is completed. Alternatively this may be done by using directly the signal code number. For example KILL 23 KILL 25 command in Solaris OS of Sun Microsystems or KILL 17 KILL 19 command in Free BSD free and open source operating system that is based on the Berkeley Software Distribution BSD version of the Unix operating system or some Linuxes.

The KILL command is used at the Shell the interactive user interface with UNIX operating system level. Alternatively the system calls of a specific OS can be used directly. For example in Unix Linux OS the commands KILL pid SIGSTOP KILL pid SIGCONT can be used.

In this example there is an interfacing stage with processes in the Operating System to get their handles as well as with threads of a specific process to get its handles. Then the thread is suspended for 4 seconds using THREAD.SUSPEND command in .NET for example . Then it is resumed for 1 second using THREAD.RESUME command in .NET . The Suspend Resume operations are repeated until the transaction is completed.

In this example the storage device is connected and the corresponding I O stream is identified. Then the I O stream is suspended for 4 seconds and then it is resumed for 1 second. The Suspend Resume operations are repeated until the I O stream finishes.

In this example the corresponding stream of IP packets is identified. Then the IP packets delivery is suspended for 4 seconds and then it is resumed for 1 second. The Suspend Resume operations are repeated until the transaction finishes.

When a transaction has started the Define Rule window shown in can be used for slowing down the system by sliding the virtual throttle slider to the left in order to prevent the selected transaction from dominating the available resources. Suitable rules may be created for type of transaction.

The above examples and description have of course been provided only for the purpose of illustration and are not intended to limit the invention in any way. As will be appreciated by the skilled person the invention can be carried out in a great variety of ways employing more than one technique from those described above all without exceeding the scope of the invention.

