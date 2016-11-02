## Introduction

Generics is an enhancement to the Java type system that was introduced in [Java 5](http://docs.oracle.com/javase/1.5.0/docs/relnotes/features.html#generics) to support [generic programming](https://en.wikipedia.org/wiki/Generic_programming) in a type-safe manner via [parametric polymorphism](https://en.wikipedia.org/wiki/Parametric_polymorphism).

The main benefits of using generics:

  - Make parametric polymorphism more convenient

  - Provide stronger compile-time type checking

  ```java
  // without generics
  List strings = new ArrayList();
  strings.add("a"); // unchecked warning
  strings.add(1); // unchecked warning

  // with generics
  List<String> genericStrings = new ArrayList<>();
  genericStrings.add("a");
  // genericStrings.add(1); // compile error
  ```

  - Remove boilerplate casts

  ```java
  // without generics
  List strings = new ArrayList();
  strings.add("a");
  String s1 = (String) strings.get(0);

  // with generics
  List<String> genericStrings = new ArrayList<>();
  genericStrings.add("a");
  String s2 = genericStrings.get(0);
  ```

## Subtyping

The [subtyping](https://en.wikipedia.org/wiki/Subtyping) relationship here is defined based on the [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle).

There are two ways to define subtyping relationship on generic classes: by [inheritance](https://docs.oracle.com/javase/tutorial/java/generics/inheritance.html) and by [wildcards](https://docs.oracle.com/javase/tutorial/java/generics/wildcards.html).

### Subtyping via inheritance

A generic class can be defined to be a subtype of a normal class.

  ```java
  class NormalClass {}
  class GenericClass<T> extends NormalClass {} // ok
  ```

A generic class can also be defined to be a subtype of another generic class, given that the parameterized types of the superclass are all matched.

  ```java
  class GenericClass1<E> {}
  class GenericClass2<T> extends GenericClass1<T> {} // match completely
  class GenericClass3<T, S> extends GenericClass1<T> {} // match completely

  class GenericClass4<E, F> {}
  class GenericClass5<T> extends GenericClass4<T, String> {} // match completely by subclass's parameterized type and normal types
  ```

### Subtyping via wildcards

Wildcards are used to specify the bounds of the parameterized types of a generic type. There are three ways to use wildcards.

| Usage | Description |
|:-----:|:-----------:|
| `<? extends E>` | either `E` or any subtype of `E` |
| `<? super E>` | either `E` or any supertype of `E` |
| `<?>` | any type |
{: .table}

A generic class is substitutable for another generic class if the relationships between their parameterized types are appropriately specified by the wildcard (`?`). Let `R` denote a raw type, then:

  - `R<S>` is substitutable for `R<? extends T>`, for any `S` that is either `T` or subtype of `T`
  - `R<S>` is substitutable for `R<? super T>`, for any `S` that is either `T` or supertype of `T`
  - `R<S>` is substitutable for `R<?>` for any type `S`

For example:

  ```java
  List<Integer> ints = new ArrayList<>();
  List<? extends Number> numberInts = ints;

  List<Double> doubles = new ArrayList<>();
  List<? extends Number> numberDoubles = doubles;

  List<Number> numbers = new ArrayList<>();
  List<? super Integer> numbers2 = numbers;
  List<? super Double> numbers3 = numbers;

  List<?> any = ints;
  any = doubles;
  any = numbers;
  ```

## Restrictions

### Generic types are invariant

Generic types are [invariant](https://en.wikipedia.org/wiki/Covariance_and_contravariance_(computer_science)#Use-site_variance_annotations_.28wildcards.29) by default. In other words, the subtyping relationship between `R<A>` and `R<B>` is regardless of that between `A` and `B`. For example, `List<Number>` and `List<Integer>` are not related at all, even though `Integer` is a subtype of `Number`.

However, if combined with wildcards, generic types can be made covariant or contravariant. The wildcard usage `<? extends T>` makes generic types covariant because it preserves the type order of the parameterized type, i.e., if `S` is a subtype of `T`, then `R<S>` is a subtype of `R<? extends T>` because `R<S>` is substitutable for `R<? extends T>`. On the other hand, `<? super T>` makes generic types contravariant because it reverses the type order, i.e., if `S` is a supertype of `T`, then `R<S>` is a subtype of `R<? super T>`.

### Type erasure



## Best practices with generics

## The get and put principle

## Checked collections

- What? Why? (DONE)
- Subtyping (DONE)
- Restrictions on generics
  - Invariant (DONE)
  - Type erasure
  - No arrays with generics
- Bounds (IGNORED)
- Reification
- Wildcards (DONE)
- Bridges (IGNORED)
- Best practices with generics
  - The get and put principle

## References

[1] [Java generics](https://amzn.com/0596527756)

[2] [Thinking in Java](https://amzn.com/0131872486)

[3] [Effective java](https://amzn.com/0321356683)

[4] [Oracle Java tutorials: Generics](https://docs.oracle.com/javase/tutorial/java/generics/index.html)

[5] http://www.javaworld.com/article/2076275/core-java/behold-the-power-of-parametric-polymorphism.html
