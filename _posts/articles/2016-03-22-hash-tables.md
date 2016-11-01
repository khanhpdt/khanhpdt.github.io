---
layout: post
title: Hash tables
excerpt: ""
categories: articles
tags: [data-structures]
---

## Overview

A hash table is a data structure which maps an element's key to its value. The crux in the implementation of a hash table is its hash function, which, given an element's key, computes the _slot_ (or _bucket_) in the table where the element's value is stored.

![hash-function]({{ site.url }}/images/hash-tables/hashing.png)
(Source: [1])

In the picture, `h()` is the hash function which maps the key of an element to its index in the hash table `T`.

The main advantage of using hash tables is that they provide constant-time basic operations, e.g., insert, search, delete, on average.

## Properties of good hash functions

- Consistent: If given the same input, a hash function must always produce the same result. However, if a hash function produces the same result for two inputs, it does not mean the two inputs are the same.
- Efficient
- Uniform: The hash values produced by a hash function should be uniformly and independently distributed. One heuristic when designing a hash function is that the function should take into account every bit of information from its input.

## Hash collisions and resolutions

A collision occurs when the hash function produces the same hash value for different items. This is because the set of possible hash values usually is smaller than the set of possible items, and also because it is difficult to make hash functions uniform in practice.

There are two popular approaches to deal with the collisions: open addressing and separate chaining.

### Open addressing

Each slot holds at most one item. When collision happens, other slots are probed to see if they are available.

#### Linear probing

This probing sequentially probes the slots next to the colliding slot.

For example, if the collision occurs at slot `x`, this probing sequentially probes slots `x + 1`, `x + 2`, `x + 3`, ... until it finds a vacant slot.

The problem of linear probing is that it tends to create clusters. A cluster is formed by the items of the same hash value. As the number of items increases, the clusters get bigger. This problem is called _primary clustering_. It increases the cost of probing, because when a collision occurs in a cluster, the probing must probe all the items in the cluster starting from the collision point.

#### Quadratic probing

This probing quadratically probes other slots when collision occurs. The idea is to make the probe as wide as possible to avoid the primary clustering problem in linear probing.

For example, if the collision occurs at slot `x`, this probing probes slots `x + 1`, `x + 4`, `x + 9`, ... until it finds a vacant slot.

This probing reduces the chance of creating big cluster, i.e., primary clustering, but still suffers from the other problem called _secondary clustering_. This problem occurs when the items of same hash value are probed in the same sequence. This is not good because as the number of items increases, the probe sequence gets bigger and thus the probing time increases.

#### Double hashing

This probing decides the step-size of the probe by another hash function. The idea is to make the step-size different for each key, so that different keys generate different probe sequences. This helps to avoid the secondary clustering problem in quadratic probing.

Requirements of the second hash function:

  - Different than the primary hash function
  - Must not produce `0`, otherwise endless loop

For example, if the collision occurs at slot `x` for the key `k`, this probing probes slots `x + h2(k)`, `x + 2*h2(k)`, `x + 3*h2(k)`, ... until it finds a vacant slot, where `h2(k)` is the second hash function.

A popular example of the second hash function is `h2(k) = CONSTANT - (k % CONSTANT)`.

### Separate chaining

Each slot in the table holds a reference to a list instead of a single item. When collision happens, the colliding element is put into the list at the corresponding slot.

Because each slot in the table points to a list, this resolution allows the load factor to be greater than or equal to 1, which is in contrast to open addressing where the load factor can be at most 1.

The performance when using this resolution is not affected by the load factor as much as when using open addressing. When the load factor increases, it is more likely that collision occurs. In case of open addressing, this also means that the probe sequence gets longer when the load factor increases, while in this chaining approach, the collision resolution is not affected at all as it is still done by simply putting the colliding element to the list. Thus, the chaining approach is more robust to the load factor, especially when the number of items are not known in advance.

## References

[1] [Introduction to algorithms](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)

[2] [Data structures and algorithms in Java](http://www.amazon.com/Data-Structures-Algorithms-Java-2nd/dp/0672324539/ref=sr_1_4?s=books&ie=UTF8&qid=1461439850&sr=1-4&keywords=data+structures+and+algorithms+in+java)

## Further readings

- [https://en.wikipedia.org/wiki/Hash_table](https://en.wikipedia.org/wiki/Hash_table)
- [https://en.wikipedia.org/wiki/Primary_clustering](https://en.wikipedia.org/wiki/Primary_clustering)
