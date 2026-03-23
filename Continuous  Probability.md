---
tags:
  - Pure
---
Continuous distributions are different from discrete distributions in the way that the likely hood of getting a specific value is always zero. They are often different in the way that the CDF of a random variable pretty much always exists
1. The PDF of a continuous distribution always integrates to $1$ over the range $-\infty$ to $\infty$ 
The relationship between the PDF $f(x)$ and the CDF $F(x)$ is 
$$
	F(x)=\int_{-\infty}^x f(x)
$$

# Distributions
## Normal Distribution 
**Parameters:** $\mu$ and $\sigma$ are the only two parameters needed 
**Expected Value:** $\mu$ 
**Description:** This is considered an important distribution because according to the Central Limit Theorem a large sum of independent identical converges to the normal distribution. This is why if you have balls moving on down a Galton board each of the bars is following a binomial distribution, and then the sum of them of the balls follows the normal distribution 
**PDF:**
$$
\frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}
$$
**CDF:** 
	Does not exist kinda 

## Exponential 
**Parameters:** $\lambda >0$ 
**Expected Value:** $\frac{1}{\lambda}$ 
**Description:** This represents the distance between points in poisson process. This could be used to model the time until a patch of ground gets hit by a rain drop. Additionally this is the only distribution with the memoryless property. This means if you have been waiting $1000$ years you can expect to wait $1000+\frac{1}{\lambda}$ years before it happen 
**PDF:**
$$
\lambda e^{-\lambda x}
$$
**CDF:**
$$
1-e^{-\lambda x}
$$

## Uniform 
**Parameters:** $a$ and $b$ the bounds 
**Expected Value:** $\frac{a+b}{2}$  
**Description:** This distribution if as basic as it comes, but it is incredibly useful nonetheless. If a mod in a video game is going to spawn it probably is going to spawn in a uniform distribution 
**PDF:**
$$
\frac{1}{b-a}
$$
**CDF:**
$$
\frac{x-a}{b-a}
$$



