---
layout: post
title: Strategy pattern
excerpt: ""
categories: articles
tags: [design-patterns]
---

## Intent

- Defines a family of algorithms (or strategies) and encapsulates them from the clients.

## Structure

![strategy-pattern-structure]({{ site.url }}/images/patterns/design-patterns/strategy/structure.png)

- Each strategy is encapsulated in each own class.
- The clients are insulated from the strategy details, and only need to know which strategy it should use.

## Applicability

Use this pattern when:

- There are multiple variants of an algorithm and you want to decouple the client from the algorithm details. The reasons for decoupling might be that you don't want to complicate the client, or the algorithm needs some data that the client cannot reach, or it's more likely that the algorithm details will change and you don't want the change to affect the client.
- A conditional statement appears _multiple_ times, and you want to replace them by using polymorphism with the strategy hierarchy.

## Risks

- Might complicate the code base, as this pattern needs a new class hierarchy.
- Increased number of objects.
- It's not gonna be easy to design the strategy interface in case the algorithm variants needs different kinds of input. For example, when adding a new strategy to an existing strategy hierarchy and that new one needs more data than the existing ones, then either we have to change the whole strategy interface or we have to introduce the new data to the strategy request (if it's an DTO).
- There might be communication overhead for certain algorithms which do not make use of all the input data, which is defined to satisfy _all_ the algorithms.

## References

- Strategy, GOF book
