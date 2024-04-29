# ENEE447 Lecture 26 

> 4/29/24

### Chapter 18: Virtual machines (cont.)  (cont.)  

3 options for implementing VMs:
1. ISA  
2. ABI  
3. API  

MOstly looking at type 1 implmentaiton
* How do we make it happen?  

![alt text](img/Lecture26/image.png)  

HW modification hlps with all the rest of them  

![alt text](img/Lecture26/image-1.png)  

Not practical since it is inefficient  

Difference between 1a b, in fulll, every abstraction gets emulated (could be using simulator). Trap and emulation most of the absrtascitons are done on the underkying HW

Binary code: Only the executable code is miodified. Not something that needs to be done earlier. Could be doing something else  

Source code modification is not considered pure emulation: Cnanot taek something like Linux and consider it as it comes to you  

![alt text](img/Lecture26/image-2.png)  

Simple scalar simulators in 446, same thing being done here. Will take each instruciton and emulate it's function  

Adv. Can have a different ISA  

![alt text](img/Lecture26/image-3.png)  

Only cetian insturciotns are emulated. The rest are run on hardware  

HArdware runs on Physical Kernel mode OR Physical User Mode  

The application program may do a systme call. In that case, where will it go?  
* Syscall is decoded, and tries to run on HW. But, once we have identified it, we switch modes to physical KM, and try on the other layers. However, the only layer that is also in physical KM is the Hypervisor.  

![alt text](img/Lecture26/image-4.png)  

![alt text](img/Lecture26/image-5.png)  

![alt text](img/Lecture26/image-6.png)  

![alt text](img/Lecture26/image-7.png)

![alt text](img/Lecture26/image-8.png)  

When x86 wa sintorducd, there were already 4 physical modes. Only 0 and 3 were being used. Later on, they implmented more layers  

![alt text](img/Lecture26/image-9.png)  

![alt text](img/Lecture26/image-10.png)  

Sensitive == Privilieged  

![alt text](img/Lecture26/image-11.png)  

Advanage: Not every priviliaged instruciton will be translated. Some other prviliaged ones can be replaced with non privilged, and therefore run on HW, making it faster  

![alt text](img/Lecture26/image-12.png)  

![alt text](img/Lecture26/image-13.png)  

![alt text](img/Lecture26/image-14.png)  

![alt text](img/Lecture26/image-15.png)  

![alt text](img/Lecture26/image-16.png)  

![alt text](img/Lecture26/image-17.png)  

![alt text](img/Lecture26/image-18.png)  

![alt text](img/Lecture26/image-19.png)  

![alt text](img/Lecture26/image-20.png)  

![alt text](img/Lecture26/image-21.png)  

![alt text](img/Lecture26/image-22.png)  

![alt text](img/Lecture26/image-23.png)  

![alt text](img/Lecture26/image-24.png)  

![alt text](img/Lecture26/image-25.png)  

![alt text](img/Lecture26/image-26.png)  

![alt text](img/Lecture26/image-27.png)  

![alt text](img/Lecture26/image-28.png)  

![alt text](img/Lecture26/image-29.png)  

![alt text](img/Lecture26/image-30.png)  

![alt text](img/Lecture26/image-31.png)  

![alt text](img/Lecture26/image-32.png)  

![alt text](img/Lecture26/image-33.png)  

![alt text](img/Lecture26/image-34.png)  

![alt text](img/Lecture26/image-35.png)  

![alt text](img/Lecture26/image-36.png)  

![alt text](img/Lecture26/image-37.png)  

*We skipped over A LOT of slides*  

![alt text](img/Lecture26/image-38.png)  

![alt text](img/Lecture26/image-39.png)  

Analogy: Shipping containers. THese days, lots od shipping is done via these transport ships. We will have a standardized container. The idea is, if we are transporting something hazardous, we may have ot ship them separately. But, sometimes you can ship everything in the same one, store them side by side, on top of each other, etc.  

Try not to run something NOT on a physical machine, but on a virtual container  

Can stop running in one place, and continue running in another  

