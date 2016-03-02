---
layout: post
title: Java Collections
category: java
---
# Chapter 10
- Java Collections Framework: java.util and java.util.concurrent
- Figure 10-1: The main interfaces of Java Collections Framework

# Chapter 11
- Iterator
  - Provides a _uniform_ way to access collection elements sequentially
  - foreach loop can be used with arrays or any collections implementing Iterable
  - fail-fast behavior
- Three basic operations:
  - Insertion and removal of elements by position
  - Retrieval elements by their contents
  - Iteration over all elements
- Amortized cost
- Concurrent collections are preferred over synchronized collections
  - See Java concurrency in practice for more details on concurrent collections

# Chapter 12

# Chapter 13

## Set
- No duplicate
- HashSet
  - Implemented by a hash table
  - Pros: basic operations like add, remove, check items
  - Cons: iterating
- LinkedHashSet
  - Order when adding is reserved
  - Pros: next() operation
  - Cons: overhead in maintaining references to the previous and next elements
- CopyOnWriteArraySet
  - Thread-safe
- EnumSet
  - Operations are bit-wise, thus they are fast
