---
layout: post
title: Linked lists
tags : [data-structures]
---

## Overview

A linked list is a data structure in which each item links to some other items in the list.

Linked lists do not support random access. To get an item in the list, one has to traverse the list until reaching the item holding a link to the target item. This is the main disadvantage of linked lists.

### Linked lists vs. Arrays

| Linked lists | Arrays |
| :------------- | :------------- |
| - Easy to expand | - Hard to expand       |
| - Sequential access | - Random access by index |
| - Use just as much memory as needed | - Memory preallocated, so might be either too much or too little |
| - Insertion takes O(1) time | - Same |
| - Not required  | - Deleting or inserting requires to rearrange items, which can take much time if the item is big |

## Types of linked lists

### Singly linked lists

A singly linked lists is an ordinary linked list in which each item holds a link to its next item.

### Double-ended linked lists

A double-ended list is a singly linked list in which the list object holds two links to the first and last items of the list. This makes accesses to the end of the list more efficient. For example, adding an item to the end of the list is just as simple as to the beginning. However, it makes it more complicated when removing items from the list, as not only the head but also the tail needs to be carefully updated because the removed items can be either of them.

### Doubly linked lists

A doubly linked list is a linked list in which each item holds references to its next and previous ones. The advantage is that is makes it convenient to traverse backward, but the disadvantages are that it requires more memory to store the link to the previous item and also it leads to more processing on basic operations (e.g., insertion, deletion) because they have to deal with more links than in singly linked lists.

### Circular linked lists

A circular linked list is a linked list in which the last item holds a link to the first item. Although circularity makes it more convenient to traverse the whole list starting from any item in the list, it demands different implementations to handle basic operations (e.g., search, remove) because if the same implementations as in other non-circular list are used, the loop over the list might take forever as the last item now points to the first item instead of a sentinel item which signals the end of the list.

## Code samples

- See [github/linkedlists](https://github.com/khanhpdt/java-playground/tree/master/src/main/java/org/khanhpdt/javaplayground/datastructures/linkedlists)

## References

[1] Data structures and algorithms in Java
