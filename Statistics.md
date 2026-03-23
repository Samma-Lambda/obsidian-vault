---
tags:
  - Applied
---
# Types of Convergence 
There are a few different types of convergence in probability and statistics. IT IS VERY IMPORTANT TO DISTINGUISH BETWEEN THEM
## Converges in Probability
A sequence $X_n$ converges in probability to a value $x$ if $P(|X_n-x|)<\epsilon$  $\forall \epsilon >0$ as $n\rightarrow \infty$. An example of this would be 

## Almost Sure convergence
This is where $n\rightarrow \infty$ we see that $P(X_n=x)=1$. An example of this would be having a head before the $n$th flip 

## Converges in Distribution
This is where as $n\rightarrow \infty$ a distribution converges to another distribution. An example of this would be the central limit theorem showing that a large number of i.i.d converges to the normal distribution 


# Large Sample Sizes
A common effect within statistics is that the estimation of things because better as you get more data. For example the sample mean becomes more and more reliable as the sample size gets larger and larger, these theorems seek to make more formal statements about this effect
## Markovs Inequality
This inequality states that for random variables $X>0$
$$
P(X\ge t)\leq \frac{E[X]}{t}
$$
This inequality is used to provide bounds on the probability of large values of $X$, and as a stepping stone for proving future theorems. 

## Chebyshev Inequality
This inequality states that 
$$
P(|X-E[X]|\ge t)\leq \frac{\text{Var}(X)}{t^2}
$$
This is proved using a specific case of Markovs Inequality where you use the random variable  $Y=(X-E[X])^2$. This shows that $P(X-E[X]\ge t)=P(Y\ge t^2)\le \frac{E[X-E[X])]}{t^2}$. This can provide useful bounds of the probability that a random variable strays aways from the expected value.

## Chernoff Bounds
This is another specific case of Markovs Inequality. We start with 
$$P(X>a)=P(e^{tX}>e^{ta})\leq \frac{E[e^{tX}]}{e^{ta}}=\frac{M_{X}(t)}{e^{ta}}$$
Where $M_X(t)$ is the moment generating function of $X$. This may seem arbitrary but this holds for any $t>0$ so you get to find the minimal $t$ value.  


## Jensen's Inequality
This is proven using a Taylor approximation of function. For any convex function we have 
$$
E[f(x)]\geq f(E[x])
$$


## Law of Large numbers
This states that the sample mean $\bar{X}_n$ converges in probability to the true mean $\mu$. It is important to note the difference between converges in probability and converges to a constants. We can ensure that it will get closer to the mean but ad infinitum it won't equal $1$

## Central Limit Theorem
This states that the distribution of the sum of i.i.d random variables will converge to the normal distribution. 

# Parameter Estimation
Given some observed data often you may want to find the parameters of the underlying distribution.  An example of this would be if you had data of a light bulb and then when it burns out you might want to model it using an exponential distribution with some one-dimensional parameter theta. 
## Posterior Distribution
You can use bayes rule to find $P(\theta|x_1,...,x_n)$ by calculating out the distribution of $\frac{P(x_1,...,x_n|\theta)P(\theta)}{P(x_1,...,x_n)}$. This actually can be easier to find because the bottom distribution is a constant, and serves to make sure the top part integrates to $1$. So we just ignore the bottom part and then find $P(x_1,...,x_n|\theta)P(\theta)$ and find $c$ such that $\int cP(x_1,...,x_n|\theta)P(\theta)=1$ ensuring it is a proper probability distribution 
### Conjugate Prior
A conjugate prior is a specific distribution that when used as a prior of another distribution stays the same distribution when sampling it. Sometimes there are closed forms that tell you based off the data what the posterior distribution will equal. An example of this would be the beta distribution being the prior of $p$ in the binomial with $n$ trials. 

### Improper Prior
Sometimes you want to do a prior which does not integrate to $1$ and thus is not a probability distribution. An example of this would be considering all read numbers equally likely. This still works out because $P(\theta)$ is a constant number. Another example would be all real positive numbers. 

## Properties of Estimators
### Bias
The bias of an estimator is defined as $E[\hat{\theta}]-\theta$, and an unbiased estimator is defined an estimator which has no bias. A surprising amount of the time estimators are biased, take for example the M.L.E of the german tank problem the expected value of $\hat{\theta}$ is less than the actual value of $\theta$. 
### Consistency 
An estimator of a parameter is considered Consistent if as $n\rightarrow \infty$ the estimator converges in probability to the true parameter $\theta$. An example of this would be the sample mean when sampling from a normal distribution with parameters $\mu,\sigma^2$. The distribution of $\bar{X}_n \sim \text{norm}(\mu,\frac{\sigma^2}{n})$ so as $n\rightarrow \infty$ $P(|\mu-\bar{X}_n|>\epsilon)=0$  




## Maximum Likelihood Estimation
The maximum likelihood estimation technique finds the $\theta$ value which has the highest density. In other words it finds the parameter which maximizes the chance of seeing the observed data.

Additionally you can also apply some monotonic function to the likelihood function to make it easier to optimize, like the logarithm function. 


## Bayes estimator
There are some problems with MLE estimation. One such one is the german tank problem. The MLE estimation will always assume that the highest number tank is cap of the uniform distribution.

To rectify this you define a loss function, which takes in the estimated parameter and the true parameter and penalizes based off the difference. This is denoted as $L(\theta,\hat{\theta})$ which is usually either $|\theta - \hat{\theta}|$ or $(\theta - \hat{\theta})^2$. 

We then go and find a value of $\theta$ what which minimizes $E(L(\theta,\hat{\theta}))$ which is the expected loss over all possible theta values of the posterior. The $|\theta - \hat{\theta}|$ loss function gives the mode and $(\theta - \hat{\theta})^2$ expected value. 

This ends up looking like 
$$
E[L(\theta,\hat{\theta})|x]=\int L(\theta,\hat{\theta})\xi(\theta|x)d\theta
$$
Where $E[L(\theta,\hat{\theta})|x]$ is a function of $\hat{\theta}$ which you want to minimize. 



## Method of Moments
The method of moments is another way to estimate parameters. In order to do this you need $k$ system of equations between the parameters and the moments of the distribution. An example of this would be estimating the gamma distribution. We have the two systems of equations for the gamma distribution 
$$
E[X]=\frac{\alpha}{\beta},E[X^2]=\frac{\alpha(\alpha+1)}{\beta}
$$
which then you can solve for $\alpha$ and $\beta$ using the sample moments because they will converge in probability the true moments

# Sampling Distribution
This is where you take multiple observations from a distribution and pass it into a function which outputs a value. Often our function is sample mean or sample variance, but it can be more complicated functions including the max or min of a sample. 
## Sample Mean and Variance
We define $\bar{X}_n=\frac{1}{n}(X_1+...+X_n)$ where all $X_i$ come from the same distribution itself is a random variable. We can easily see using the properties of expected value and variance see that $E[\bar{X}_n]=\mu$ and $\text{Var}(\bar{X}_n)=\frac{\sigma^2}{n}$. Additionally there is the strange property that the sample mean and the sample variance are independent random variables 

## Distribution of  Sample Variance and Mean for Normal distribution
The sample mean $\frac{1}{n}\Sigma X_i$  when sampling from a normal distribution is a normal distribution which can be proved by seeing that the sum of normals is normal and that the scaled version of normal distributions is normal

Alternatively $\frac{n\hat{\sigma^2}}{\sigma^2}$ follows the chi squared distribution with $n-1$ degrees of freedom. The chi squared distribution with $n$ degrees of freedom is equivalent to $X_1^2+...+X_n^2$ 


## T-Distribution
This distribution is defined below where $Z$ is standard normal, and $Y$ is $\chi^2_m$ then the $t$ distribution with $m$ degrees of freedom is 
$$
X=\frac{Z}{(\frac{Y}{m})^2}
$$
When we have $n$ samples from the normal distribution the distribution $U=\sqrt{n}(\bar{X}_n-\mu)/\sigma^{\prime}$ is the $t$ distribution with $n-1$ degrees of freedom.
We can calculate $P(U\leq x)=p$ for our desired $p$ value using the $t$ distributions quantile function to find an $x$. You then get $P(\sqrt{n}(\bar{X}_n-\mu)/\sigma^{\prime} \leq x)$ which can be rewritten into the form $P(\bar{X}_n\leq \mu + \frac{x}{\sqrt{n}}\sigma^{\prime})=p$ but this is not as useful as one might hope because $\sigma^{\prime}$ is a random variable. But it will eventually let us make confidence intervals. 


## Confidence Intervals
A confidence interval is defined as $P(A < g(θ) < B) ≥ γ$ where $A\leq B$ and $A,B,\gamma$ are real numbers and $g$ is a real valued function of $\theta$. 
These state a the probability that a specific parameter lies within the interval $(A,B)$. Note that while traditionally the interval is symmetric, it does not need to be. You can additionally do $(A,\infty)$ or $(-\infty,B)$.
These are mostly calculated by using random variables which are constructed using observations which have the same distribution for all possible parameters. These type of variables are known as pivotal.  
### Pivotal Technique
A pivotal variable $V$ is a random variable which takes a sample $X_1...X_n$ and is the same regardless of parameters $\theta$. Additionally if there is some function such that $r(V(X,\theta))=g(\theta)$, we can do the following technique

Let $V$ be a pivotal variable that is a random sample of $X_1,...,X_n$. Let $G$ be the CDF of $V$, we can create a confidence interval $A = r(G^{-1}(\gamma_1), X)$ and $B = r(G^{-1}(\gamma_2),X)$. 
#### Notable Pivotal Variables 
- **T-Distribution:** $n^{\frac{1}{2}}(\bar{X}_n-\mu)/\sigma^{\prime}$ when you are sampling from the normal distribution always follows the $T$ distribution
- $\theta T$ is $\text{Gamma}(1,1)$ where $T$ is the sum of i.i.d exponential distributions
- **Chi-Squared:** Since the chi squared distribution is the sum of squared standard normals. We see that when $S^2=\frac{1}{n-1}\Sigma_{1}^n(X_i-\bar{X}_n)$ then $\frac{(n-1)S^2}{\sigma^2}\sim \chi^2_{n-1}$  
### Confidence Interval for the rate of exponentials
If we have samples from some exponential distribution $X_i$ and we want to estimate $\theta$ we could construct a confidence interval using this method. Let $T$ be the sum of all the observations. Note that $\theta T$ is a gamma distribution with parameters $n$ and $1$. We know that $P(\theta T \leq G^{-1}(\gamma))=\gamma$,now we can rearrange this to be $P(\theta\leq \frac{G^{-1}(\gamma)}{T})=\gamma$ 


# Hypothesis Testing 
Hypothesis testing does exactly what it sounds like, it lets you test how supported that hypothesis is by the data. An example might be wether fruit that receive a specific type of fertilizer grow bigger than a type that don't. 

## Definition of Hypothesis testing
The parameter value $\theta \in \Omega$ can either exists in two different spaces $\Omega_0$ and $\Omega_1$ where $\Omega_0 \cup \Omega_1 = \Omega$.  As statisticians we want to determine wether or not the parameter is in $\Omega_0$ or $\Omega_1$ which is determined based off some test statistic. We define $H_0$ as $\theta \in \Omega_0$ which is known as our null hypothesis and $H_1$ as $\theta \in \Omega_1$ which is our alternative hypothesis 

## Critical Region/Rejection Region
The critical region is a set of all data vectors which we reject $H_0$. We can also define a region based off some test statistic $T:X\rightarrow \mathbb{R}$ called the rejection region which is all values of test statistics such that we reject $H_0$. 
## Type I and II errors
A type I error is when reject the null hypothesis when it is true, and a type 2 error is when you fail to reject the null hypothesis when it is not true. 
Type I: Convicting a innocent person 
Type II: Failing to convict a guilty person 
## Power Function
For some test procedure $\delta$ the power function denoted as $\pi(\theta|\delta)$ is a function from $\Omega\rightarrow [0,1]$ where the output is the probability of rejecting the null hypothesis for a specific value of $\theta$.  Ideally we want the power function to be high when $\theta \in \Omega_{1}$ and low when $\theta\in\Omega_0$ 


## Significance/Size/P-Value
A hypothesis test has a level $\alpha_0$ if for all values of $\theta \in \Omega_0$, $\pi(\theta)\leq \alpha_0$. The size of a hypothesis test is $\text{Sup}(\pi(\theta))$ where $\theta\in\Omega_0$. The $p$ value is the smallest level at which we would reject the null hypothesis 


## Common Types of Hypothesis tests
### Likelihood ratio test 
The likelihood ratio test uses the statistic 
$$
\Lambda(x)=\frac{\text{sup}_{\theta\in\Omega_0}(f_n(x|\theta))}{\text{sup}_{\theta\in\Omega}(f_n(x|\theta))}
$$
And we reject the test whenever this value is less than $k$. 

### T test
This is used when you are sampling from a normal distribution, and there is a unknown $\sigma^2$ and mean $\mu$ and we want to determine wether $H_0: \mu \leq \mu_0$ and $H_1: \mu > \mu_0$. 
We reject $H_0$ if $U\geq c$ where $U=n^{1/2}\frac{\bar{X}_n-\mu_0}{\sigma^{\prime}}$. Note that when $\mu_0=\mu$ we get $U=t_{n-1}$. 
We calculate the value of $c$ based off our desired level $\alpha_0$ where $T_{n-1}^{-1}(1-\alpha_0)=c$ 