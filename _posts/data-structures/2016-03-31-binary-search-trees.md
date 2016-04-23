---
layout: post
title: Binary search trees
tags: [data-structures]
---

## Definitions

A tree is a collection of nodes and edges without any cycle.

A binary tree is a tree where each node has at most two edges.

A binary search tree (BST) is a binary tree where the key of each node is larger than or equal to the keys of all the nodes in that node's left subtree and smaller than or equal to the keys of all the nodes in that node's right subtree. In other words, if the key of node `y` is `y.key`, then `x.key <= y.key <= z.key` for any node `x` in `y`'s left subtree and any node `z` in `y`'s right subtree.

<!--break-->

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

## Source code

- [github/BST](https://github.com/khanhpdt/datastructures-algorithms/blob/master/data-structures/src/main/java/org/khanhpdt/playgrounds/datastructures/trees/BinarySearchTree.java).

## References

[1] [Data structures and algorithms in Java](http://www.amazon.com/Data-Structures-Algorithms-Java-2nd/dp/0672324539/ref=sr_1_4?s=books&ie=UTF8&qid=1461439850&sr=1-4&keywords=data+structures+and+algorithms+in+java)
[2] [Introduction to algorithms](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)
[3] [Algorithms](http://www.amazon.com/Algorithms-4th-Robert-Sedgewick/dp/032157351X/ref=sr_1_2?ie=UTF8&qid=1461440135&sr=8-2&keywords=algorithms)
[4] [https://en.wikipedia.org/wiki/Tree_traversal](https://en.wikipedia.org/wiki/Tree_traversal)
[5] [http://www.refactoring.com/catalog/replaceRecursionWithIteration.html](http://www.refactoring.com/catalog/replaceRecursionWithIteration.html)
[6] [Looping versus recursion for improved application performance](http://www.ibm.com/developerworks/websphere/techjournal/1307_col_paskin/1307_col_paskin.html)
[7] [Self-balancing binary search tree](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)
