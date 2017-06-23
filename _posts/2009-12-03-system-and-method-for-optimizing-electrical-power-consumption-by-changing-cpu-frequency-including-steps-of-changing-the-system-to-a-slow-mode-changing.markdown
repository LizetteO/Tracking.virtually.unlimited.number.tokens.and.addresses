---

title: System and method for optimizing electrical power consumption by changing CPU frequency including steps of changing the system to a slow mode, changing a phase locked loop frequency register and changing the system to a normal mode
abstract: A system and a method for optimizing power in an electronic device are described. The system may be used to implement low power techniques to achieve maximum performance with low battery utilization. A processing load level monitor monitors load(s) on processors. Processor frequencies are updated through the driver until the load is close to 100%, which means that the core frequency is changed to the load processor around 100% at the minimum possible frequency.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08589707&OS=08589707&RS=08589707
owner: STMicroelectronics International N.V.
number: 08589707
owner_city: Amsterdam
owner_country: NL
publication_date: 20091203
---
The present application claims priority of India Provisional Patent Application No. 2772 Del 2008 filed Dec. 5 2008 which is incorporated herein in its entirety by this reference.

The present disclosure relates to optimization of electrical power and more specifically to a device for optimizing consumption of electrical power to procure maximum performance with the same power utilization.

Power management is an essential element for battery operated electronic devices. With the rising performance expectations on multimedia devices it is important to implement low power techniques to have maximum performance with low battery utilization. Even though multiple parallel execution units increase the performance of the processor power is wasted when some of the processing units are idle during various time intervals.

Various techniques have been implemented to optimize power. Since the power consumption of the processor is proportional to the frequency reduction of the frequency of the system clock reduces the power consumption of the microprocessor.

There are some other means to implement this type of power optimization by increasing or decreasing voltage and frequency. But it is done using dedicated hardware which can monitor and change voltage frequency of a single processor at one time. This adds the extra cost of a dedicated hardware chipset which is designed for this purpose. High performance has increased power consumption. What is desired is an embedded application to find the best trade off between energy efficiency and performance by scaling CPU frequency and voltage levels.

A system according to an embodiment of the present invention includes a device for optimizing consumption of electrical power. The system preferably includes a processor block a processing load level monitor coupled to the processor block and an operating frequency and or voltage adjustor coupled to the output of the load level monitor and to the processor block. In a method of the present invention consumption of electrical power is optimized by monitoring processing load levels and adjusting operating frequency and or voltage. Preferably the operating voltage and or frequency is adjusted until the load reaches an optimum level and the frequency is updated based on the system usage level. The instant invention may be operative to manage multiple cores at no extra cost.

The embodiments of the present disclosure will be described in detail with reference to the accompanying drawings. However the present disclosure is not limited to the embodiments and the embodiments described herein in the art of the present disclosure. The disclosure is described with reference to specific circuits block diagrams signals etc. simply to provide a more thorough understanding of the disclosure. The detailed description of the disclosure is as follows 

The present disclosure teaches a system comprising a device for optimizing consumption of electrical power. Said system includes a processor block a processing load level monitor coupled to the processor block and an operating frequency and or voltage adjustor coupled to the output of said load level monitor and the processor block. The processing load level monitor monitors and calculates the load of the processors and the operating frequency and or voltage adjustor updates the voltage and or frequency of said processors till the load is reached to the optimum level said frequency is updated based on the system usage level.

The present disclosure also teaches a method for optimizing consumption of electrical power. The method steps include monitoring processing load level and adjusting operating frequency and or voltage.

The present disclosure further teaches a device for optimizing consumption of electrical power. Said system includes a processor block a processing load level monitor coupled to the processor block and an operating frequency and or voltage adjustor coupled to the output of said load level monitor and the processor block. The processing load level monitor monitors and calculates the load of the processors and the operating frequency and or voltage adjustor updates the voltage and or frequency of said processors till the load reaches an optimum level. Said frequency is updated based on the system usage level.

The present disclosure also teaches a multimedia system comprising a device for optimizing consumption of electrical power. Said multimedia system includes a processor block a processing load level monitor coupled to the processor block and an operating frequency and or voltage adjustor coupled to the output of said load level monitor and the processor block. Processing load level monitor monitors and calculates the load of the processors and the operating frequency and or voltage adjustor updates the voltage and or frequency of said processors till the load is reached at an optimum level and said frequency is updated based on the system usage level.

An application sends a request through the frequency and or voltage adjustor to update the operating frequency and voltage level if required . The processing load level monitor changes the frequency based on the system usage level is not based on the user application e.g. VOIP call video playback etc. and is expandable to any number of processors in the system on chip SoC .

System power consumption in a digital based system is described as Power where C is the capacitance being switched per clock cycle V is voltage and F is the processor frequency cycles per second .

There will be a relative effect in power consumption level with respect to the change in the voltage or frequency.

Frequency reduction brings down the number of instructions a processor can issue in a given amount of time hence performance is reduced. Therefore it is generally used when the workload is low. In contrary performance is increased by raising the processor s frequency beyond the manufacturer s design specifications.

Broadly speaking there are two fundamental methods provided by an Operating System to measure CPU Usage. The facilities provided by Windows CE Windows Mobile for measuring CPU load are described below. Application Programming Interface may vary from one Operating System OS to another but the method will be same.

Thread CPU usage is helpful to measure CPU usage of a particular thread. GetThreadTimes in Windows embedded obtains timing information about a specified thread. Thread CPU usage can be used in the following two ways 

Each OS provides a means to know the CPU idle time. This can be used to calculate the overall CPU Load. Windows Embedded provides GetIdleTime GetTickCount to help measure the CPU idle time during a particular period. For Multimedia processors like Audio Video DSPs firmware support need to be added with custom APIs which will provide the DSP load information on demand. If these types of APIs are not available from OS then similar APIs are needed to be developed by calculating the MIPS Million instructions per second and MCPS Million clocks per second .

The following steps need to be carried out dynamically in order to scale the system from one frequency to other.

Peripheral Clock Status on various use cases are shown in Table 2. Comparison between FULL and IDLE processor is presented. When the system is running at Normal Frequency difference is found in the Microprocessor Core current. Same benefit can be achieved when clocks are gated after scaling to a lower frequency.

Embodiments of the method for optimizing consumption of electrical power are described in and . The methods are illustrated as a collection of blocks in a logical flow graph which represents a sequence of operations that can be implemented in hardware software or a combination thereof. The order in which the process is described is not intended to be construed as a limitation and any number of the described blocks can be combined in any order to implement the process or an alternate process.

Although the disclosure of the instant disclosure has been described in connection with the embodiment of the present disclosure illustrated in the accompanying drawings it is not limited thereto. It will be apparent to those skilled in the art that various substitutions modifications and changes may be made thereto without departing from the scope and spirit of the disclosure.

