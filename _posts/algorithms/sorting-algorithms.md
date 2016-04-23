---
layout: post
title: Sorting algorithms
tags: [algorithms]
---

Let assume that the algorithms are used to sort a given array in _ascending_ order.

## Selection sort

Conceptually, this algorithm organizes the array into two areas: the sorted area containing the elements in sorted order and the other area containing the remaining unsorted elements. Let call the sorted area _S_ and the unsorted area _U_. Initially, _S_ is empty and _U_ is the whole array. 

For each iteration, the algorithm selects the minimum element from _U_ and then adds it into _S_. Thus, the sorting is done by the selection operation.

<!--break-->

## Insertion sort

This algorithm also uses two areas during the sorting.

For each iteration, it sequentially selects _an_ element from _U_ and inserts it into _S_ such that the order in _S_ is preserved. Thus, the sorting is done by the insertion operation.

## Bubble sort

This algorithm also uses two areas during the sorting.

For each iteration, it "bubble up" the largest element in _U_ into _S_. The "bubble up" operation is done by a sequence of two operations: comparing two neighboring elements and swapping them if they are out of order. Because the largest element in _U_ will always be swapped with its neighbor to the right, it will be moved (or "bubbled up") to the last position in _U_ and eventually be added to _S_. Thus, the sorting is done by the "bubble up" operation.

## Shell sort

This algorithm is an extension of the insertion sort algorithm to improve the computational time on average. It does so by reducing the number of memory movements needed to insert an element, which is proportional to the distance between its current and correctly-sorted position.

The idea is to divide the array into multiple subarrays and then sort the subarrays independently. The subarrays are interleaved and contain the elements that are `h`-position far from each other. 

The algorithm consists of multiple iterations. In each iteration, the insertion sort algorithm is used to sort the subarrays, and the value of `h` is reduced after each iteration until `h = 1` which is also when the algorithm completes.

Because the elements in each subarray is `h`-position from each other, this algorithm facilitates movements of elements in large distances in the first iterations. This helps to make the array become more well-sorted as `h` decreases, thereby reducing the number of movements in later iterations and on average.

This algorithm reduces the overall memory movements by exploiting the trade-off between the size and the partial order of an array to be sorted. It pays upfront the cost to sort each subarray whose size is smaller than the original array to make the original array become more well-sorted after each iteration. Eventually, it turns out that the partial order not only compensates for those upfront costs but also makes this algorithm more efficient than the insertion sort algorithm.

The average computational time of this algorithm depends on the values of the `h`-sequence.

## Merge sort

This algorithm follows the divide-and-conquer technique. It divides the array into two subarrays, then recursively sorts each of them, and finally merges the sorted subarrays to produce the sorted version of the original array.

The crux of this algorithm is the merge operation, which combines any two sorted arrays to produce a new sorted array containing all the elments of the input arrays.

What this algorithm actually does is to organize a sequence of merges in such a way that the output is a sorted array. Thus, the sorting is done by the merge operation, and as a result the performance of this algorithm is determined by that of the merge operation.

## Heap sort

## Quick sort

## Complexity comparisons

## Source code

## References

[1] Algorithms, 4th
[2] Introduction to algorithms, 3rd
[3] The art of computer programming, Vol. 3