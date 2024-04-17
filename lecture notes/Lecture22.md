# ENEE447 Lecture 22  

> 4/15/24

### Chapter 11: IO Management (cont.)  

Mainly dealing with higher level aspects of cheduling  

![alt text](img/Lecture22/image.png)  

High level formatting and low level formatting  

There is a posiblilty for bad blocks during formatting  
* If one is found, it is not considered for storage  

![alt text](img/Lecture22/image-1.png)  

Non-volatile Mmeory Devices have characteritics that present challenges  

R/W in page increments but cant overwrite in place  

Lifespan is measures in drive writes per day  

*From here, vendor-specific approaches*  

![alt text](img/Lecture22/image-2.png)  

![alt text](img/Lecture22/image-3.png)  

![alt text](img/Lecture22/image-4.png)  

![alt text](img/Lecture22/image-5.png)  

### Chapter 12: File System  

*No slides :(*  

MOst of the management of the file system is under the contorol of the end user  
* Create new files, directroeis, etc.  

File Concept:  
* Contiguous logical address space
* Types
    * Data
        * Numeric
        * Character
        * Binary

Named, ordered collection of informaion  

File manager (OS) manages this data by storing it on a device, then mapping th block toragae to a logical view  

Allocating and deallocating storage  

Providing file directories  

File tructure

* None: Sequence of bytes
* Simple record structure
    * Lines
    * Fixed/ Variable length
* Complex structres
    * Formatted document
    * Relocatable load file

File attributes
* Name
* Identifier
* Type
* Location
* Size
* Protction
* Time, date, user ID

Info about tiles are kept in the directory structure, which is maintained on the disk  

File opeations
* Write
* Read
* Reposition within file
* Delete
* Truncate  

Open files

Sseveral pieces of data needed to manage open files  
* File POinter
    * Point to last R/W location, per process that has the file open
* File-open count
    * ocunt of number of times a file was opened. Allows removal of data from open-file table when last proceses closes it  
* Disk location of the file
    * Cache of data access information
* Access rights  
    * Per process access mode information  

OPen fil locking
* Mediates access to a file  
    * Mandatory: ccess is dened depending on locks held and requestes
    * Advisory: 

Access methods
* Sequential
* Direct  

Memory-Mapped Files  
* Memory mapped file IO allows file IO to be treated as routine memory accss by mapping a disk block to a page in memory  
* A file is intially read using demand paging. A page sized portion of the file is read from the file system into a physical page. subsequent reads/writes to/from the file are treated as ordinary memory accesses
* Simplifies file access by treating file IO through memory rather than `read()` and `write()` system calls  
* Also allows several processes to map the same file allowing the pages in memory to be shared  

irectory structure: 
* Collection of nodes containing information about all files  
* Both the directory structure and h files reside on disk. Backups of these two ???  

