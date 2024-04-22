# ENEE447 Lecture 24  

> 4/22/24

### Chapter 18: Virtual machines  

What are they?  

![alt text](image.png)  

Abstraction: Something like Google Maps
* ONly see wht is needed to go from point A to point B

File systems are also an abstraction  
* The user only sees the file getting created, removed, etc.
    * Lower level: Memory adreses are being accessed and modified  

If the memory has seveeral modules, but we only see it as a linear bank of memory, this is ocnsidered an abstraciton  

Above ^, th cylinder represents the hard disk. The file is being represented on  virtual disk on the right.  

![alt text](image-1.png)  

OS provides abstraciotn AND virtualization  

![alt text](image-2.png)  

The Non-V machine in and of itself had a bit of viftulization  

VMM: AKA Hypervisor  
* Providing three diffeent VMs  
* NOw we can run 3 different OSs that can be different  
    * Different from dual booting  
    * Dual booting is more like the image on the left, just with a switch at boot time  

IN many ways, the VMM takes some rlle from the OS that is done in the left situation  

We gernerla dont make nay changs to the OSs. Whatever the OS is, it thinks it is interacting directl with the hardware when it really not  
* The difficulty is when, what happens when a proces makes a system call?
    * anytim a process needs help from the OS, it makes a sys call and the OS handles it. 

* When a VM makes a syscall, instead of going to the kernel, the sys call is handled by the VMM  

Portablility is the main thing driving our need for virtual machines  

![alt text](image-3.png)  

![alt text](image-4.png)  

![alt text](image-5.png)  

There are mny different ways to do virtualization, some of which shown above  

(a) is the same as the one we just saw 2 slides ago  

For (b), we have the advantage of translating from ISA 2 to OS 1, meaning we can run programs meant for one ISA on a different set via translation  

(d) shows 2 VMMs working togethr 

![alt text](image-6.png)  

![alt text](image-7.png)  

![alt text](image-8.png)  

![alt text](image-9.png)  

Comic sans :vomit:  

^ Not a perfecct example acc. to professor  

OS supports multiple processes  

![alt text](image-10.png)  

![alt text](image-11.png)  

"Wine" is similar to JVM  
* Allows Windows programs to run on Linux  

In some sense, because of context switch, every process thinks it has full access to full hardware. Virtualization of the ABI can present different operating systems  


![alt text](image-12.png)  

Hosted means the VM is running on some software  

![alt text](image-13.png)  

![alt text](image-14.png)  

![alt text](image-15.png)  

![alt text](image-16.png)  

![alt text](image-17.png)  

![alt text](image-18.png)  

![alt text](image-19.png)  

![alt text](image-20.png)  

Remember, there is a Hardware layer underneath the VMM layer as well  

