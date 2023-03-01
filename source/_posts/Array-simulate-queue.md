---
title: Array_simulate_queue
date: 2023-02-27 09:20:10
tags:
---
# how to using array.
Queue is a linear list which order is first in and first out. we could define two pointers to help us to Determine the front and rear positions.
## processing
### 1.defined variable
we could definded three varivables : front, rear, maxSize.
Front and rear both from 0;if we add data to this queue, the rear would be added 1. And if we retrieve one data, the front will be added 1.
the maxSize is the volume of the queue, it from front to rear.
### 2.what variable that we should acquire
According to this queue, we could search Valid data, and the value of rear and front.
### 3.method design
(1)isEmpty: using this method could judge if this queue is Empty, which means if rear==front,the quque is Empty. 
(2)isFull: using this method could judge if this queue is full, which means if (rear+1)%maxSize==front, the queue is full.
(3)addQueue: using this method could add data to the queue, first we could use Isfull method to judge whether has space to store this date. Subsequently, storing the parameter which we input-this means arr[rear]=parameter. Afterwards, the rear will be added 1.
(4)getQueue: using this method could return date which according the index which we could input this index as a parameters. Next step, the front will be added 1. However, before we add, we need to verify whether existing valid date by Isempty method.
(5)showQueue: using this method could show all the date of this Queue. in this way, from front to rear. However, before show this queue, we need to verify whether existing some date in the queue.
(6)size: using method could return the number of vaild date. by expression which is(rear+maxSize-front).
(7)headQueue: using this method could reutrn first date by returning front.


