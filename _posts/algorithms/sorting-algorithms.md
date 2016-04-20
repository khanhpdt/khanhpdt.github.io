---
layout: post
title: Sorting algorithms
tags: [algorithms]
---

Let assume that the algorithms are used to sort a given array in _ascending_ order.

## Selection sort

Conceptually, this algorithm organizes the array into two areas: the sorted area containing the elements in sorted order and the other area containing the remaining unsorted elements. Let call the sorted area as _S_ and the unsorted area as _U_. Initially, _S_ is empty and _U_ is the whole array. 

For each iteration, this algorithm selects the minimum element from _U_ and then adds it into _S_. Thus, the sorting is done by the selection operation.

## Insertion sort

This algorithm also uses two areas during the sorting.

For each iteration, this algorithm sequentially selects _an_ element from _U_ and inserts it into _S_ such that the order in _S_ is preserved. Thus, the sorting is done by the insertion operation.

## Shell sort

This algorithm is an extension of the insertion sort algorithm to improve the computational time on average. It does so by reducing the number of memory movements needed to insert an element, which is proportional to the distance between its current and correctly-sorted position.

The idea is to divide the array into multiple subarrays and then sort the subarrays independently. The subarrays are interleaved and contain the elements that are `h`-position far from each other. 

The algorithm consists of multiple iterations, during which the insertion sort can be used to sort the subarrays. After each iteration, the distance `h` is reduced and the algorithm completes when `h = 1`.

Because the elements in each subarray is `h`-position from each other, this algorithm facilitates movements of elements in large distances in the first iterations. This helps to make the array become more well-sorted as `h` decreases, thereby reducing the number of movements in later iterations and on average.

## Bubble sort

## Merge sort

## Heap sort

## Quick sort

## Complexity comparisons

## References

[1] Algorithms, 4th
[2] Introduction to algorithms, 3rd
[3] The art of computer programming, Vol. 3