# ENEE447 Lecture 8  

> 2/14/24

### Chapter 5: Concurrency (cont.)  

Last time: Looking at monitors and semaphores  

Drawback of semaphores: Every time we need to use them, we need to make a call to the operating system  

Monitors are OO approach
* makes it easier 
* Less parallelism  
* More overhead  

![alt text](img/Lecture08/image.png)  

In the case of prod-cons, 2 main methods
* Put item in
* Take item out

In the case of the monitor, there will be 2 gray rectangles in the middle part  

Producer code ned not worry whether it can or cannot enter  
* Same thing for consumer  

![alt text](img/Lecture08/image-1.png)  

Application programmer doesn't need to worry about this ^ implementation  

Monitors relieves the programmer from doing this ^   

Monitors allow you to specify new variable type: Condition variable  

![alt text](img/Lecture08/image-2.png)  

These are used for signalling, and we may signal from one to the other  

![alt text](img/Lecture08/image-3.png)  

Will not be asked to analyze/ write with monitors in exam! <sub>only thing i got right on the first exam last semester...</sub>  

![alt text](img/Lecture08/image-4.png)  

Monitor has 2 functions: append and take  

![alt text](img/Lecture08/image-5.png)  

![alt text](img/Lecture08/image-6.png)  

![alt text](img/Lecture08/image-7.png)  

![alt text](img/Lecture08/image-8.png)  

![alt text](img/Lecture08/image-9.png)  

Shared memory model we saw could be made explicit, but it is usually implicit (semas used to ensure synch)  

Message passing means that only the I/O is shared/ connected (explicit)  

Explicit communication: No need to worry about CS  
* Con: All communication needs to go thru OS  
* Each process needs to make packet and sent to OS, leading to overhead  
    * Thus, we don't really send small messages  

Message passing does not restrict us to one system, we can communicate all throughout a network  

![alt text](img/Lecture08/image-10.png)  

Due to having a source and destination, we call this explicit  

Shared memory does not have a destination. Whoever has access can read it  

Blocking send: This process did a send, should it wait until it has been received? 
* If it can continue, its non-blocking
* If not, called blocking  

Blocking receive means we need a message in order to proceed 

Most common protocol: Non-blocking send, blocking receive  

![alt text](img/Lecture08/image-11.png)  

In main, however many slots we have, that many null sends were made, giving us our capacity  

Clue's in the name! If we get a `mayproduce` message, we know we may start producing. Consequently, when we produce, we send a `mayconsume` message to know we may consume  

![alt text](img/Lecture08/image-12.png)  

![alt text](img/Lecture08/image-13.png)   

With locks: 

```
acquire lock
cs
release lock
```  

With Transactional memory:  

```
P1              P2
...             ...
Transaction     Transaction
...             ...
```
Keep log as to when a transaction started, and when it completed  
* Done for each process

Time stack: Log will keep track of transaction start and completion times using timestamps

When a transaction completes, you cannot just keep going. Must commit the  transaction. 

At the tim of commitment, a check will be done using the log etc. to check for any mutex conflicts  

Rolling back occurs whenever there is a conflict, ad we have to go back  
* At every update that is done, the log will keep th previous and new value  

Backing off, then waiting for some random time  

Transactional memory is useful if you think conflicts will not be likely  

TM is an idea from the database community  

OpenMP is more standard for parallel programming  

![alt text](img/Lecture08/image-14.png)  

Enabling/ disabling preemption == disabling interrupts  

Spinlock: Instead of request going into memory, relies on cache coherence and only checking there  
* Avoids creation of traffic  

Yes, it is a busy wait, but does not cause traffic  

![alt text](img/Lecture08/image-15.png)  

![alt text](img/Lecture08/image-16.png)  

![alt text](img/Lecture08/image-17.png)  

This is an important chapter for exam 1!!!  

![alt text](img/Lecture08/image-18.png)  

We will need to know how to analyze the scenarios circled. Given an incorrect solution, we must find the issue, explain it, and give a correct solution and explain why it solves the issue  

### Chapter 9: Uniprocessor scheduling  

Scheduling: 3 levels
* Long term
* Medium term
* Short term

![alt text](img/Lecture08/image-19.png)  

Long-term: Whether to create a new process NOW :zap:

Medium-term: Whether to swap out or in some processes

Short-term: Which process or KLT to run next  
* KLT: Kernel Level Thread  

![alt text](img/Lecture08/image-20.png)  

![alt text](img/Lecture08/image-21.png)  

![alt text](img/Lecture08/image-22.png)  

![alt text](img/Lecture08/image-23.png)  

Scheduler makes the decision, and the dispatcher does th actual switching  

![alt text](img/Lecture08/image-24.png)  

![alt text](img/Lecture08/image-25.png)  

![alt text](img/Lecture08/image-26.png)  

What should a short-term scheduler be looking at?  
* Fairness: Say 5 processes enter system in some order. Whoever came first, goes first, etc. 
    * OR: What % of the CPU time are each process getting? Is one getting more than the others?  
* Throughput: How many processes are finishing in unit time? 
* Priorities: Which process has critical information  
* Context switch time

![alt text](img/Lecture08/image-27.png)  

![alt text](img/Lecture08/image-28.png)  

Batch systems vs. interactive systems vs. real time  

Batch: Mostly compute intensive, CPU-bound processing  
* Usually, no human operator  
* Non-preemptive 

Interactive: Consumer-grade
* Preemptive  

Real-time: Engine control, anti-brake system  
* Hard deadlines, etc.
* May have both, but typically preemptive  

![alt text](img/Lecture08/image-29.png)  

Wednesday: May finish this chapter  