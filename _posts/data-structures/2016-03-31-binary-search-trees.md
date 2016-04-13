---
layout: post
title: Binary search trees
tags: [data-structures]
---

## Definitions

A tree is a collection of nodes and edges without any cycle.

A binary tree is a tree where each node has at most two edges.

A binary search tree (BST) is a binary tree where the key of each node is larger than or equal to the keys of all the nodes in that node's left subtree and smaller than or equal to the keys of all the nodes in that node's right subtree. In other words, if the key of node `y` is `y.key`, then `x.key <= y.key <= z.key` for any node `x` in `y`'s left subtree and any node `z` in `y`'s right subtree.

## Binary tree traversals

- In-order traversals

  A node is visited between the visits of its subtrees: Visit node's left subtree -> Visit node -> Visit node's right subtree.

- Pre-order traversals

  A node is visited before visiting its subtrees: Visit node -> Visit node's left subtree -> Visit node's right subtree.

- Post-order traversals

  A node is visited after visiting its subtrees: Visit node's left subtree -> Visit node's right subtree -> Visit node.

### Implementation notes

The traversals can be implemented by either recursion or iteration.

Recursion offers a more concise solution, but it demands more stack memory as each recursive method call adds a new method frame to the stack. It might even cause stack overflow if the number of recursions is sufficiently large.

If using iteration, a manual data structure stack is necessary to support the inevitable backtracking during the traversals.

## Balanced BSTs

A balanced BST is a BST which automatically adjusts itself so that the heights of its left and right branches differ by only a certain amount. By doing this, its height is kept to a small value.

Two well-known examples of balanced BSTs are red-black and AVL trees.

Because the basic operations on a BST depend on its height, a balanced BST offers a better performance than the normal one in the worst case. More specifically, basic operations on BSTs run in `O(h)` time. More specifically, in the worst case, the height of a normal BST can be the same as the number of nodes, but the height of a red-black tree is always upper-bounded by `2*lg(n+1)`, where `n` is the number of the internal nodes in the tree [2, Lemma 13.1].

## Code samples

- See [github/BST](https://github.com/khanhpdt/java-playground/tree/master/src/main/java/org/khanhpdt/javaplayground/datastructures/trees).

## References

[1] Data structures and algorithms, 2nd, SAMS
[2] Chapter 12 and 13, Introduction to algorithms, 3rd
[3] Algorithms, 4th
[4] https://en.wikipedia.org/wiki/Tree_traversal
[5] http://www.refactoring.com/catalog/replaceRecursionWithIteration.html
[6] [Looping versus recursion for improved application performance](http://www.ibm.com/developerworks/websphere/techjournal/1307_col_paskin/1307_col_paskin.html)
[7] [Self-balancing binary search tree](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)
