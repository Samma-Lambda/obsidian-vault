---
tags:
  - Computer
---
This is the physical elements of a computer, this section focused on utilizing the hardware of the computer instead of mathematical or data structure improvements
# RAM
This storage is significantly faster than disk when you retrieve it. But it is typically more limited than the amount of disk space

# Disk 
Disk storage is storage that is slower than RAM for retrieval, but when the machine powers off the data is not lost.  

# Cores 
The CPU can have multiple workers and each worker is known as a core. Often when you write a program, it will only be utilizing a single core, so you can speed things up by utilizing multiple. But since the behavior of cores can be inconsistent, it can cause errors due to something called a race condition(where one thread finishes before another in an unpredictable way). So you typically need to split things up in an effective way(like splitting the roots of merge sort) 