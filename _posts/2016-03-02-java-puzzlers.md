---
layout: post
title: Java puzzlers
---

# Expressive Puzzlers

- Puzzle 2
  - Not all decimals can be represented exactly using binary floating-point

- Puzzle 8
  - Conditional operator
  - Should always avoid mixed-type computations

- Puzzle 9
  - Compound assignment (e.g., a += b) contains an implicit cast

# Puzzlers with characters

- Puzzle 13
  - String interning
  - Object comparison by equals() and ==

- Puzzle 18
  - The conversion between String and byte[] always involves using a specific charset

# Loopy puzzlers

- Puzzle 25
  - Postfix increment operator
  - Do not assign a variable more than once in a single expression

- Puzzle 28
  - Infinity
  - Floating-point operations return the floating-point value that is closest to their exact mathematical result.
  - Binary floating point arithmetics in Java

# Exceptional puzzlers

- Puzzle 36
  - The try statement 14.20 (Java Language Specification Java SE 7 (JLS7))

- Puzzle 37
  - Exception checking 11.2.3 (JLS7)

- Puzzle 38
  - Compile-time checking of exceptions 11.2 JLS7

    > When interfaces are involved, more than one method declaration may be overridden by a single overriding declaration. In this case, the overriding declaration must have a throws clause that is compatible with all the overridden declarations (§9.4.1).

- Puzzle 39
  - The System.exit method halts the execution of the current thread and all others dead in their tracks.

- Puzzle 40
  - Initialization of classes and interfaces 12.4 JLS7

- Puzzle 42
  - & and | can be used as && and || for boolean values, but they do not support short-circuit evaluation.

- Puzzle 43
  - It's possible that an undeclared exception can be thrown out. Examples:
    - newInstance()
  - Generics
    - Java exception checking is a compile-time facility, not a JVM feature.

# Classy puzzlers

- Puzzle 46
  - If more than one methods are applicable to an invocation, the most specific one is chosen.

- Puzzle 47
  - Static fields are shared by their declaring class and any _subclasses_.

- Puzzle 48
  - No dynamic dispatch on static methods (15.12.4.4 JLS7)

- Puzzle 49
  - The static initializers and class variable initializers are executed in textual order (12.4.1 JLS7)
  - Be very careful of circularity in class initialization

- Puzzle 50
  - instanceof and cast operators
    - `null` is a subtype of every type. However, `null instanceof Type` always returns false.
	- `instanceof` requires two operands must be in the same hierarchy. Otherwise, there'll be compile errors.
	- cast operator throws exception at run-time if the types are not convertable.

- Puzzle 51
  - Be very careful of circularity in class instance initialization
  - Should never call overridable (especially overridden) methods in constructors

- Puzzle 52
  - Be consistent: either use eager or lazy initialization, not both
  - Default values are set in the preparation phase, while the field initializers are executed in the initialization phase, which occurs after the preparation phase. For more details, see [JVM Startup](http://docs.oracle.com/javase/specs/jls/se8/html/jls-12.html#jls-12.1)

- Puzzle 53
  - From [JLS8](http://docs.oracle.com/javase/specs/jls/se8/html/jls-8.html#jls-8.8.7)

    > If a constructor body does not begin with an explicit constructor invocation and the constructor being declared is not part of the primordial class Object, then the constructor body implicitly begins with a superclass constructor invocation "super();"
  - Private constructor capture pattern
    - Workaround to be able to do both things: passing a value to the superclass constructor, while also storing the value at the class itself. Without this pattern, doing these two things is not possible due to rules on constructors.

- Puzzle 54
