# Algorithm analysis

Analyzing an algorithm is to determine how much resources the algorithm needs. The resources might be either memory usage, or computational time, or network resources. However, computational time is the desired in most of the cases.

## The RAM model

[2.1, 2]

## Computational time

Computational time is the time needed for an algorithm to do its processing.

The computational time of an algorithm depends on two properties: the size and the characteristics of its input. For example, the computational time of an insertion sort algorithm increases as the number of items increases, and given a number of items to be sorted, the algorithm takes the longest time when the items are in the reverse order of the desired order.

## Order of growth (or Rate of growth)

The order of growth of an algorithm tells us how quickly the computational time of the algorithm increases with the size of the input of the algorithm.

Order of growth is usually represented by asymptotic notations, which involve only the leading term (excluding its coefficient) of the computational time formula.

![asymptotic-notations](/assets/imgs/algorithms/asymptotic-notations.png)
(Source: Fig 3.1 [1])

Several reasons why asymptotic notations are used to represent the order of growth:

  - They are easier to derive than the exact computational time.
  - Even though they are not so accurate for small input size, their accuracy increases as the input size increases. This is because, for large input size, the contribution of the leading term becomes more significant compared to the others. Asymptotic notations fit well into the situations where it is interested to know how an algorithm performs as the input size increases.
  - They make it simple to compare the computational time of different algorithm.

## Worst-case analysis

The worst-case computational time lets us know the longest time an algorithm might take. Thus, if a worst-case running time of an algorithm is `T`, then we know for sure that the algorithm always finishes before `T` time.

## Average-case analysis

## Amortized analysis

# Design techniques

## Divide-and-conquer

- 3 steps
  - Divide
  - Conquer
  - Combine

- Recurrences
  - The substitution method
  - The recursion tree method
  - The master method



# References
[1] Chapter 2, 3, and 4, Introduction to algorithms, 3rd
[2] The algorithm design manual
