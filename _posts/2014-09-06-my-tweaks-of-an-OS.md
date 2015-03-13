---
layout: post
title: My tweaks of PintOS Operating System!
---

[Pintos](http://web.stanford.edu/class/cs140/projects/pintos/pintos.html#SEC_Contents) is a simple operating system framework for the 80x86 architecture. It does not support priority scheduling. Our task is to implement priority scheduler and multilevel feed back priority scheduler.    
* [Code repo Link](https://github.com/prakashn27/Pintos-Project1).

##Algorithm###
###Priority Scheduler###
* For priority scheduler, Changed the scheduler linked list into priority queue, so that everytime next Highest prioirty thread is scheduled.

**Pros:** 
1. Guarantees early completion of high priority jobs

**Cons:**     
- Can cause starvation of low priority jobs 
- How to decide/assign priority numbers?


###Multi level feedback priority queue scheduler###
* For Multilevel feedback queue scheduler, I maintained seperate queue (8ms round robin queue, 16ms round robin queue and FIFO). All the process first goes into the first queue, if it is not completed then it is scheduled to next queue and even if 24ms (8 + 16) is not enough for the process to finish it is appended in the tail of the FIFO. 

**Pros:**		
1. Great for timesharing – no starvation
2. Does not require prior knowledge of CPU burst times
3. Generally reduces average response time

**Cons:**			
1. What if all jobs are almost time same length? Increases the turnaround time.			
2. How to set the “best” time quantum?
  		* if small, then context switch often, incurring high overhead			
  		* if large, then response time degrades				

