## Randomization

## Divide-and-conquer

Divide-and-conquer is a technique to solve a problem by dividing it into subproblems and then independently conquering each of them. The technique involves three steps:

  - _Divide_ the problem into subproblems.
  - _Conquer_ each subproblem typically by calling the algorithm recursively.
  - _Combine_ the solutions to the subproblems into the one to the original problem.

A well-known example of using divide-and-conquer technique is the merge-sort algorithm.

Computing the complexity of divide-and-conquer algorithms usually involves solving recurrences. There are three main techniques to solve recurrences [1, Chapter 4]:

  - The substitution method
  - The recursion-tree method
  - The master method

<!--break-->

## Dynamic programming

Dynamic programming is similar to divide-and-conquer technique in which it also splits the problem into subproblems and then try to solve each subproblem recursively. However, the main difference arises when the subproblems _overlap_. In this situation, the divide-and-conquer technique is unaware of the overlapping and thus will solve the overlapped subproblems multiple times. On the contrary,  dynamic programming is aware of the overlapping. Thus, it only solves the overlapped problems once and then simply look up the solutions when the overlapped subproblems are encountered again.

The "programming" in "dynamic programming" refers to the look up, not to writing code. As dynamic programming stores the solutions so that it does not need to recompute them again, it is a typical example of the classic trade-off between computational time and memory.

Dynamic programming technique should only be used to solve optimization problems with two properties: optimal substructure and overlapping subproblems [1, Sec. 15.3]. A problem has optimal substructure if an optimal solution to the problem consists of optimal solutions to the subproblems. Optimal substructure requires that the resources used to find the solutions to the subproblems are independent of each other. A problem has overlapping subproblems if the recursion to solve the problem leads to solving some subproblems multiple times.

Dynamic programming technique involves four steps [1, Chapter 15]

  - Characterize the structure of an optimal solution
  - From the previous analysis, derive a recursion definition for the value of an optimal solution
  - From the previous recursion definition, derive an algorithm to compute the value of an optimal solution.
  - Construct an optimal solution, if one is needed (note that the previous steps only try to find the value of an optimal solution)

There are two approaches to implementing dynamic programming algorithms:

  - Top-down: The algorithm is implemented as a normal recursive algorithm, but when a solution to a subproblem is found, it is saved so that it can be looked up later when the same subproblem is encountered.
  - Bottom-up: The subproblems are solved in the order of their sizes with the smallest first, so that when a subproblem is encountered, it is guaranteed that all of its sub-subproblems are already solved.

## Greedy heuristics

# References

[1] Introduction to algorithms, 3rd
