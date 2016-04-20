---
layout: post
title: Visitor pattern
tags: [design-patterns]
---

## Intent

- Defines new operations for a class hierarchy _without_ modifying the hierarchy.

## Structure

![visitor-pattern-structure]({{ site.url }}/assets/imgs/patterns/design-patterns/visitor/structure.png)

- In the diagram, the `accept(Visitor v)` method just simply calls `v.visit(this)`, which implements the necessary operation on the given `Component`. This is the _double dispatch_ technique, where the result of the call depends on the request and the types of _two_ receivers.
<!--break-->
- New operations for the `Component` class hierarchy can be created by adding new `Visitor`. Thus, it's not necessary to modify the `Component` class hierarchy to define its new operations.

# Applicability

This pattern should be used when:

- The class hierarchy rarely changes, while its operations usually does. This is because adding new operations can be simply done by adding new visitors. On the other hand, adding new classes into the hierarchy leads to adding new `visit()` method to the `Visitor` interface, which leads to modifying _all_ the existing visitors.

# Risks

- The pattern is quite complicated to understand. Using this pattern might make it hard for other team members to get familiar with the code.
- If this pattern is used with the Composite pattern and the Composite contains a cycle in it, the accept-visit loop might be repeated forever.

# Implementation

- [github/Visitor](https://github.com/khanhpdt/design-patterns/tree/master/src/main/java/org/khanhpdt/designpatterns/visitor) for an example.

# References

- Visitor, GOF book
- Visitor, Chapter 29, Design Patterns In Java
