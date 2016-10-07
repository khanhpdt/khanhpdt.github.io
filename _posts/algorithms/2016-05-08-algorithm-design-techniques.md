---
layout: post
title: Algorithm design techniques
tags:
  - algorithms
---

## Divide-and-conquer

Divide-and-conquer technique solves a problem by continually dividing the given problem into subproblems until each of those subproblems is simple enough to be conquered easily. Then, it combines the solutions to those subproblems into the solution for the original problem.

This technique typically involves three steps:

  * _Divide_ the problem until the subproblems are simple enough
  * _Conquer_ each subproblem
  * _Combine_ the solutions to the subproblems into the one for the original problem.

A well-known example of using divide-and-conquer technique is the merge-sort algorithm.

<!--break-->

Computing the complexity of divide-and-conquer algorithms usually involves solving recurrences. There are three main techniques to solve recurrences [1, Chapter 4]:

  * The substitution method
  * The recursion-tree method
  * The master method

## Dynamic programming

Dynamic programming is similar to divide-and-conquer technique in that it also splits the problem into subproblems and then tries to solve each subproblem recursively. However, the main difference arises when the subproblems _overlap_. In this situation, the divide-and-conquer technique is unaware of the overlapping and thus will solve the overlapped subproblems multiple times. On the contrary, dynamic programming is aware of the overlapping. Thus, it only solves the overlapped problems once and then simply looks up the solutions when the overlapped subproblems are encountered again.

The "programming" in "dynamic programming" refers to the look up, not to writing code. As dynamic programming stores the solutions so that it does not need to recompute them again, it is a typical example of the classic trade-off between computational time and memory.

Dynamic programming technique should only be used to solve optimization problems with two properties: optimal substructure and overlapping subproblems [1, Sec. 15.3]. A problem has optimal substructure if an optimal solution to the problem consists of optimal solutions to the subproblems. Optimal substructure requires that the resources used to find the solutions to the subproblems are independent of each other. On the other hand, a problem has overlapping subproblems if the recursion to solve the problem leads to solving some subproblems multiple times.

Dynamic programming technique involves four steps [1, Chapter 15]

  - Characterize the structure of an optimal solution
  - From the previous analysis, derive a recursion definition for the value of an optimal solution
  - From the previous recursion definition, derive an algorithm to compute the value of an optimal solution.
  - Construct an optimal solution, if one is needed (note that the previous steps only try to find the value of an optimal solution)

There are two approaches to implementing dynamic programming algorithms:

  - Top-down: The algorithm is implemented as a normal recursive algorithm, but when a solution to a subproblem is found, it is saved so that it can be looked up later when the same subproblem is encountered.
  - Bottom-up: The subproblems are solved in the order of their sizes with the smallest first, so that when a subproblem is encountered, it is guaranteed that all of its subproblems are already solved.

## Greedy heuristic

Greedy heuristic is usually used to solve optimization problems. At each decision point, this heuristic always chooses the direction that seems best at the moment. In other words, it always chooses the _best_ option for the _current_ situation.

Because the heuristic considers only locally-best solutions, it cannot guarantee optimal solutions; however, sometimes it still leads to one.

## Randomization

This technique is used to make the behavior of an algorithm dependent on random values during its execution, thereby making the behavior of the randomized algorithm _undeterministic_ at run-time.

One typical use case of this technique is to randomize the input of an algorithm so that the algorithm achieves its _expected_ performance. This should only applies to algorithms whose expected performances are better than their worst-case ones. For example, the technique can be used to randomize the input of the quick sort algorithm whose expected computational time is `O(n*lgn)` which is much better than `O(n^2)`  in its worst case.

There are two common ways to randomize an array:
  
  1. Randomize by sorting: Assigns each element a random value and reorder the elements in the array by their associated random values.
  2. Randomize in-place: Iterates over the array and swaps each element with a randomly chosen element in the array. 

The latter approach is better than the former, as it requires no extra memory to store the random values and no sorting.

# References

[1] [Introduction to algorithms](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)
