---
layout: post
title: Visitor pattern
excerpt: ""
categories: articles
tags: [design-patterns]
modified: 2016-11-03
---

## Intent

- Allow to define new operations for a class hierarchy _without_ modifying the hierarchy

## Structure

![visitor-pattern-structure]({{ site.url }}/images/patterns/design-patterns/visitor/structure.png)

- The concrete implementations of `accept(Visitor v)` methods only need to call `v.visit(this)`, then the callee `Visitor` will carry out the necessary operation on the caller `Component`. This is the _double dispatch_ technique, where the result of the call depends on the request and the types of _two_ receivers, e.g., `Component` and `Visitor` in this case.
- Each `Visitor` supports a specific group of operations on the `Component` class hierarchy. Thus, new group of operations can be added via new `Visitor` without changing the `Component` hierarchy at all.

# Applicable contexts

- A class hierarchy rarely changes, but its services usually do.

# Benefits

- Allow to extend the services of a whole class hierarchy without changing the hierarchy, because the extension can be done by adding new visitors
- Allow to modify the services of a whole class hierarchy without changing the hierarchy, because the modification can be done by adapting the corresponding visitors

# Risks

- The pattern is quite complicated to understand. Using this pattern might make it hard for other team members to get familiar with the code.
- Adding new classes to the hierarchy causes changes to the whole visitor hierarchy, because new classes require new `visit()` methods in the `Visitor` interface and thus in all the existing visitors
- If this pattern is used with the Composite pattern and the Composite contains a cycle in it, the accept-visit loop might be repeated forever.

# Example

- [github/Visitor](https://github.com/khanhpdt/design-patterns/tree/master/src/main/java/vn/khanhpdt/playgrounds/designpatterns/visitor)

# References

[1] Visitor, [The GOF book](https://amzn.com/0201633612)

[2] Visitor, Chapter 29, [Design Patterns In Java](https://amzn.com/0321333020)
