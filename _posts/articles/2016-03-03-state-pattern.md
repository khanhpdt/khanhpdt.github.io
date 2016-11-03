---
layout: post
title: State pattern
excerpt: ""
categories: articles
tags: [design-patterns]
modified: 2016-11-03
---

## Intent

- Allow an object to adjust its behavior based on its state

## Structure

![state-pattern-structure]({{ site.url }}/images/patterns/design-patterns/state/structure.png)

- `Client` does not need to know about the `Object` states as well as the associations between the states and the object behaviors.
- The behaviors are now handled by the corresponding `State` objects.
- The state transition method can be centralized in the `Object` or distributed over the concrete states.
- The `Object` can also pass itself as an argument to the operations of `State` objects. This helps the state objects to access the information in the `Object`.

## Applicable contexts

- You want to modify the object's behavior at run-time depending on its state.
- You want to eliminate the duplications of the conditional clause on the object's states currently scatterring over different places.
- You want to emphasize the transitions between states.
- You want to emphasize the associations between states and behaviors.
- There are complicated logics revolving around the object states, and each of those states can transform to another state.

## Risks

- Increase the number of classes, as each state is now a class itself
- Increase the number of objects, but this risk can be reduced by reusing the same instance of the state (if possible)
- More complicated code

## Example

- [github/State](https://github.com/khanhpdt/design-patterns/tree/master/src/main/java/vn/khanhpdt/playgrounds/designpatterns/state)

## References

[1] State,  [The GOF book](https://amzn.com/0201633612)
