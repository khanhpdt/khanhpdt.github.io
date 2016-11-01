---
layout: post
title: Bitwise operators in Java
excerpt: ""
categories: articles
tags: [java]
---

Bitwise operators operate on its operands in a bit-by-bit pattern. These operators only accept operands of integral types, including `byte, char, short, int, long`.

## Operators OR, AND, and XOR

Before performing these operators `&, |, ^`, binary numeric promotion is applied on the operands [2]. If one of the operands is of type `long`, the other is promoted to `long`; otherwise, both operands are converted to `int`. The type of those operator expressons is the promoted type.

It should also be noticed that when these operators `&, |, ^` are used on `boolean` values, they are called logical operators [2], and that short-circuiting is not supported in this case.

### OR

Rule: `x | y == 1` if `x` or `y` is `1`.

Example:

```java
0b1010111 | 0b1000010 == 0b1010111
```

### AND

Rule: `x & y == 1` if both `x` and `y` are `1`.

Example:

```java
0b1010111 & 0b1000010 == 0b1000010
```

### XOR

Rule: `x ^ y == 1` if either `x` or `y` is `1` but not both.

Example:

```java
0b1010111 ^ 0b1000010 == 0b10101
```

## Complement operator

The result of `~ x` is obtained by flipping all the bits in `x`.

Example:

```java
~ 0b1010111 == 0b11111111111111111111111110101000
```

Note that unary numeric promotion is applied before this operator is performed. If the operand is of type `long`, it remains unchanged; otherwise, it is converted to `int`. This promoted type is also the type of the result.

## Shift operators

Before performing these operators, unary numeric promotion is applied on each operand. As stated before, in unary numeric promotion, an operand remains unchanged if its type if `long`, otherwise it is converted to `int`. The type of these shift expressions is the promoted type of the left operand.

### Left shift

The result of `x << y` is `x` after shifting its bits `y` positions to the left and then inserting zeroes at the lower-order bits.

Example:

```java
0b1010111 << 3 == 0b1010111000
```

### Signed right shift

The result of `x >> y` is `x` after shifting its bits `y` positions to the right and then inserting at the higher-order bits zeroes if `x > 0` or ones if `x < 0`.

Example:

```java
// 0b10101 = 21
0b10101 >> 3 == 0b10
// 0b11111111111111111111111110011011 = -101
0b11111111111111111111111110011011 >> 3 == 0b11111111111111111111111111110011
```

### Unsigned right shift

Same as `>>` except that the inserted bits are always zeroes.

Example:

```java
0b11111111111111111111111110011011 >>> 3 == 0b00011111111111111111111111110011
```

## Idioms

Let `n` denote an integer, and `b` denote the `i`th bit in `n` couting from the LSB.

  * Clear all but `b`: `n & (1 << i)`

```java
0b11111 & (1 << 2) == 0b00100
```

  * Turn `b` off: `n & (~ (1 << i))`

```java
0b1111 & (~(1 << 2)) == 0b11011
```

  * Turn `b` on: `n | (1 << i)`

```java
0b11000 | (1 << 2) == 0b11100
```

  * Set `b` to bit `a`: `(n & (~ (1 << i))) | (a << i)`

```java
0b11111 & ((~ (1 << 2)) | (0 << 2)) == 0b11011
0b11011 & ((~ (1 << 2)) | (1 << 2)) == 0b11111
```

  * Create a bit mask with `i` trailing ones: `(1 << i) - 1`

```java
(1 << 5) - 1 == 0b11111
(1 << 10) - 1 == 0b1111111111
```

  * Clear the right most bit `1`: `n & (n - 1)`

```java
0b111011_1 & (0b111011_1 - 1) == 0b111011_0
0b11101_100 & (0b11101_100 -1) == 0b11101_000
0b1_000000 & (0b1_000000 - 1) == 0
```

## Further reading

[1] Bitwise operators, Thinking in Java, 4th

[2] [Bitwise and logical operators](https://docs.oracle.com/javase/specs/jls/se8/html/jls-15.html#jls-15.22)
