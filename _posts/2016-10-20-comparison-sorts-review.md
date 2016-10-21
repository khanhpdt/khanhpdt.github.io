---
layout: post
title: Comparison sorts review
tags: 
  - algorithms
---

This post reviews the basic ideas of the fundamental comparison-sort algorithms, namely the sorting algorithms where the order between two elements are determined by _comparing_ them.

The sorting order is assumed to be ascending.

## Selection sort

During sorting, this algorithm splits the array to two areas: the sorted area containing elements in sorted order and the unsorted area containing the remaining unsorted elements. Let call the sorted area __S__ and the unsorted area __U__. Initially, __S__ is empty and __U__ is the whole array. If the sorting is in-place, then __S__ stands before __U__ in the array.

For each iteration, this algorithm _selects_ the minimum element from __U__ and then adds it into the tail of __S__. Thus, after each iteration, __U__ is shrinked, whereas __S__ is expanded. The iteration continues until __U__ is empty, meaning all items are sorted.

<!--break-->

Because this algorithm always looks for the mininum element in __U__, its performance is insensitive to whether the input is sorted or not.

[Complexity:](https://en.wikipedia.org/wiki/Selection_sort)

| Best | Average | Worst |
| :----: | :------: | :-----: |
| `O(n^2)` | `O(n^2)` | `O(n^2)` |

## Insertion sort

This algorithm also produces two areas __U__ and __S__ during sorting, and if the sorting is in-place, then __S__ also stands before __U__ in the array.

For each iteration, it takes an element from __U__ and _inserts_ it into __S__ without breaking the order in __S__. As in selection sort, the iteration continues until __U__ is empty. This algorithm is different than selection sort in that the sorting in this algorithm is done by the insert operation, while that in selection sort is done by the select operation.

The best case of this algorithm is when the input is already sorted, whereas the worst case is when the input is sorted in the reverse order. 

One special property of this algorithm is that it can be used to sort [online](https://en.wikipedia.org/wiki/Online_algorithm), because it does not need to know all the elements of __U__ in advance.

[Complexity:](https://en.wikipedia.org/wiki/Insertion_sort)

| Best | Average | Worst |
| :----: | :------: | :-----: |
| `O(n)` | `O(n^2)` | `O(n^2)` |

## Bubble sort

Similar to selection sort and insertion sort, this algorithm also produces the two areas during the sorting. However, in constrast to those algorithms, if this algorithm sorts in-place, then __U__ stands before __S__ in the array.

At each iteration, the largest element in __U__ is "bubbled up" until it reaches __S__. This "bubble up" operation comprises of two steps: compare two neighboring elements and swap them if they are out of order. Since a larger element is always swapped with its right neighbor, the largest element will be shifted to the right (aka "bubbled up") and eventually to the end of __U__, then it is moved to the head of __S__.

If we view the "bubble up" operation as the select operation in selection sort, this algorithm behaves similarly to selection sort, except that the selected element is the largest one, not the smallest one as in selection sort.

Like insertion sort, the best case of this algorithm is when the input is already sorted, whereas the worst case is when the input is sorted in the reverse order.

[Complexity:](https://en.wikipedia.org/wiki/Bubble_sort)

| Best | Average | Worst |
| :----: | :------: | :-----: |
| `O(n)` | `O(n^2)` | `O(n^2)` |

## Shell sort

This algorithm is an extension of the insertion sort algorithm to improve the computational time on average. It does so by reducing the average number of memory movements needed to insert an element.

The idea is to divide the array into subarrays that are interleaved across the array and contain the elements `h`-position apart from each other. At each iteration, each of those subarrays are sorted by insertion sort. After that, the gap `h` is reduced and new subarrays are formed. The algorithm then repeats the sorting with those new subarrays until `h = 1`. At this point, the whole array is sorted since when `h = 1`, the whole array is also the only subarray.

There are two benefits from making the elements of subarrays scattered over the whole array. First, the number of movements needed to move elements between large distance is smaller than if the elements are contiguous. For example, given an array with 10 elements, moving the first element to the last position only needs 2 movements in a subarray where `h = 5`, whereas it takes 9 movements if the elements are contiguous. Second, sorting subarrays whose elements are scattered over the whole array makes the array become more well-sorted after each iteration, thereby reducing the number of elements to be moved and also the distances between their current and correctly-sorted positions.

This algorithm is able to reduce the overall memory movements due to the premise that the number of memory movements is dependent on the partial order of the array being sorted. It thus pays upfront the cost to sort the subarrays to make the original array become more well-sorted knowing that this cost will be paid off in the end. And it turns out that the partial order not only compensates for those upfront costs but also makes this algorithm more efficient than the insertion sort algorithm.

The average computational time of this algorithm depends on the values of the `h`-sequence.

[Complexity:](https://en.wikipedia.org/wiki/Shell_sort)

| Best | Average | Worst |
| :----: | :------: | :-----: |
| `O(n*logn)` | Depending on the gap sequence | `O(n*(logn)^2)` |

## Heap sort

This algorithm sorts by using the data structure _heap_ and its special heap property. Let just consider max heaps where the heap property says that each node in the heap is equal to or larger than its children. Because of this max-heap property, the largest element is always the root of the heap. 

At each iteration, this algorithm swaps the largest element (which currently is the root of heap) with the last element in the array. After this step, the largest element is considered sorted and thus ignored in later iterations. Since the swap might break the max-heap property, the algorithm must first restructure the heap (but without considering the sorted elements) to ensure the property and then repeats the iteration with the restructured heap.

[Complexity:](https://en.wikipedia.org/wiki/Heapsort)

| Best | Average | Worst |
| :----: | :------: | :-----: |
| `O(n*logn)` | `O(n*logn)` | `O(n*logn)` |

## Merge sort

This algorithm follows the divide-and-conquer technique. It divides the array into two subarrays, then recursively sorts each subarray, and finally _merges_ the sorted subarrays to produce the sorted version of the original array.

The crux of this algorithm is the merge operation, which combines two sorted arrays to produce a new sorted array with all the elments in the two arrays.

What this algorithm actually does is to organize a sequence of merges in such a way that the output is a sorted array. Thus, the sorting is done by the merge operation, and as a result the performance of this algorithm is determined by that of the merge operation.

[Complexity:](https://en.wikipedia.org/wiki/Merge_sort)

| Best | Average | Worst |
| :----: | :------: | :-----: |
| `O(n*logn)` | `O(n*logn)` | `O(n*logn)` |

## Quick sort

Like merge sort, this algorithm follows the divide-and-conquer technique. 

The first step (divide) in this algorithm is to divide the input array into three parts: two subarrays and a pivot element, which must satisfy the following properties:

  - The pivot element stays between the two subarrays, i.e., the structure of the array after the divide step is `[first_subarray, pivot_element, second_subarray]`.
  - All elements in `first_subarray` <= `pivot_element` < all elements in `second_subarray`

The second step (conquer) is to sort each of the two subarrays recursively. As the pivot element is already in its correct position, it will not be considered by the algorithm anymore. 

The final step (combine) is not necessary as the two subarrays and the pivot element are already in their correct positions.

The crux of this algorithm is the divide step, which is commonly referred to as the _partition_ step. This step is the one that actually does the sorting. Conceptually, this algorithm can be viewed as a sequence of partitionings.

The performance of this algorithm is mainly influenced by the balance between the partitions created in the divide step. The worst case occurs when one of the partitions is empty, whereas the best case does when the two partitions have approximately the same size. The performances of the algorithm in the worst and best case can be intuitively calculated as follows. The partitioning cost is the same in two cases, i.e., `O(n)`. In the worst case, the algorithm is recursively called `O(n)` times, whereas in the best case only `O(lg(n))`. So, in total, the worst case takes `O(n^2)` time, whereas the best case `O(n*lg(n))` time.

[Complexity:](https://en.wikipedia.org/wiki/Quicksort)

| Best | Average | Worst |
| :----: | :------: | :-----: |
| `O(n*logn)` or `O(n)` | `O(n*logn)` | `O(n^2)` |

## Complexity comparisons

See [Comparison of sorting algorithms](https://en.wikipedia.org/wiki/Sorting_algorithm#Comparison_of_algorithms) for a comprehensive comparison.

## Source code

- [github/sortings](https://github.com/khanhpdt/datastructures-algorithms/tree/master/algorithms/src/main/java/vn/khanhpdt/playgrounds/algorithms/sortings)

## Further reading

[1] [Algorithms, 4th](http://www.amazon.com/Algorithms-4th-Robert-Sedgewick/dp/032157351X/ref=sr_1_2?ie=UTF8&qid=1461440135&sr=8-2&keywords=algorithms)
[2] [Introduction to algorithms, 3rd](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)
[3] [The art of computer programming, Vol. 3](http://www.amazon.com/Art-Computer-Programming-Sorting-Searching/dp/0201896850/ref=sr_1_9?s=books&ie=UTF8&qid=1461485952&sr=1-9&keywords=the+art+of+computer+programming)
[4] [Sorting algorithm](https://en.wikipedia.org/wiki/Sorting_algorithm)
