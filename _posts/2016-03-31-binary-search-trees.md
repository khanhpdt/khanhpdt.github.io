---
layout: post
title: Binary search trees
tags: [data-structures]
---

## Terminology

__binary tree__ a tree where each node has at most two children
__height of a node__ the length (or the number of edges) of the longest downward path from the node to a leaf
__height of tree__ the height of its root
__depth of a node__ the length of the upward path from the node to the root
__level of a node__ = 1 + depth of the node
__full binary tree__ a binary tree whose nodes have either 0 or 2 children
__complete binary tree__ a binary tree where all levels except the last one are completely filled; the last level is filled from the left

## Binary search tree

A binary search tree (BST) is a binary tree where each node is larger than or equal to all the nodes in its left subtree and smaller than or equal to all the nodes in its right subtree. In other words, for each node `y` in a BST, `x <= y <= z`, where `x` is any node in `y`'s left subtree and `z` is any node in `y`'s right subtree. This property is also known as the binary-search-tree property.

<!--break-->

The main advantage of BSTs is that they speed up the basic operations by exploiting the binary-search-tree property. Specifically, all the operations to search, to find min or max, to find sucessor or predecessor, and to insert or delete take `O(h)` time, where `h` is the tree height. Without the binary-search-tree property, all of those operations, except insertion, take `O(n)` time as all the nodes need to be checked.

## Binary-tree traversals

| Traversal type | Order |
| --------- | ----- |
| pre-order | `y` -> `y`'s left subtree -> `y`'s right subtree |
| in-order | `y`'s left subtree -> `y` -> `y`'s right subtree |
| post-order | `y`'s left subtree -> `y`'s right subtree -> `y` |

These traversals can be implemented as either recursive or iterative algorithms. Using recursive algorithms usually leads to more concise and intuitive solutions, but in the programming languages where recursive calls are not optimized (e.g., Java), these solutions consume a lot of stack memory as each recursive call adds a new method frame to the stack. This can even cause stack overflow if there are too many such calls. 

On the other hand, solutions by iterative algorithms are more complicated as iterative approach does not come naturally with the traversal problem. During traversing, iterative algorithms usually need to save the current state of the traversal so that it can backtrack to that state to continue with the nodes in the correct order. This backtracking can be implemented by using an additional data structure (e.g., stack). The only advantage of using iterative algorithms is that they use stack memory much less than the recursive algorithms, but this advantage is only valid when the programming language in use does not support recursion well.

## Balanced BSTs

A balanced BST is a BST which automatically adjusts itself to keep the heights of its left and right branches differ by only a certain amount. This adjustment is to keep the nodes well-distributed, thereby preventing the unbalanced increase in the subtrees' heights. The two well-known examples of balanced BSTs are red-black and AVL trees.

The main advantage of balanced BSTs is the significant improvement on the tree's height in the worst case, leading to the improvement on the performances of basic operations, e.g., search, min, and max, whose performances are linear to the tree's height. For example, the height of a normal BST in the worst case is equal to the number of the tree nodes, whereas that of a red-black tree is always upper-bounded by `2*lg(n+1)`, where `n` is the number of the internal nodes in the tree [2, Lemma 13.1]. Thus, the worst-case complexities of the basic operations on red-black trees are reduced from `O(n)` to `O(lgn)`.

## Source code

- [github/trees](https://github.com/khanhpdt/datastructures-algorithms/tree/master/data-structures/src/main/java/vn/khanhpdt/playgrounds/datastructures/trees)
- [github/tree-traversals](https://github.com/khanhpdt/datastructures-algorithms/tree/master/algorithms/src/main/java/vn/khanhpdt/playgrounds/algorithms/trees)

## Further readings

[1] [Data structures and algorithms in Java](http://www.amazon.com/Data-Structures-Algorithms-Java-2nd/dp/0672324539/ref=sr_1_4?s=books&ie=UTF8&qid=1461439850&sr=1-4&keywords=data+structures+and+algorithms+in+java)
[2] [Introduction to algorithms](http://www.amazon.com/Introduction-Algorithms-3rd-MIT-Press/dp/0262033844/ref=sr_1_1?s=books&ie=UTF8&qid=1461439930&sr=1-1&keywords=introduction+to+algorithms)
[3] [Algorithms](http://www.amazon.com/Algorithms-4th-Robert-Sedgewick/dp/032157351X/ref=sr_1_2?ie=UTF8&qid=1461440135&sr=8-2&keywords=algorithms)
[4] [https://en.wikipedia.org/wiki/Tree_traversal](https://en.wikipedia.org/wiki/Tree_traversal)
[5] [http://www.refactoring.com/catalog/replaceRecursionWithIteration.html](http://www.refactoring.com/catalog/replaceRecursionWithIteration.html)
[6] [Looping versus recursion for improved application performance](http://www.ibm.com/developerworks/websphere/techjournal/1307_col_paskin/1307_col_paskin.html)
[7] [Self-balancing binary search tree](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)
