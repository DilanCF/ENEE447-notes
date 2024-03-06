# ENEE447 Lecture 12 

> 3/4/24

### Chapter 10b: Real-Time Scheduling  

Midterm 1 will only have chapters 2-5, 9, NO CHAPTER 10  

Looking at scheduling algos fro real-time systems  

RTS have periodic tasks  

![alt text](img/Lecture12/image.png)  

Occasionally, if there is an aperiodic task, there must be a way to take care of it  

What do if we have a period close to 1?
* Must upgrade the system
* Periodic systems with a utilization of 1 means we need something stronger  

For periodic tasks, its sufficient to have a hyperperiod  

IN exam 2, if there is a question for hyperperiod, we may need to find i and draw out the schedule for it  

![alt text](img/Lecture12/image-1.png)  

Any time we are given a set of tasks, first we need to calculate the total utilization. If more than 1, we cannot schedule anymore  
* Here, $2/5$ + $9/15$ = 1

If there is an aperiodic task, some deadlines will be missed  

The bottom img/Lecture12/image shows that after the first hyperperiod, everything can repeat  

![alt text](img/Lecture12/image-2.png)  

We really need to look at the deadlines, not so much on fairness
* RR not great for RTS  

![alt text](img/Lecture12/image-3.png)  

*Change png names starting here*
![alt text](img/Lecture12/image-5.png)

If we try to do FCFS (first img/Lecture12/image), we miss deadlines due to other tasks running at the time we wanted to do T<sub>1</sub> in order to meet the deadline  

*FIX THIS PNG: (1,3) -> (3,1), etc.*

Whereas for the second algorithm, we can see that we meet the deadliness comfortably for both tasks  

![alt text](img/Lecture12/image-6.png)  

We usually know how many tasks we will have due to a more deterministic system  

![alt text](img/Lecture12/image-7.png)  

Feasibility: Is the utilization less than 1?  

![alt text](img/Lecture12/image-8.png)  

![alt text](img/Lecture12/image-9.png)  

![alt text](img/Lecture12/image-10.png)  

If util > 1, impossible feasibility.

If < 1, some algorithms may still not be able to be scheduled  

![alt text](img/Lecture12/image-11.png)  

![alt text](img/Lecture12/image-12.png)  

Loosely categorize them into these groups since some algorithms may be hybrids  

Static == offline  

![alt text](img/Lecture12/image-13.png)  

Not much difference: Main one is the terminology  
* One gives priority, which we take into consideration
    * Priority is also given statically  

![alt text](img/Lecture12/image-14.png)  

Best effort: Used by many modern operating systems  

![alt text](img/Lecture12/image-15.png)  

Cyclic, RMS, EDF algorithms will be studied first  

There is some similarity with RR where we divide the time into quantums  

Divide into slots

At the beginning of every minor cycle, look at the ready tasks and determine based on deadlines which should go next  

![alt text](img/Lecture12/image-16.png)  

(Here he chose to change some of the variable letters, not really necessary)  

Major cycle == hyperperiod  

![alt text](img/Lecture12/image-17.png)  

Brown == T1
Blue == T2
Green == T3  

![alt text](img/Lecture12/image-18.png)  

![alt text](img/Lecture12/image-19.png)  

![alt text](img/Lecture12/image-20.png)  

![alt text](img/Lecture12/image-21.png)  

![alt text](img/Lecture12/image-22.png)  

![alt text](img/Lecture12/image-23.png)  

![alt text](img/Lecture12/image-24.png)  

Highest-priority ready task (The one with the shorted period)

As the period increases, the priority decreases  

Say we have the following 3 tasks: 

T1: (10,3)
T2: (5,2)
T3: (20,5)  

Priorities in descending order: 
1. T2
2. T1
3. T3  

![alt text](img/Lecture12/image-25.png)  

Hyperperiod: 140  

Calculating utilization gives us 131/140, meaning we can try and schedule these tasks  

![alt text](img/Lecture12/image-26.png)  

if your utilization is less than .69 (nice), you're guaranteed to have a proper schedule  

In the exam, if you miss a deadline, you need to make it clear  

When you miss a deadline, what should happen?  

Here, we assume if you missed a deadline there is not point to continue  

What will happen if we try to use a non-preemptive method?  

*Phone pic here*

![alt text](img/Lecture12/image-27.png)  

![alt text](img/Lecture12/image-28.png)  
<sub>hehe nice max utilization</sub>  

![alt text](img/Lecture12/image-29.png)  

![alt text](img/Lecture12/image-30.png)  

![alt text](img/Lecture12/image-31.png)  

![alt text](img/Lecture12/image-32.png)  

*Will finish rest on Wednesday*