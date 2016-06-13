---
layout: post
title: Algorithm analysis
tags: [algorithms]
---

Analyzing an algorithm is to determine how much resources the algorithm needs. The resources might be either memory usage, or computational time, or network resources. However, computational time is the desired in most of the cases.

## Computational time

Computational time is the time needed for an algorithm to do its processing.

An algorithm comprises of the basic operations provided by the machine on which it is run. As a result, its computational time is calculated from those of the basic operations. To simplify the analysis of the computational time, the _RAM model_ is usually used as a hypothetical machine to run an algorithm. In this model, each basic operation (e.g., arithmetic, data movement, control, subroutine call and return) takes a constant amount of time [1, Sec. 2.2].

The computational time of an algorithm depends on two properties of its input: the size and the characteristics. For example, the computational time of an insertion sort algorithm increases as the number of items increases, and given a number of items to be sorted, the algorithm takes the longest time when the items are in the reverse order of the desired order.

## Order of growth (or Rate of growth)

The order of growth of an algorithm tells us how quickly the computational time of the algorithm increases with the size of the input of the algorithm.

Order of growth is usually represented by asymptotic notations including only the leading term (excluding its coefficient) of the computational time formula.

![asymptotic-notations](/assets/imgs/algorithms/asymptotic-notations.png)
(Source: [1, Fig. 3.1])

The asymptotic notations are commonly used to represent the order of growth because:

  - They are easier to derive than the exact computational time.
  - Their accuracy increases as the input size increases, because the contribution of the leading term becomes more significant as the size increases. Thus, asymptotic notations fit well into the situations where it is interested to know how an algorithm performs as the input size increases. (However, for the small input size, they are not so accurate.)
  - They make it simple to compare the computational time of different algorithms.

## Types of analyses

### Best-case analysis

This analysis focuses on the shortest time an algorithm might take for a given input size.

### Worst-case analysis

This analysis focuses on the longest time an algorithm might take for a given input size.

### Average-case analysis

This analysis focuses on the average time an algorithm might take for a given input size. It typically uses probability to analyze the average time.

### Amortized analysis



## References

[1] [Introduction to algorithms](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)
