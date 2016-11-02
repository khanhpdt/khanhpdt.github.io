---
layout: post
title: Abstract Factory pattern
excerpt: ""
categories: articles
tags: [design-patterns]
---

## Intent

- Provides a single place to (dynamically) create a family of related objects.

## Structure

![abstract-factory-pattern-structure]({{ site.url }}/images/patterns/design-patterns/abstract-factory/structure.png)

In the diagram, `AbstractFactory` acts as the single place providing services to create two related products A and B. Users of those services, e.g., `Client`, do not need to know how the products are implemented or how they are created; instead, they only need to know the right factory for its need, which they might create themselves or receive from another source.

## Applicable contexts

- There are objects related to each other, each of which has different forms, and they are usually created together.
- You want to centralize the creation of some objects and to decouple that creation details from the users of those objects.

## Benefits

- Users of abstract factories are decoupled from the concrete implementations of the objects and the factories.
- Switch between groups of objects at run-time is simple, as it can be done by changing the factory.
- The related objects are guaranteed to be created and used together, preventing the users from mistakenly using unrelated objects from different groups.
- High cohesion. Factories are only responsible for creating objects, while users just need to choose which factories they need.

## Risks

- If there appears a new type of object, the abstract factory needs to add this object to the group of objects it can create, thus causing all the concrete factories to change.

## Implementation

- If there is only one group of related objects, the creations of those objects should be put into a single place, but it is not yet necessary to implement a full abstract factory pattern. Wait for the second group and then this pattern can be considered.

- In case the concrete objects do not conform to a common interface, e.g., the `ConcreteProductA1` and `ConcreteProductA2` are of different types, this pattern can use the Adapter pattern to resolve the problem.

## Example

- [github/AbstractFactory](https://github.com/khanhpdt/design-patterns/tree/master/src/main/java/vn/khanhpdt/playgrounds/designpatterns/abstractfactory)

## References

[1] Abstract Factory, [The GOF book](https://amzn.com/0201633612)

[2] Abstract Factory, [Design patterns explained](https://amzn.com/0321247140)
