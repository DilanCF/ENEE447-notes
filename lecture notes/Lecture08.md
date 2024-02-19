# ENEE447 Lecture 4  

> 2/14/24

### Chapter 5: Concurrency (cont.)  

Last time: Looking at monitros and semapohores  

Drawbak of semaphores: Everytime we need to use them, we need to make a call to the operating system  

Monitors are OO approach
* makes it easier 
* Less parallelism  
* More overhead  

![alt text](image.png)  

In the caee of prod-cons, 2 main methods
* Put item in
* Take item out

In the case of the monitor, there will be 2 gray rectangles in the middle part  

Producer code ned not worrry whether it can or cannot enter  
* Same thing for consumer  

![alt text](image-1.png)  

Application programmer doesnt need to worry about this ^ implementation  

Monitors releives the programmer from doing this ^   

MOnitor allow youto specify new variable type: Condition variable  

![alt text](image-2.png)  

These are used for signalling, and we may signal from one to the other  

![alt text](image-3.png)  

Will not be asked to analyze/ write with monitors in exam! <sub>only thing i got right on the first exam last time...</sub>  

![alt text](image-4.png)  

Monitor has 2 functions: append and take  

![alt text](image-5.png)  

![alt text](image-6.png)  

![alt text](image-7.png)  

![alt text](image-8.png)  

***Edit image names!!!***
![alt text](image-10.png)  

Shared memory model we saw could be made explicit, but it is usually implicit (semas used to ensure synch)  

Message passing means that only the I/O is shared/ connected (explicit)  

Explicit communication: No need to worry about CS  
* Con: All communication needs to go thru OS  
* Each process needs to make packet and sent to OS, leading to overhead  
    * Thus, we dont really send small messages  

Message passing does not restrict us to one system, we can communicate all thruought a network  

![alt text](image-11.png)  

Due to having a source and destination, we call this explicit  

Shared memory does not have a destination. Whoever has caccess can read it  

Blocking send: This process did a send, should it wait until it has been recieved? 
* If it can continue, its nonblocking
* If not, called blocking  

Blocking recieve means we need a message in order to proceed 

Most common protocol: Nonblocking send, blocking recieve  

![alt text](image-12.png)  

In main, howevr many slots we have, that many null sends were made, giving us our capacity  

Clue's in the name! If we get a "mayproduce" message, we know we may start producing. Consequently, when we produce, we send a "mayconsume" mesage to know we may consume  

![alt text](image-13.png)  

![alt text](image-14.png)   

with locks: 

```
acquire lock
cs
release lock
```  

with Transacitonal memory:  

```
P1              P2
...             ...
Transaction     Transaction
...             ...
```
Keep log as to when a transaciton started, and when it completed  
* Done for each process

Time stack: Log will keep track of transaction start and completion times using timestamps

When a transaction completes, you cannot just keep going. Must commit the  transactoin. 

At the tim of commitment, a check will be done using the log etc. to check for any mutex conflicts  

Rolling back occurs whenever there is a conflict, ad we have to go back  
* At every update that is done, the log will keep th previous and new value  

Backing off, then waiting for some random time  

Transacitonal memory is useful if you think conflicts will not be likely ???  

TM is an idea from the database community  

OpenMP is more standard for parallel programming  

