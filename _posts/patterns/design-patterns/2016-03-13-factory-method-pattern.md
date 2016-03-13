---
layout: post
title: Factory Method pattern
tags: [design-patterns]
---

# Intent

- Defers object creations to subclasses.

# Structure

![abstract-factory-pattern-structure]({{ site.url }}/assets/imgs/patterns/design-patterns/factory-method/structure.png)

In the diagram, the `SuperClass` defines a method to create a `Product`. The method can be an actual implementation, in which case it acts as the default implementation. If any subclass needs to create another `Product` rather than the default, it can override the default implementation to create the desired `Product`. Alternatively, the method can be an abstract method to enforce the subclasses to define the methods themselves.

# Applicability

This pattern can be used when

- There are two class hierarchies and objects of one of the hierarchy need to use the objects of the other.
- The class does not know exactly which object to instantiate, but its subclasses do.
- You want to defer the object instantiation to the subclasses for some other reasons.

# Implementation

- See [github/AbstractFactory](https://github.com/khanhpdt/design-patterns/tree/master/src/main/java/org/khanhpdt/designpatterns/factorymethod) for an example.

# Reference

- Factory method, GOF
