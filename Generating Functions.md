---
tags:
  - Applied
---
Generating functions where the coefficient of $x^n$ encodes some useful power. Technically a generating function is not a polynomial but instead a power series(because it is infinite).
You may be initially confused by this but it actually makes sense think about if you have the set $\{1,...,10\}$ and you want to know how many combinations there are of three elements from this set that equal $7$. You can instead find the coefficient of $x^7$ in $(x+x^2+...+x^{10})^{3}$ 
Often you can use the properties of polynomials like $(a+b)^n=\Sigma_{r=0}^{m}\binom{n}{r}a^{r}b^{n-r}$ or $(1+x)^{n}=\Sigma_{r=0}^{n}\binom{n}{r}x^r$



An example of this is if you roll $4$ $12$ sided dice how many ways are there to get a sum of $24$ . We can start by simply writing out the generating function for this of $(x^1+x^2+...+x^{12})^4$ but we can simplify this even more rewriting it as $x^4(1+x^1+x^2+...+x^{11})^4$ we can then further rewrite the inner part as $x^4(\frac{1-x^{12}}{1-x})^4$. Further rewriting this again we find that if we can just calculate the coefficient of $x^{20}$ in the polynomial $(1-x^{12})^4(1-x)^{-4}$. Using the binomial theorem we can expand out

$(1-x^{12})^4=\binom{4}{0}(-x^{12})^0+\binom{4}{1}(-x^{12})^1+\binom{4}{2}(-x^{12})^2-\binom{4}{3}(-x^{12})^3+\binom{4}{4}(-x^{12})^4$, we can ignore most of that expansion and then only care about the coefficients of $x^0,x^{12}$ because those are important in making the coefficient of $x^{20}$. First we calculate the coefficient of $x^{20}$(because we can multiply by $1$ in the other part) in $(1-x)^{-4}$ which we find to $\binom{23}{3}$, and then we need to calculate the coefficient of $x^{12}$(because it can be multiplied by the $x^8$) and get $\binom{11}{3}$ and multiply it by the coefficient of $x^8$ which is $4$. Thus the coefficient of $x^{20}$ is $\binom{23}{3}-\binom{11}{3}\cdot 4=1111$