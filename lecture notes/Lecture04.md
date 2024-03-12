# ENEE447 Lecture 4  

> 1/31/24

### Chapter 4: Threads (cont.)  

*Notes from another classmate*

![Alt text](img/Lecture04/image.png)  

![Alt text](img/Lecture04/image-1.png)  

![Alt text](img/Lecture04/image-2.png)  

![Alt text](img/Lecture04/image-3.png)  

![Alt text](img/Lecture04/image-4.png)  

![Alt text](img/Lecture04/image-5.png)  

![Alt text](img/Lecture04/image-6.png)  

![Alt text](img/Lecture04/image-7.png)  

![Alt text](img/Lecture04/image-8.png)  

![Alt text](img/Lecture04/image-9.png)  

![Alt text](img/Lecture04/image-10.png)  

![Alt text](img/Lecture04/image-11.png)  

![Alt text](img/Lecture04/image-12.png)  

![Alt text](img/Lecture04/image-13.png)  

![Alt text](img/Lecture04/image-14.png)  

![Alt text](img/Lecture04/image-15.png)  

![Alt text](img/Lecture04/image-16.png)  

![Alt text](img/Lecture04/image-17.png)  

![Alt text](img/Lecture04/image-18.png)  

![Alt text](img/Lecture04/image-19.png)  

![Alt text](img/Lecture04/image-20.png)  

![Alt text](img/Lecture04/image-21.png)  

![Alt text](img/Lecture04/image-22.png)  

![Alt text](img/Lecture04/image-23.png)  

![Alt text](img/Lecture04/image-24.png)  

![Alt text](img/Lecture04/image-25.png)  

![Alt text](img/Lecture04/image-26.png)  

![Alt text](img/Lecture04/image-27.png)  

![Alt text](img/Lecture04/image-28.png)  

![Alt text](img/Lecture04/image-29.png)  

![Alt text](img/Lecture04/image-30.png)  

![Alt text](img/Lecture04/image-31.png)  

![Alt text](img/Lecture04/image-32.png)  

![Alt text](img/Lecture04/image-33.png)  

![Alt text](img/Lecture04/image-34.png)  

![Alt text](img/Lecture04/image-35.png)  

![Alt text](img/Lecture04/image-36.png)  

![Alt text](img/Lecture04/image-37.png)  

![Alt text](img/Lecture04/image-38.png)  

![Alt text](img/Lecture04/image-39.png)  

![Alt text](img/Lecture04/image-40.png)  

![Alt text](img/Lecture04/image-41.png)  

### Chapter 5: Concurrency  

![Alt text](img/Lecture04/image-42.png)  

![Alt text](img/Lecture04/image-43.png)  
Concurrency arises in three different contexts:
* ***Multiple applications***: Multiprogramming was invented to allow processing time to be dynamically shared among a number of active applications.
* ***Structured applications***: As an extension of the principles of modular design and structured programming, some applications can be effectively programmed as a set of concurrent processes.
* ***Operating system structure***: The same structuring advantages apply to systems programs, and we have seen that operating systems are themselves often implemented as a set of processes or threads.


![Alt text](img/Lecture04/image-44.png)  

![Alt text](img/Lecture04/image-45.png)  

![Alt text](img/Lecture04/image-46.png)  

1. ***The sharing of global resources is fraught with peril.*** For example, if two processes both make use of the same global variable and both perform reads and writes on that variable, then the order in which the various reads and writes are executed is critical. An example of this problem is shown in the following subsection.

2. ***It is difficult for the OS to manage the allocation of resources optimally.*** For example, process A may request use of, and be granted control of, a particular I/O channel and then be suspended before using that channel. It may be undesirable for the OS simply to lock the channel and prevent its use by other processes. Indeed, this may lead to a deadlock condition.

3. ***It becomes very difficult to locate a programming error*** because results are typically not deterministic and reproducible 

All of the foregoing difficulties present themselves in a multiprocessor system as well, because here too the relative speed of execution of processes is unpredictable. A multiprocessor system must also deal with problems arising from the simultaneous execution of multiple processes. Fundamentally, however, the problems are the same as those for uniprocessor systems.

![Alt text](img/Lecture04/image-47.png)  

We can classify the ways in which processes interact on the basis of the degree to which they are aware of each other’s existence.
Table lists 3 possible degrees of awareness plus the consequences of each:

* ***Processes unaware of each other***: These are independent processes that are not intended to work together. The best example of this situation is the multiprogramming of multiple independent processes. These can either be batch jobs or interactive sessions or a mixture. Although the processes are not working together, the OS needs to be concerned about competition for resources. For example, two independent applications may both want to access the same disk or file or printer. The OS must regulate these accesses.

* ***Processes indirectly aware of each other***: These are processes that are not necessarily aware of each other by their respective process IDs but that share access to some object, such as an I/O buffer. Such processes exhibit cooperation in sharing the common object.

* ***Processes directly aware of each other***: These are processes that are able to communicate with each other by process ID and that are designed to work jointly on some activity. Again, such processes exhibit cooperation. 

Conditions will not always be as clear-cut as suggested in this Table. Rather, several processes may exhibit aspects of both competition and cooperation. Nevertheless, it is productive to examine each of the 3 items in the preceding list separately and determine their implications for the OS.


![Alt text](img/Lecture04/image-48.png)  

In the case of competing processes three control problems must be faced. First is the need for ***mutual exclusion***. Suppose two or more processes require access to a single non-sharable resource, such as a printer. During the course of execution, each process will be sending commands to the I/O device, receiving status information, sending data, and/or receiving data. We will refer to such a resource as a ***critical resource***, and the portion of the program that uses it as a critical section of the program. It is important that only one program at a time be allowed in its ***critical section***. We cannot simply rely on the OS to understand and enforce this restriction because the detailed requirements may not be obvious. In the case of the printer, for example, we want any individual process to have control of the printer while it prints an entire file. Otherwise, lines from competing processes will be interleaved.

The enforcement of mutual exclusion creates two additional control problems. One is that of ***deadlock***. For example, consider two processes, P1 and P2, and two resources, R1 and R2. Suppose that each process needs access to both resources to perform part of its function. Then it is possible to have the following situation: the OS assigns R1 to P2, and R2 to P1. Each process is waiting for one of the two resources. Neither will release the resource that it already owns until it has acquired the other resource and performed the function requiring both resources. The two processes are deadlocked.

A final control problem is ***starvation***. Suppose that three processes (P1, P2, P3) each require periodic access to resource R. Consider the situation in which P1 is in possession of the resource, and both P2 and P3 are delayed, waiting for that resource. When P1 exits its critical section, either P2 or P3 should be allowed access to R. Assume that the OS grants access to P3 and that P1 again requires access before P3 completes its critical section. If the OS grants access to P1 after P3 has finished, and subsequently alternately grants access to P1 and P3, then P2 may indefinitely be denied access to the resource, even though there is no deadlock situation. 


![Alt text](img/Lecture04/image-49.png)  

In the first 2 cases of process interactions that we have discussed, each process has its own isolated environment that does not include other processes. The interactions among processes are indirect. In both cases, there is a sharing. In the case of competition, they are sharing resources without being aware of the other processes. In the second case, they are sharing values, and although each process is not explicitly aware of the other processes, it is aware of the need to maintain data integrity. When processes cooperate by communication, however, the various processes participate in a common effort that links all of the processes. Because nothing is shared between processes in the act of passing messages, mutual exclusion is not a control requirement for this sort of cooperation. However, the problems of deadlock and starvation are still present. As an example of deadlock, two processes may be blocked, each waiting for a communication from the other. As an example of starvation, consider three processes, P1, P2, and P3, that exhibit the
following behavior. P1 is repeatedly attempting to communicate with either P2 or P3, and P2 and P3 are both attempting to communicate with P1. A sequence could arise in which P1 and P2 exchange information repeatedly, while P3 is blocked waiting for a communication from P1. There is no deadlock, because P1 remains active, but P3 is starved.  
