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
(4)getQueue: using this method could return date which according the index which we could input this index as a parameters. Next step, the front will be added 1. However, before we add, we need to verify whether existing valid data by Isempty method.
(5)showQueue: using this method could show all the data of this Queue by traversing Queue, from front to rear. However, before show this queue, we need to verify whether existing some data in the queue.
(6)size: using method could return the number of valid data. by expression which is(rear+maxSize-front).
(7)headQueue: using this method could reutrn first date by returning front.

## code implementation
``` java
public class CircleQueue {
    int front;
    int rear;
    int maxSize;
    int[] arr;

    public CircleQueue(int arrMaxSize) {
        maxSize = arrMaxSize;
        rear = 0;
        front = 0;
        arr = new int[maxSize];
    }

    // judge Queue whether has space
    public boolean isFull() {
        return (rear + 1) % maxSize == front;
    }

    // judge whether existing data in Queue
    public boolean isEmpty() {
        return front == rear;
    }

    // add data in Queue
    public void addQueue(int n) {
        // if Queue was filled, there is no space to store.
        if (isFull()) {
            System.out.println("Queue was filled");
            return;
        }
        // add parameter to Queue
        arr[rear] = n;
        // putting rear behind, needing think of making module.
        rear = (rear + 1) % maxSize;
    }

    // acquiring data from Queue.
    public int getQueue() {
        // judge whether existing data in Queue
        if (isEmpty()) {
            throw new RuntimeException("Queue is empty, cannot get");
        }
        // front is pointing the fist data of Queue.
        // 1.creating a temporary variable to store the data which is pointed by front.
        // 2.putting front behind, needing think of making module.
        // 3.returning temporary variable.
        int val = arr[front];
        front = (front + 1) % maxSize;
        return val;
    }

    // show all the data which in the Queue
    public void showQueue() {
        if (isEmpty()) {
            System.out.println("there is no data in the queue");
            return;
        }
        // traversing Queue from front achieve to last valid.
        /*
         * Do not set rage in sizs()
         * must noting traverse rage is from front to (front + size()), which is dynamic
         * rage!!!
         */
        for (int i = front; i < front + size(); i++) {
            System.out.printf("arr[%d]=%d\n", i % maxSize, arr[i % maxSize]);
        }
    }

    /*
     * returning the number of valid data. must to think making module because Queue
     * has cycle.
     */
    public int size() {
        return (rear + maxSize - front) % maxSize;
    }

    // show the head of Queue,noting this is not get head.
    public int headQueue() {
        // firstly, must judge whether existing headQueue
        if (isEmpty()) {
            throw new RuntimeException("there is no data in the queue");
        }
        return arr[front];
    }

    public static void main(String[] args) {
        CircleQueue c = new CircleQueue(4);
        // add three data in Queue
        c.addQueue(10);
        c.addQueue(19);
        c.addQueue(15);
        /*
         * test whether Queue is full. Though the arrMaxSize is 4,
         * /*one space must keep empty.
         * thus, the number of valid data cannot over 3.
         */
        System.out.println(c.isFull());
        c.getQueue();
        c.getQueue();
        c.getQueue();
        // if the number of data that over we store, function report Exception.
        try {
            c.getQueue();
        } catch (Exception e) {
            System.out.println(e.getMessage());
        }
        /* after getting out three data, we need judge whether Queue is empty */
        System.out.println(c.isEmpty());
        /* this processing is judege whehter Queue is cycle Queue */
        c.addQueue(23);
        c.addQueue(28);
        c.addQueue(32);
        //show entire Queue
        c.showQueue();
        //print the data which we get
        System.out.println(c.getQueue());

    }
}
```

