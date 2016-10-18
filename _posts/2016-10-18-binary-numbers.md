---
layout: post
title: Binary numbers
tags:
  - number-system
  - binary-number
---

A binary number is a number whose representation is a combination of only two digits, `0` and `1`. For example, `01011001` and `010` are two binary numbers.

## Methods to represent signed binary numbers

There are three well-known methods to represent signed binary numbers: sign-magnitude, ones' complement, and two's complement.

### Sign-magnitude

This method allocates the most significant bit (MSB) for representing the sign and the other bits for the number magnitude. A number is negative if its MSB is `1` and positive otherwise. For example, `0101` represents `5`, whereas `1101` represents `-5`.

<!--break-->

Given `n` bits, the range of the numbers this method can handle is `(-(2^(n-1) - 1), 2^(n-1) - 1)`. 

It should be noted that this method yields two representations of zero. For example, given 4 bits, the two representations of zero are `1000` and `0000`.

### Ones' complement

A ones' complement of a binary number is the result of applying bitwise `NOT` operation on that binary number. For example, the ones' complement of `10010` is `01101`. Using this method, a negative binary number is the ones' complement of its positive counterpart. For example, in a 4-bit system, `0101` represents `5` and `1010` represents `-5`.

Similar to sign-magnitude, given `n` bits, the range of the numbers represented by this method is `(-(2^(n-1) - 1), 2^(n-1) - 1)`. 

There are also two presentations of zero using this method. For example, given 4 bits, the two representations of zero are `0000` and `1111`.

### Two's complement

A two's complement of a binary number of `n` bits is the result of subtracting the number from `2^n`. Since the sum of a binary number of `n` bits and its ones' complement is a number of `n` bits `1`, the two's complement of the binary number is also equal to the sum of its ones' complement and `1`. For example, the two's complement of `10101` is equal to `1 + 01010 = 01011`. Using this method, a negative binary number is the two's complement of its positive counterpart.

There are two ways to compute the two's complement of a binary number. The first one is mentioned above, which computes the two's complement by adding `1` to the ones' complement of the binary number. The second one is a bit more convenient for computing by hand. Specifically, it has two step: it finds the first `1` bit starting from the least significant bit, and then flips all the bits on the right of that `1` bits. For example, to find the two's complement of `10110`, this second approach keeps `10`, flips `101` into `010`, and finally gives the result of `01010`.

## Arithmetic

### Addition

Rules:

	0 + 0 = 0
	0 + 1 = 1 
	1 + 0 = 1 
	1 + 1 = 0, carry 1

Example:

	  1 1 1 1 1   (carried)
        0 1 1 0 1
	+   1 0 1 1 1
	  -----------
	= 1 0 0 1 0 0

### Subtraction

Rules:

	0 - 0 = 0
	0 - 1 = 1, borrow 1
	1 - 0 = 1
	1 - 1 = 0
	
Example:

	    1   1 1 1    (borrowed)
	  1 1 0 1 1 1 0
    -     1 0 1 1 1
	----------------
	= 1 0 1 0 1 1 1
	
Substraction can also be done by adding the substrahend to the two's complement of the minuend, i.e., `x - y = x + ((~y) + 1)`.

### Multiplication

Multiplication is performed similarly to that of decimal numbers, but with the following rules:

	x * 0 = 0
	x * 1 = x
	
Example:
	
	     1 0 1 1
       *     1 0
       ---------
         0 0 0 0
	+  1 0 1 1
	   ---------
	=  1 0 1 1 0

### Division

Division is performed similarly to that of decimal numbers.

Example: `11011/101` gives the quotient `101` and the remainder `10`.

    1 0 1) 1 1 0 1 1
         - 1 0 1      -> 1
           -----
               1 1    -> 0
	           1 1 1 
             - 1 0 1  -> 1
               -----
                 1 0
	
## Further reading

[1] [https://en.wikipedia.org/wiki/Binary_number](https://en.wikipedia.org/wiki/Binary_number)
[2] [http://www.electronics-tutorials.ws/binary/signed-binary-numbers.html](http://www.electronics-tutorials.ws/binary/signed-binary-numbers.html)
[3] [https://en.wikipedia.org/wiki/Signed_number_representations](https://en.wikipedia.org/wiki/Signed_number_representations)
