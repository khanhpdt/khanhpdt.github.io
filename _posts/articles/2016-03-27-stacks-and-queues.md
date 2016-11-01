---
layout: post
title: Stacks and Queues
excerpt: ""
categories: articles
tags: [data-structures]
---

Stacks and queues are data structures in which the items can only be accessed in a restricted way.

## Stacks

A stack is a last-in-first-out (LIFO) data structure where both insertion and deletion takes place at only one end of the stack.

Two basic operations on a stack are push and pop. Push is to add an item into the stack, and pop is to remove an item from the stack.

## Queues

An ordinary queue is a first-in-first-out (FIFO) data structure where insertion takes places at one end and deletion at the other end of the queue.

Two basic operations on a queue are enqueue and dequeue. Enqueue is to add an item into the queue, and dequeue is to remove an item from the queue.

A deque is a double-ended queue where insertion and deletion can take place at both of the queue's ends.

A circular queue is an ordinary queue which allows to move the pointers (front and rear) circularly. For example, if a new item is added when the rear pointer already points to the last position in the queue but there is still space between the beginning of the queue and the front pointer, then the rear pointer is allowed to move to the beginning of the queue. Thus, the circularity helps to make use of all the available space in the queue.

A priority queue is a queue where the highest (or lowest) priority is always at the front.

## Source code

- [github/stacks](https://github.com/khanhpdt/datastructures-algorithms/tree/master/data-structures/src/main/java/vn/khanhpdt/playgrounds/datastructures/stacks)
- [github/queues](https://github.com/khanhpdt/datastructures-algorithms/tree/master/data-structures/src/main/java/vn/khanhpdt/playgrounds/datastructures/queues)

## References

[1] [Data structures and algorithms in Java](http://www.amazon.com/Data-Structures-Algorithms-Java-2nd/dp/0672324539/ref=sr_1_4?s=books&ie=UTF8&qid=1461439850&sr=1-4&keywords=data+structures+and+algorithms+in+java)
