## 8.4.5
Suppose that the random variables $X_1$ and $X_2$ are independent and that each has the normal distribution with mean $0$ and variance $σ^2$. Determine the value of $P \frac{(X_1+X_2)^2}{(X_1-X_2)^2} <4$ 

Note that $X_1+X_2$ and $X_1 - X_2$ have the same variance because both $X_1$ and $X_2$ are symetric.
Thus we can rewrite the inequality as $-2\leq \frac{\sigma}{\sigma} \frac{X_1+X_2}{X_1-X_2}\leq 2$ which is a normal distribution divided by a standard normal distribution divided by another standard normal which is an example of the standard normal distribution. This is the t distribution with $1$ degree of freedom which you can then use to solve $P \frac{(X_1+X_2)^2}{(X_1-X_2)^2} <4 =P(-2\leq T_1 \leq 2)$   

## 8.4.6
In Example $8.2.3$, suppose that we will observe $n = 20$ cheese chunks with lactic acid concen-  
trations $X_1, . . . , X_{20}$. Find a number $c$ so that  $P(\bar{X}_{20} ≤ μ + cσ′) = 0.95$. 
We want to find $P(\bar{X}_{20} \leq \mu +c \sigma ^{\prime})=0.95$ and we know that $n^{1/2}(\bar{X}_n - \mu)/\sigma^{\prime} = t_{n-1}$ 
$P(U \leq B)=0.95$
 We can calculate $c=\frac{1.729}{\sqrt{20}}$ . 
## 8.5.2
Suppose that a random sample of eight observations is taken from the normal distribution with unknown mean $μ$ and unknown variance $σ^2$, and that the observed values are $3.1, 3.5, 2.6, 3.4, 3.8, 3.0, 2.9,$ and $2.2$. Find the shortest confidence interval for $μ$ with each of the following three confidence coefficients: (a) $0.90$, (b) $0.95$, and (c) $0.99$.

$A = \bar{X}_n - T^{-1}_{n-1}(\frac{1+\gamma}{2})\frac{\sigma^{\prime}}{\sqrt{n}}$ 
$B = \bar{X}_n + T^{-1}_{n-1}(\frac{1+\gamma}{2})\frac{\sigma^{\prime}}{\sqrt{n}}$
Where all of these values can be easily calculated and inverse $T$ distribution can be calculated to find all values of $A$ and $B$ for different confidence coefficients 

## 8.5.4
Suppose that $X_1, . . . , X_n$ form a random sample from the normal distribution with unknown mean $μ$ and known variance $σ^2$. How large a random sample must be taken in order that there will be a confidence interval for $μ$ with confidence coefficient $0.95$ and length less than $0.01σ$ ?

A normal 95% confidence interval is $\bar{X}\pm \text{norm}(0.975)\frac{\sigma}{\sqrt{n}}$ so the length is $2\text{norm}(0.975) \frac{\sigma}{\sqrt{n}}$ and we want $2\text{norm}(0.975) \frac{\sigma}{\sqrt{n}}\leq 0.01\sigma$ so we just need to rearrange until we can isolate $n$

The sigmas can be canceled by dividing by sigma resulting in $2\text{norm}(0.975)/\sqrt{n}\leq 0.01$ or $2\text{norm}(0.975)/0.01\leq \sqrt{n}$ which rounding is $400\leq \sqrt{n}$ or $n\geq 400^2$
 

## 8.5.6
Suppose that $X_1,...,X_n$ form a random sample from the exponential distribution with unknown mean $\mu$. Describe a method for constructing a confidence interval with with a specified confidence coefficient $\gamma$. 

Note that $\Sigma X_i \sim \text{Gamma}(n,\frac{1}{\mu})$. Further $\frac{1}{\mu}\Sigma X_i \sim \text{Gamma}(n,1)$ 
Note that $P(\frac{1}{\mu}\Sigma X_i \leq c_2)$ is the  CDF of Gamma which we can use to solve for $c_2$ using $P(\frac{1}{\mu}\Sigma X_i\leq c_2)=\gamma + \frac{1-\gamma}{2}$ and the inverse CDF of gamma. We can do a similar process for $c_1$ but instead with $1-$ the cdf of gamma and $\gamma - \frac{1-\gamma}{2}$

## 8.7.2
Suppose that $X$ is a random variable whose distribution is completely unknown, but it is known that all the moments $E(X^k)$, for $k = 1, 2, . . . ,k\text{th}$ sample moment $\frac{1}{n}\Sigma^{n}_{i=1}X^k_i$ . Is an unbiased estimator of $E[{X^k}]$ 

To prove something is unbiased we need to prove that $E[\hat{\theta}]-\theta = 0$.
$E[\frac{1}{n}\Sigma_{i=1}^n X^k_i]=\frac{1}{n}E[\Sigma_{i=1}^n X^k_i]=\frac{n}{n}E[ X^k_i]=E[ X^k_i]$ 

## 8.7.3
For the conditions of exercise $2$, find an unbiased estimator of $E(X)^2$

We know that the sample variance is an unbiased estimator of $\text{Var}(X)$ and that the second sample moment is an unbiased estimator of $E[X^2]$. The sum of two unbiased estimators is an unbiased estimator. Thus the second sample moment minus the sample variance is an unbiased estimator of $E[X]^2$


## 8.7.8
Suppose that a random variable $X$ has the geometric distribution with unknown parameter $P (0 < p < 1)$. Show that the only unbiased estimator of $P$ is the estimator $δ(X)$ such that $δ(0) = 1$ and $δ(X) = 0$ for $X > 0$.

Let $\delta$ be an unbiased estimator of $X$. By definition of estimator $\delta$ returns some value for every possible observation of $X$. Thus the expected value of $\delta$ is $a_0p+a_1p(1-p)+...a_np(1-p)^n$. We can factor out a $p$ resulting in this value being $p(a_0+a_1(1-p)+...+a_n(1-p)^n)=p$ otherwise $a_0+a_1(1-p)+...+a_n(1-p)^n = 1$. As $p\rightarrow 1$ we see that the value of $a_0$ must converge to $1$. Alternatively as $p\rightarrow 0$, $\Sigma_{i=0} ^n a_n = 1$. Both of these extremes force $\delta$ to be be the previously mentioned function

