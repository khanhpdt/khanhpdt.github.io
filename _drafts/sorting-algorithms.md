---
layout: post
title: Sorting algorithms
tags: [algorithms]
---

This post summarizes the main idea and the steps of some fundamental sorting algorithms. Let first assume that the algorithms sort a given array in _ascending_ order.

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

This algorithm sorts by using the data structure _heap_ and its special heap property. Let just consider max heaps where the heap property says that each node in the heap is equal to or larger than its children. Because of this max-heap property, the largest element is always the root of the heap. 

For each iteration, this algorithm swaps the largest element (which currently is the root of heap) with the last element in the array. After this step, the largest element is considered sorted and thus ignored for later iterations. However, because the swap might break the max-heap property, the algorithm must restructure the heap (but without considering the sorted elements) to preserve the property.

## Quick sort

Like merge sort, this algorithm follows the divide-and-conquer technique. 

The algorithm divides the input array into three parts: two subarrays and a pivot element, which must satisfy the following properties:
    
- The pivot element stays between the two subarrays, i.e., the structure of the array after the divide step is `[first_subarray, pivot_element, second_subarray]`.
- All elements in `first_subarray` <= `pivot_element` < all elements in `second_subarray`

After the divide step, the algorithm continues with the conquer step to sort each of the two subarrays recursively. As the pivot element is already in its correct position, it will not be considered by the algorithm anymore. 

The combine step is not necessary as the two subarrays and the pivot element are already in their correct positions.

The crux of this algorithm is the divide step, which is commonly referred to as the partition step. This step is the one that actually does the sorting. Conceptually, this algorithm can be viewed as a sequence of partitionings.

The performance of this algorithm is mainly influenced by the balance between the partitions created in the divide step. The worst case is when one of the partitions is empty, and the best case is when the two partitions have approximately the same size. 

The performances of the algorithm in the worst and best case can be intuitively calculated as follows. The partitioning cost is the same in two cases, i.e., `O(n)`. In the worst case, the algorithm is recursively called `O(n)` times, whereas in the best case only `O(lg(n))`. So, in total, the worst case takes `O(n^2)` time, whereas the best case `O(n*lg(n))` time.

## Complexity comparisons

## Source code

- [github/sortings](https://github.com/khanhpdt/datastructures-algorithms/tree/master/algorithms/src/main/java/org/khanhpdt/playgrounds/algorithms/sortings)

## References

[1] [Algorithms](http://www.amazon.com/Algorithms-4th-Robert-Sedgewick/dp/032157351X/ref=sr_1_2?ie=UTF8&qid=1461440135&sr=8-2&keywords=algorithms)
[2] [Introduction to algorithms](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)
[3] [The art of computer programming, Vol. 3](http://www.amazon.com/Art-Computer-Programming-Sorting-Searching/dp/0201896850/ref=sr_1_9?s=books&ie=UTF8&qid=1461485952&sr=1-9&keywords=the+art+of+computer+programming)