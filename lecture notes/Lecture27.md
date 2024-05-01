# ENEE447 Lecture 26 

> 4/29/24

### Chapter 15: Security  

Chapters not covered in the first exam will be covered in the midterm a week from today  

Big questions: 
* Deadlock chapter
* Chapter 10b (RTS), 
    * Deadlines
* Memory management (first chapter, chapter 7),  
    * Fixed partition, buddy, paging
* Chapter 8 (Virtual memory) 
    * Different algorithms: Page replacement
        * FIFO, LRU, Clock algorithms, Working set algo  
* Multicore processors (Chapter 10a)  

Traditionally, OSs have not had a big role in security. However, that is changing as times do as well  

Make OS secure, and how can the OS help in making the system secure?  

![alt text](image.png)  

If ou isolate and not connect your system, it is the safest. But then its not very useful for much, is it?  

> The safest ship is the one that never sets sail

No matter what, no system can ever be 100% secure  

If you try to make a system more secure, performance will be impacted  

Ultimately, there must be a trade off  

The more sharing is allowed, the more vulnerable you become  

![alt text](image-1.png)  

I personally disagree with the last bullet. If you don't know how you got in, how can the defender know? Security specialists prepare for attacks by thinking of what an attacker may do  

![alt text](image-2.png)  

![alt text](image-3.png)  

Last bullet is a Linux command. The reason its a problem is because there is a space between the wildcard and the .o, meaning it will remove ALL files, not just the .o files  

![alt text](image-4.png)

![alt text](image-5.png)  

![alt text](image-6.png)  

Many companies try to make chips in other countries. WHen they place an order and tell the company to make a billion chips. Once they have the intelligence, they can copy it and sell it on the black market  

SYstem differentiates UM and KM by a single bit. HW attacks happen by adding a module that, after some time, can flip this crucial bit  

![alt text](image-7.png)  

![alt text](image-8.png)  

![alt text](image-9.png)  

![alt text](image-10.png)  

![alt text](image-11.png)  

![alt text](image-12.png)  

![alt text](image-13.png)  

![alt text](image-14.png)  

![alt text](image-15.png)  

![alt text](image-16.png)  

![alt text](image-17.png)  

![alt text](image-18.png)  

Fun fact: The portion with NO_OP is known as a NO_OP sled. Since there are multiple NO_OPs, the SP will continue to "slide" down until it hits the payload, in this case the modified shell code  

![alt text](image-19.png)  

![alt text](image-20.png)  

![alt text](image-21.png)  

![alt text](image-22.png)  

![alt text](image-23.png)  

![alt text](image-24.png)  

![alt text](image-25.png)  

![alt text](image-26.png)  

![alt text](image-27.png)  

![alt text](image-28.png)  

![alt text](image-29.png)  

![alt text](image-30.png)  

![alt text](image-31.png)  

![alt text](image-32.png)  

![alt text](image-33.png)  

![alt text](image-34.png)  

