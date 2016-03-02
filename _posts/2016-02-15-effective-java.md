---
layout: post
title: Effective Java
---

# Reflection
- Pros:
  - Provides a programmatic way to introspect a class
  - Provides an "abnormal" and unique way to
    - Invoke class methods and constructors
    - Access and modify class fields
- Cons:
  - Performance overhead over non-reflective counterparts
  - Loss of compile-time type checking
  - Exposure of internals, e.g., `private` fields or methods can be accessed and modified
- General rule
  - Should always try to avoid using reflection in normal applications
  - If it is unavoidable, reflection should be used very cautiously. One acceptable way of using reflection is to create an instance, but after that normal invocation should be used on the created instance.
- References
  - [1] Item 53, Effective Java 2nd, Joshua Bloch
  - [2] https://docs.oracle.com/javase/tutorial/reflect/
  - [3] http://www.javaworld.com/article/2077015/java-se/take-an-in-depth-look-at-the-java-reflection-api.html
