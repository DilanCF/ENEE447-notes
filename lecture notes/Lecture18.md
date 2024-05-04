# ENEE447 Lecture 18  

> 4/1/24

### Chapter 7: Memory Management (cont.)  

Last time: Looking at different types of partitioning:
* Contiguous partitioning  

Talked about different algos for partitioning  

![alt text](img/Lecture18/image.png)  

![alt text](img/Lecture18/image-1.png)  

There are still some kind of contiguous allocation has both internal and external fragmentation  
* Tries to minimize both  

![alt text](img/Lecture18/image-2.png)

In the beginning, the memory is completely free, so we have one block. Any request made will be rounded up to the nearest power of 2 to avoid unnecessary internal fragmentation  
* Make the internal fragmentation less than the total emory used in the allocation  

Once we allocate, we need to split up the rest of the memory into partitions of powers of 2.  

![alt text](img/Lecture18/image-3.png)  

IN this slide, we can see the "buddy" aspect of this algorithm. If we have two 128k nodes, one being occupied and the other free, when they are both free, they will merge into a bigger 256k node  

![alt text](img/Lecture18/image-4.png)  

![alt text](img/Lecture18/image-5.png)  

![alt text](img/Lecture18/image-6.png)  

CS: Code Segment  
DS: Data Segment  
SS: Stack Segment  

Advantage of segmentation, you only need a contiguous section for the smaller segments compared to having a larger one in a linear address space  

![alt text](img/Lecture18/image-7.png)  

![alt text](img/Lecture18/image-8.png)  

![alt text](img/Lecture18/image-9.png)  

![alt text](img/Lecture18/image-10.png)  

![alt text](img/Lecture18/image-11.png)  

![alt text](img/Lecture18/image-12.png)  

![MFW paging](img/misc/Aware.png)  

For user memory, it is standard across general purpose systems to use paging  

```
Virtual space       Physical space
-----               ------
|   |               |    |     
|   |-------------->|    |
|   |               |    |
|   |      |------->|    |
|   |------|        |    |
-----               ------
```  

T<sub>avg</sub> = T<sub>pm</sub> + ***mT<sub>ss</sub>***  

***mT<sub>ss</sub>***: Page fault ratio  

The above sketch is not possible without some intermediary. This is done by way of a page table which can translate how the virtual address indicates to which physical address  
* Page table is handled by the OS  

```
Virtual space       Physical space
-----                   ------
|   |      {    }------>|    |     
|   |----->{    }       |    |
|   |      {    }       |    |
|   |      {    }------>|    |
|   |----->{    }       |    |
-----                   ------
```  

![alt text](img/Lecture18/image-13.png)  

Separate page tables for A,B, etc.  

Reverse page table. For each frame, which processes are here? 

Having a direct page table is an issue since they are huge and you need one for each process

As we see here, the memory is partitioned into different sections of frames. Its up to the OS to determine how to give out frames, how to replace them, etc.  

![alt text](img/Lecture18/image-14.png)  

### Chapter 8: Virtual memory  

![alt text](img/Lecture18/image-15.png)  

Cannot quantify thrashing, but it is apparent when it is happening due to slow application loading times
* OS is running too many processes without enough memory, so there is a high rate of page swapping  

![alt text](img/Lecture18/image-16.png)  

![alt text](img/Lecture18/image-17.png)  

![alt text](img/Lecture18/image-18.png)  

![alt text](img/Lecture18/image-19.png)  

Small page size: 
* Need an even bigger page table
* May not capture all of spatial locality  
* Less time for copying page between SS and PM  
* Less internal fragmentation  

Large page size: Inverse of the above bullets lol  

![alt text](img/Lecture18/image-20.png)  

![alt text](img/Lecture18/image-21.png)  

Pre-paging: OS knows that a process will know x amount of pages. Therefore, will set the pages aside before the process comes in  

Resident set: How many frames given to a certain process  