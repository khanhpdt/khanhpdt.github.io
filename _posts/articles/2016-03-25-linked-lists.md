---
layout: post
title: Linked lists
excerpt: ""
categories: articles
tags : [data-structures]
---

## Overview

A linked list is a data structure in which each item is linked to other items in the list.

Linked lists do not support random access. To get an item in the list, one has to sequentially traverse the list until reaching the item. This sequential access is also the main disadvantage of using linked lists.

### Linked lists vs. Arrays

| Linked lists | Arrays |
| :------------- | :------------- |
| - Easy to expand | - Hard to expand       |
| - Sequential access | - Random access by index |
| - Use just as much memory as needed | - Memory preallocated, so might be either too much or too little |
| - No rearrangement required  | - Deleting or inserting might require to rearrange items, which can take much time if the items are big |
{: .table}

## Types of linked lists

### Singly linked lists

A singly linked list is an ordinary linked list in which each item holds a link to its next item.

### Double-ended linked lists

A double-ended linked list is a singly linked list in which the list object holds the links to both the first and last items of the list. This helps accesses to the list end more efficient. For example, adding an item to the end of the list is just as simple as to the beginning. However, it makes it more complicated when removing items from the list, as not only the head but also the tail needs to be carefully updated because the removed items can be either of them.

### Doubly linked lists

A doubly linked list is a linked list in which each item holds references to its next and previous items. The backward link makes it convenient to traverse backward, but it needs more memory and makes basic operations (e.g., insertion, deletion) more complicated because they have to deal with more links than in singly linked lists.

### Circular linked lists

A circular linked list is a linked list in which the last item holds a link to the first item. Although circularity makes it more convenient to traverse the whole list starting from any item in the list, it demands different implementations to handle basic operations (e.g., search, remove). This is because if the same implementations as in other non-circular lists are used, the loop over circular lists might take forever as the last items now points to the first items instead of the sentinel items which signal the end of the lists.

## Source code

- [github/linkedlists](https://github.com/khanhpdt/datastructures-algorithms/tree/master/data-structures/src/main/java/vn/khanhpdt/playgrounds/datastructures/linkedlists)

## References

[1] [Data structures and algorithms in Java](http://www.amazon.com/Data-Structures-Algorithms-Java-2nd/dp/0672324539/ref=sr_1_4?s=books&ie=UTF8&qid=1461439850&sr=1-4&keywords=data+structures+and+algorithms+in+java)
