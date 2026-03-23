---
tags:
  - Pure
---
Combinatorics is the math of calculating the number of ways something can exist. For example the number of ways that you can roll $18$ with $6$ $6$-sided dice, or the number of ways to have a cube with one missing side

# Basic Enumeration
## Addition Rule(Or)
If you can split all possible outcomes into two non-overlapping groups, and there are  $n_1$ outcomes in the first group and  $n_2$ in the second, then the total number of outcomes is $n_1+n_2$. This can be done with any number of groups

An example might be for breakfast I have one fruit every day, and I have $4$ apples and $3$ oranges. This can be seen as doing one of the two possible tasks $\{\text{eat an apple},\text{eat an orange}\}$, and since I am doing only one of them I have $7$ possible breakfasts

## Product Rule(And)
Suppose that when you are determining the total number of outcomes, you identify $k$ different aspects that can vary. Then the total number of outcomes is the number of ways to do each aspect times the number of ways to do each other aspect

An example is if a password requires a uppercase letter and then after that a digit, we can view creating a password as first creating a uppercase letter, and then creating a digit. This means there are $26\times 10=260$ possible passwords

## Division Rule
If there are $n$ ways to do a task, but $d$ of them are equivalent for every single outcome, then the number of ways to do the task is $\frac{n}{d}$.

An example would be if you sit $4$ people at a circular table and two seatings are considered equivalent if they are rotationally equivalent, then there are $\frac{4\cdot 3\cdot 2\cdot 1}{4}$ seating arrangements

## Inclusion-Exclusion
This counts by using the property that $|A|+|B|-|A\cap B|=|A\cup B|$. This stems from the fact that just $|A|+|B|$ double counts everything they share. There are longer formulas for when there are more than two sets. 

An example would be strings of 1 and 0 with length 7 with either a starting 1 or endings with 000. We can find the number of bitstrings by finding the number of bit strings that start with 1 being 2^6, finding the number of bit strings ending in 000 which is 2^4, and then finding the number of strings that fall into both of these categories which is 2^3. Thus our final answer is 2^6+2^4-2^3​`


## Complement Rule 
This is the best rule in all of probability. If $A\subseteq X$ then $|A|=|X|-|A^c|$. This is useful when it is easier to count the complement rather than the whole set 



# Combinations/Permutations
A combination is a subset of elements(so order does not matter), where a permutation is a subset of elements in which order matters. 
## N choose K 
N choose K is represented using $\binom{n}{k}$. The formula for calculating it is below
$$
\binom{n}{k}=\frac{n!}{k!(n-k)!}
$$
This represents the number of combinations there are when choosing $k$ objects out of $n$ objects. This is derived because the number of permutations of $k$ elements from $n$ elements is $\frac{n!}{k!}$(think about every possible combinations and then $k!$ of them are equivalent)
# Counting Via Bijection 
If you can define a bijective function $f:A\rightarrow B$ then we know that $|A|=|B|$. This can somethings make counting sets way easier as you can define a bijection and then count what it bijected to(or use another persons proof to know you have properly counted it)
An example of this could be how many subsets are there for a given set $X$. This initially seems like a really daunting question but when you realize that you can define a bijection from $f:P(X)\rightarrow \{0,1\}^{|X|}$ where each element becomes a bit and is either $0$ or $1$ based off wether it is in the subset of not





[[Generating Functions]]

[[Explicit Formulas for Linear Recursion]]
