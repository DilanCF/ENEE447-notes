# ENEE447 Lecture 24  

> 4/22/24

### Chapter 18: Virtual machines  

What are they?  

![alt text](img/Lecture24/image.png)  

Abstraction: Something like Google Maps
* ONly see wht is needed to go from point A to point B

File systems are also an abstraction  
* The user only sees the file getting created, removed, etc.
    * Lower level: Memory addresses are being accessed and modified  

If the memory has several modules, but we only see it as a linear bank of memory, this is considered an abstraction  

Above ^, th cylinder represents the hard disk. The file is being represented on  virtual disk on the right.  

![alt text](img/Lecture24/image-1.png)  

OS provides abstraction AND virtualization  

![alt text](img/Lecture24/image-2.png)  

The Non-V machine in and of itself had a bit of virtualization  

VMM: AKA Hypervisor  
* Providing three different VMs  
* NOw we can run 3 different OSs that can be different  
    * Different from dual booting  
    * Dual booting is more like the img/Lecture24/image on the left, just with a switch at boot time  

In many ways, the VMM takes some role from the OS that is done in the left situation  

We generally don't make any changes to the OSs. Whatever the OS is, it thinks it is interacting directly with the hardware when it really not  
* The difficulty is when, what happens when a process makes a system call?
    * Anytime a process needs help from the OS, it makes a sys call and the OS handles it. 

* When a VM makes a syscall, instead of going to the kernel, the sys call is handled by the VMM  

Portability is the main thing driving our need for virtual machines  

![alt text](img/Lecture24/image-3.png)  

![alt text](img/Lecture24/image-4.png)  

![alt text](img/Lecture24/image-5.png)  

There are mny different ways to do virtualization, some of which shown above  

(a) is the same as the one we just saw 2 slides ago  

For (b), we have the advantage of translating from ISA 2 to OS 1, meaning we can run programs meant for one ISA on a different set via translation  

(d) shows 2 VMMs working together 

![alt text](img/Lecture24/image-6.png)  

![alt text](img/Lecture24/image-7.png)  

![alt text](img/Lecture24/image-8.png)  

![alt text](img/Lecture24/image-9.png)  

Comic sans :mask:  

^ Not a perfect example acc. to professor  

OS supports multiple processes  

![alt text](img/Lecture24/image-10.png)  

![alt text](img/Lecture24/image-11.png)  

"Wine" is similar to JVM  
* Allows Windows programs to run on Linux  

In some sense, because of context switch, every process thinks it has full access to full hardware. Virtualization of the ABI can present different operating systems  


![alt text](img/Lecture24/image-12.png)  

Hosted means the VM is running on some software  

![alt text](img/Lecture24/image-13.png)  

![alt text](img/Lecture24/image-14.png)  

![alt text](img/Lecture24/image-15.png)  

![alt text](img/Lecture24/image-16.png)  

![alt text](img/Lecture24/image-17.png)  

![alt text](img/Lecture24/image-18.png)  

![alt text](img/Lecture24/image-19.png)  

![alt text](img/Lecture24/image-20.png)  

Remember, there is a Hardware layer underneath the VMM layer as well  

