# ENEE447 Lecture 1  

> 1/24/24

### Syllabus  

Need to buy a Raspberry Pi  

2 exams, non cumulative  

Approx. March 13 and May 8  
* Old Exams available on ELMS <sub>huh, how unlike a certain other professor who also teaches OS...</sub>

### ENEE350 review 

3 major parts:
* Processor management
* Memory management
* I/O management  

After, may cover security, VM, cloud computing, etc.  

1st part is biggest acc. to prof  

![Alt text](img/Lecture01/image.png)  

![Alt text](img/Lecture01/image-1.png)  

Anytime a system has more than one program running, must manage th processes, enable protection, etc.  

Operating systems are as varied as the computer systems that we have all around us  

![Alt text](img/Lecture01/image-2.png)  

Not much time spent on structure  

Modular structures are good in profs opinion  

^ modular, V speed  
* Still good for learning and productivity  

Need to share the resources and protect processes from each other when the time calls for either of them  

Security: Prevent external threats from manipulating our OS  

![Alt text](img/Lecture01/image-3.png)  

Persistence: Related to IO  

![Alt text](img/Lecture01/image-4.png)  

![Alt text](img/Lecture01/image-5.png)  

At the bottom, we have the HW (internal)  

ISA is the interface that allows for SW to manipulate HW  

OS runs in kernel mode w/ higher privileges  

API refers to user programs  
* Sometimes for efficiency, may need to access the OS directly. Use ABI in this case  

If only the OS may interact with the HW, will be very inefficient. This is why we have the bit on the RHS where sometimes the libraries and application programs are using the HW directly  

![Alt text](img/Lecture01/image-6.png)  

![Alt text](img/Lecture01/image-7.png)  

3 is the end-user view  

Virtual machine
* Virtualization at different levels  

![Alt text](img/Lecture01/image-8.png)  

Example of VM  

![Alt text](img/Lecture01/image-9.png)  

IN a system with only one process, short bursts of CPU executions, with long IO waits  
* Very inefficient  
 * This is where we can use multiprogramming to our advantage  

![Alt text](img/Lecture01/image-10.png)  

With this, wait times are getting overlapped, making more use of the processor  

However, due to this, resource management becomes more of a concern (we don't want programs to clobber each others resources)  

![Alt text](img/Lecture01/image-11.png)  

![Alt text](img/Lecture01/image-12.png)  

![Alt text](img/Lecture01/image-13.png)

![Alt text](img/Lecture01/image-14.png)  

We need interrupts in order to stop execution for any reason (IO, checks, etc.)  

![Alt text](img/Lecture01/image-15.png)  

If a program wants to interrupt the system, we make a system call which is trickled down to the HW  

![Alt text](img/Lecture01/image-16.png)  

<sub>deja vu...</sub>  

![Alt text](img/Lecture01/image-17.png)  

The Linux API will list all the system calls it supports
* OS must support all system calls  

![Alt text](img/Lecture01/image-18.png)  

![Alt text](img/Lecture01/image-19.png)  

![Alt text](img/Lecture01/image-20.png)  

Device: IO devices  

![Alt text](img/Lecture01/image-21.png)  

![Alt text](img/Lecture01/image-22.png)  

![Alt text](img/Lecture01/image-23.png)  

![Alt text](img/Lecture01/image-24.png)  

Note that certain system calls are vastly different between OSs. THis is why people usually use APIs
* Differences go beyond name, some implementations are vastly different (i.e fork vs CreateProcess)  

![Alt text](img/Lecture01/image-25.png)  

Doing this will slow us down, so there are concessions between portability and speed  

![Alt text](img/Lecture01/image-26.png)

`read_command` will take the command and the parameters inserted and store them into `command` and `parameters`. This will then allow the child to execute the command with the parameters  

![Alt text](img/Lecture01/image-27.png)  

IO devices are accessible only in kernel mode  
* Accessed by device driver  
    * Driver is processed by the CPU 

DMA: Direct Memory Access  

![Alt text](img/Lecture01/image-28.png)  

CPU and disk controller usually overlap  

![Alt text](img/Lecture01/image-29.png)  

What's the limit? Where should we stop, if at all?  
* We don't want too many processes active at a time  
* Memory wil need to be partitioned  
* Processes may not get sufficient memory  

Medium term scheduler will decide how many active processes to keep in memory 

Long term scheduler will figure out how many resources we have and if we can assign processes  

Short term scheduler will decide which process to run next in this ^ timeline  
* Different ways to implement this  

![Alt text](img/Lecture01/image-30.png)  

![Alt text](img/Lecture01/image-31.png)  

![Alt text](img/Lecture01/image-32.png)  

What if a program is never giving up the CPU? 
* We want the OS to gain control after a certain amount of time
* Before giving control to the process, we have a time for it. As long as it is not doing IO, and it is taking too long, we send a HW interrupt and force it to gain control once again  

![Alt text](img/Lecture01/image-33.png)  

Process manager: OS  
* Int. handler also part of OS  

When P<sub>1</sub> goes to Process manager, we know that we have made a system call  

When P<sub>n</sub> goes to int. handler, we know there was a HW interrupt (keyboard, etc.)  

Every time control comes to kernel mode, scheduler gets to run  

Always looks at the whole picture  

Unless specifically mentioned, we always talk about a single core system  

![Alt text](img/Lecture01/image-34.png)  

Time is being shared among different processes  

We need interrupt-based context switches for these interactive applications  

*Review over, time for the new stuff*  

### Chapter 2: OS Overview  

![Alt text](img/Lecture01/image-35.png)  

Program: Static lines of code sitting somewhere in memory  

Process: Dynamic instance of a program that is currently running  

![Alt text](img/Lecture01/image-36.png)  

![Alt text](img/Lecture01/image-37.png)  

Green is the structure of the Unix OS
* File subsystem: IO  

Both sides may need to talk to each other  

File system is character based system  

![Alt text](img/Lecture01/image-38.png)  

![Alt text](img/Lecture01/image-39.png)  

![Alt text](img/Lecture01/image-40.png)  

![Alt text](img/Lecture01/image-41.png)  

Next time: Chapter 3 and processes  
