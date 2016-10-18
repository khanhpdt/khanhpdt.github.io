---
layout: post
title: Abstract Factory pattern
tags: [design-patterns]
---

## Intent

- Provides a single place to (dynamically) create a group of related objects.

## Structure

![abstract-factory-pattern-structure]({{ site.url }}/assets/imgs/patterns/design-patterns/abstract-factory/structure.png)

In the diagram, the `AbstractFactory` provides two methods for the `Client` to create two related products A and B. The `Client` does not need to know about the concrete types of the products it needs to creates, but instead it only needs to obtain the right factory for its need. It can get the factory either by creating the factory itself or by accepting the factory from an external source. Thus, this pattern also helps to decouple the clients from the implementations of the products and even the factories.

<!--break-->

## Applicability

This pattern can be used when

- There is a group of related objects and you want to centralize the creations of those objects. It is even more appropriate to use this pattern if each of the objects has multiple types.

## Benefits

- The client is decoupled from the concrete implementations of the objects and sometimes even the factories.
- It is simple to change a group of objects at run-time, which is simply done by changing the factory.
- The related objects are guaranteed to be created and thus used together, which prevents the clients from mistakenly using unrelated objects from different groups.
- High cohesion, because the factories is only responsible for creating objects, while the clients just need to worry which factories they need.

## Risks

- If there appears a new object, the abstract factory needs to add this object to the group of objects it currently supports. This causes all the concrete factories to change. which are currently supported by the abstract factory, then the abs

## Implementation

- If there is only one group of related objects, the creations of these objects should be put into a single place. But it is not yet necessary to implement a full abstract factory pattern. Wait for the second group and then this pattern can be used.

- In case the concrete objects do not conform to a common interface, e.g., the `ConcreteProductA1` and `ConcreteProductA2` are of different types, this pattern can use the Adapter pattern to resolve the problem.

- See [github/AbstractFactory](https://github.com/khanhpdt/design-patterns/tree/master/src/main/java/org/khanhpdt/designpatterns/abstractfactory) for an example.

## References

- Abstract Factory, GOF
- Abstract Factory, book "Design patterns explained: A new perspective on Object-Oriented design".
