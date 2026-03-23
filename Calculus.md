---
pure:
---
Calculus studies limits(how things act as a variable converges to a specific value), derivatives(The instantaneous rate of change of a function at a specific point along a specific direction), and integrals(a way of calculating the accumulated area underneath the curve at a specific point) 

# Derivative techniques
There are a variety of ways to take derivatives and here are a few of them. Most of them work for multivariable functions 

## Linearity of the Derivative
This is the exact same form of linearity of that of a linear transform, or of expected value. It states that 
$$
dx(\alpha f(x)+\beta g(x))=\alpha f^{\prime}(x) +\beta g^{\prime}(x)
$$

## Power Rule 
The power rule is by far the simplest derivative technique, it simply states that 
$$
x^n dx=nx^{n-1}
$$

## Chain Rule 
This rule states that 
$$
f(g(x))dx=f^{\prime}(g(x))g^{\prime}(x)
$$
often its easy to forget to use this rule when you need to like $e^{5x}dx = 5e^{5x}$ 

## Product Rule
This rule states that 
$$
f(x)g(x)dx=f^{\prime}(x)g(x)+f(x)g^{\prime}(x)
$$

## Quotient Rule
This rule can be derived using the product rule. But at the time I don't want to write the proof for it. It states that
$$
\frac{f(x)}{g(x)}dx=\frac{f^{\prime}(x)g(x)+f(x)g^{\prime}(x)}{[g(x)]^2}
$$

