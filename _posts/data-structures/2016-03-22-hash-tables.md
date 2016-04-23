---
layout: post
title: Hash tables
tags: [data-structures]
---

## Overview

A hash table is a data structures which map an element's key to its value. The crux in the implementation of a hash table is its hash function, which, given an element's key, computes the _slot_ (or _bucket_) in the table where the element's value is stored.

<!--break-->

![hash-function]({{ site.url }}/assets/imgs/hash-tables/hashing.png)
(Source: [1])

In the picture, `h()` is the hash function which maps the key of an element to its index in the hash table `T`.

- Pros
  - Fast insertion and search (only takes `O(1)` time on average)
- Cons
  - Difficult to expand because hash tables are built upon arrays
  - Unordered

## Hash functions

Some important requirements on hash functions:

  - Consistent
    A hash function must produce same output for the same input. Conversely, if a hash function produces two different outputs, we know that the inputs are different. However, given two different inputs, it is not guaranteed that the outputs are different.  
  - Efficient
    A hash function should be fast. This usually leads to simple hash functions.
  - Produce uniformly and independently distributed hash values (ideal case)
    One heuristic when designing the hash function is that the function should take into account every bit of information from its input.

## Hash collisions and resolutions

A collision occurs when the hash function produces same hash value for different items. This is because the hash function cannot produce uniformly and independently distributed hash values. This is actually always the case in practice.

There are two popular approaches to deal with the collisions: open addressing and separate chaining.

### Open addressing

Each slot holds a single item. When collision happens, other slots are probed to see if they are available.

#### Linear probing

This probing sequentially probes the slots next to the colliding slot.

For example, if the collision occurs at slot `x`, this probing sequentially probes slots `x + 1`, `x + 2`, `x + 3`, ... until it finds a vacant slot.

The problem of linear probing is that it tends to create clusters. A cluster is formed by the items of the same hash value. As the number of items increases, the clusters get bigger. This problem is called _primary clustering_. It increases the cost of probing, because when a collision occurs in a cluster, the probing must probe all the items in the cluster starting from the collision point.

#### Quadratic probing

This probing quadratically probes other slots when collision occurs. The idea is to make the probe as wide as possible to avoid the primary clustering problem in linear probing.

For example, if the collision occurs at slot `x`, this probing probes slots `x + 1`, `x + 4`, `x + 9`, ... until it finds a vacant slot.

This probing reduces the chance of creating big cluster, i.e., primary clustering, but still suffers from the other clustering problem called _secondary clustering_. This problem occurs when the items of same hash value are probed in the same sequence. This is not good because as the number of items increases, the probe sequence gets bigger and thus the probing time increases.

#### Double hashing

This probing decides the step-size of the probe by another hash function. The idea is to make the step-size different for each key, so that different keys generate different probe sequences. This helps to avoid the secondary clustering problem in quadratic probing.

Requirements of the second hash function:

  - Different than the primary hash function
  - Must not produce `0`, otherwise endless loop

For example, if the collision occurs at slot `x` for the key `k`, this probing probes slots `x + h2(k)`, `x + 2*h2(k)`, `x + 3*h2(k)`, ... until it finds a vacant slot, where `h2(k)` is the second hash function.

A popular example of the second hash function is `h2(k) = CONSTANT - (k % CONSTANT)`.

### Separate chaining

Each slot in the table references to a list instead of a single object. When collision happens, the colliding element is put into the list at the corresponding slot.

Because each slot in the table points to a list, this resolution allows the load factor to be greater than or equal to 1, which is in contrast to open addressing where the load factor can be at most 1. Furthermore, the performance when using this resolution is not affected by the load factor as much as when using open addressing. When the load factor increases, it is more likely that collision occurs. In case of open addressing, this also means that the probe sequence gets longer when the load factor increases, while in this chaining approach, the collision resolution is not affected at all as it is still done by simply putting the colliding element to the list. Thus, the chaining approach is more robust to the load factor, especially when the number of items are not known in advance.

## References

[1] [Introduction to algorithms](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)
[2] [Data structures and algorithms in Java](http://www.amazon.com/Data-Structures-Algorithms-Java-2nd/dp/0672324539/ref=sr_1_4?s=books&ie=UTF8&qid=1461439850&sr=1-4&keywords=data+structures+and+algorithms+in+java)

## Further readings

- [https://en.wikipedia.org/wiki/Hash_table](https://en.wikipedia.org/wiki/Hash_table)
- [https://en.wikipedia.org/wiki/Primary_clustering](https://en.wikipedia.org/wiki/Primary_clustering)
