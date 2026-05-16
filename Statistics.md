---
tags:
  - Applied
---
Statistics is taking in observed data and making statements about the world. Because observed data is random this uses a lot of techniques and math from probability. 
Here is the path
# Path
#### 1. Parameter Estimation 
We assume that some random variable follows a distribution, then we use the observed data find the best possible parameters of that distribution 
#### 2. Statistics 
Now we start to consider functions of random vectors(Statistics) and using those to make more advanced statements about the parameters. For example we might use pivotal variables to make confidence intervals about our parameters. 
#### 3.  Hypothesis Testing
We expand on using these statistics to see how likely a specific belief about parameters is. For example we might say $\mu\leq n$ and then see how much faith we should have in that statement. It also lets us compare different populations using a statistic from both of them, to see how likely their parameters being the same are.
#### 4.  Non-Parametric Methods
Before working with this we were assuming that our data was from a specific distribution, but now we expand to methods which ask questions such as "does this data follow this distribution". This allows us to answer more advanced questions such as independence of variables

# Parameter Estimation
Given some observed data often you may want to find the parameters of the underlying distribution.  An example of this would be if you had data of a light bulb and then when it burns out you might want to model the distribution of when a fresh light bulb will burn out. 
## Posterior Distribution
If you are willing to make a statement about what the parameters might be before observing the data(A prior), you can have the distribution of the parameter "tune" itself to the observed data. We do this by calculating $P(\theta|x_1,...,x_n)$ using bayes rule. Because of Bayes rule 
 $$P(\theta|x_1,...,x_n) = \frac{P(x_1,...,x_n|\theta)P(\theta)}{P(x_1,...,x_n)}$$
 This actually can be easier to find because the bottom distribution is a constant, and serves to make sure the top part integrates to $1$. So we just ignore the bottom part and then find $P(x_1,...,x_n|\theta)P(\theta)$ and find $c$ such that $\int cP(x_1,...,x_n|\theta)P(\theta)=1$ ensuring it is a proper probability distribution. If we did have to calculate the value $P(x_1,...,x_n)$ we would have to integrate over every value of our prior. 
### Conjugate Prior
A conjugate prior is a specific distribution that when used as a prior of another distribution stays the same distribution when sampling it. Sometimes there are closed forms that tell you based off the data what the posterior distribution will equal. An example of this would be using the beta distribution as your prior when trying estimate $p$ in $\text{bin}(N,p)$. If started with a prior of $\text{beta}(a,b)$ and then observed $x$ successes, your posterior would be $\text{beta}(a+x,b+N-x)$ 

### Improper Prior
Sometimes you want to do a prior which does not integrate to $1$ and thus is not a probability distribution. An example of this would be considering all read numbers equally likely. This still works out because $P(\theta)$ is a constant number. Another example would be all real positive numbers. 

## Bayes estimator
While its nice to look at your posterior distribution, you aren't given a value back as an estimated parameter. To do this you use a bayes estimator, which picks a parameter value from the posterior based off some loss function. 

These loss functions compute some penalty based off how different the estimated parameter is than the true parameter. Often the loss function is either  $|\theta - \hat{\theta}|$ or $(\theta - \hat{\theta})^2$

Because we don't actually know the true parameter $\theta$, we instead minimize $E(L(\theta,\hat{\theta}))$  which is the expected loss over all possible theta values of the posterior. 

This ends up looking like 
$$
E[L(\theta,\hat{\theta})|x]=\int L(\theta,\hat{\theta})\xi(\theta|x)d\theta
$$
Where $E[L(\theta,\hat{\theta})|x]$ is a function of $\hat{\theta}$ which you want to find the minimal value for. 

## Maximum Likelihood Estimation
The maximum likelihood estimation technique finds the value of $\theta$ that maximizes the function $P(x_1,x_2,...,x_n|\theta)$. An example of this would be if we flipped a coin $7$ times and got heads $3$ then the likelihood function would be $p^3(1-p)^4$. Often we apply some monotonic function to the likelihood and then optimize it, like log to make the multiplication easier. 
This is essentially saying what parameter would make it the most likely for us to see the data we observed 

## Method of Moments
The method of moments is another way to estimate parameters. In order to do this you need $k$ system of equations between the parameters and the moments of the distribution. An example of this would be estimating the gamma distribution. We have the two systems of equations for the gamma distribution 
$$
E[X]=\frac{\alpha}{\beta},E[X^2]=\frac{\alpha(\alpha+1)}{\beta}
$$
which then you can solve for $\alpha$ and $\beta$ using the sample moments because they will converge in probability the true moments. 

## Properties of Estimators
### Bias
The bias of an estimator is defined as $E[\hat{\theta}]-\theta$, and an unbiased estimator is defined an estimator which has bias $0$. A surprising amount of estimators are biased, take for example the M.L.E of the german tank problem the expected value of $\hat{\theta}$ is less than the actual value of $\theta$ because increasing $\hat{\theta}$ would result in the probability of seeing the maximum we saw being less. 
### Consistency 
An estimator of a parameter is considered Consistent if as $n\rightarrow \infty$ the estimator converges in probability to the true parameter $\theta$. An example of this would be the sample mean when sampling from a normal distribution with parameters $\mu,\sigma^2$. The distribution of $\bar{X}_n \sim \text{norm}(\mu,\frac{\sigma^2}{n})$ so as $n\rightarrow \infty$ $P(|\mu-\bar{X}_n|>\epsilon)=0$  
### Mean Squared Error
The Mean Squared Error of a estimator is exactly what it sounds like, its the expected distance from the true parameter squared. Mathematically it can be written as $E((\hat{\theta}-\theta)^2)$ which can be rewritten into the form $\text{Var}(\hat{\theta})+\text{Bias}(\theta,\hat{\theta})^2$ which is typically easier to solve 




# Statistics 
We can define a statistic, which is a function from a vector of our random variable to some other space(often $\mathbb{R}$). Sometimes we want to study the distribution of this statistic, to be able to predict things like what the average or variance of a sample might be.

Alternatively there are some more advanced statistics which actually don't change from the parameters of our random variables, which we can use to make statements about the parameters of our random variable. 

## Statistics of the Normal Distribution
Here are some statistics which you would use when sampling from a normal distribution with parameters $\mu$ and $\sigma^2$
### Sample Mean
The sample mean which is defined as $\frac{1}{n}\Sigma_{i=1}^{n}X_i$ follows the normal distribution with parameters $\mu$ and $\frac{1}{n}\sigma^2$ 
### Sample Variance 
We know that $\frac{n}{\sigma^2}\hat{\sigma}^2$ follows the distribution $\chi^2_{n-1}$. Thus we can create a confidence interval 
$P\left((\chi^2_{n-1})^{-1}(\alpha/2)\leq \frac{n}{\sigma^2}\hat{\sigma}^2\leq (\chi^2_{n-1})^{-1}(1-\alpha/2)\right)=1-\alpha$ which can be rewritten into $P\left(\frac{n\hat{\sigma}^2}{(\chi^2_{n-1})^{-1}(1-\alpha/2)}\le \sigma^2 \le\frac{n\hat{\sigma}^2}{(\chi^2_{n-1})^{-1}(\alpha/2)}\right) = 1 - \alpha$
### T Statistic
The $T$ statistic is calculated as $n^{1/2}(\bar{X}_n-\mu)/\sigma^{\prime}$ where $\bar{X}=\frac{1}{n}\Sigma_{i=1}^{n}X_i$ and $\sigma^{\prime} =\frac{1}{n-1}\left(\Sigma_{i=1}^{n}(X_i-\bar{X}_n)^2\right)^{\frac{1}{2}}$. The $T$ statistic follows the $T$ distribution with $n-1$ degrees of freedom. Note that since this does not depend on the variance, you can rewrite stuff to be able to isolate $\mu$ and make a confidence interval around it.  
We can define a confidence interval using $P(-T^{-1}_{n-1}(1-\frac{\alpha}{2})\leq n^{1/2}(\bar{X}_n-\mu)/\sigma^{\prime}\leq T^{-1}_{n-1}(1-\frac{\alpha}{2}))=1-\alpha$ which can be rewritten to 
$P\left(\bar{X}_n - T^{-1}_{n-1}\left(1-\frac{\alpha}{2}\right)\frac{\sigma'}{\sqrt{n}}\le \mu \le\bar{X}_n + T^{-1}_{n-1}\left(1-\frac{\alpha}{2}\right)\frac{\sigma'}{\sqrt{n}}\right) = 1-\alpha$. 

Additionally $U=\frac{\sqrt{m+n-2}(\bar{X}-\bar{Y})}{(\frac{1}{m}+\frac{1}{n})^{1/2}\sqrt{S^2_X+S^2_Y}}$ follows the $T$ distribution with $m+n-2$ degrees of freedom iff $\mu_X=\mu_Y$ and $\sigma_{X}=\sigma_{Y}$.

Further $U=\frac{\bar{X_m}+\bar{Y_n}}{\sqrt{\frac{S_X^2}{m(m-1)}+\frac{S_Y^2}{n(n-1)}}}$ follows the $T$ distribution with degrees of freedom that is a long formula which needs to be estimated, that if I am using I should probably just look up

### F Statistic 
If two populations $X$ and $Y$ and the same variance $\sigma_X=\sigma_Y$, then 
$$
V=\frac{S_x/(m-1)}{S_y/(n-1)}
$$
Follows the F distribution 

### F Statistic 


## Confidence Intervals
A confidence interval is defined as $P(A < g(θ) < B) ≥ γ$ where $A\leq B$ and $A,B,\gamma$ are real numbers and $g$ is a real valued function of $\theta$. 
These state the probability that a specific parameter lies within the interval $(A,B)$. Note that while traditionally the interval is symmetric, it does not need to be. You can additionally do $(A,\infty)$ or $(-\infty,B)$.
These are mostly calculated by using random variables which are constructed using observations which have the same distribution for all possible parameters. These type of variables are known as pivotal.  
### Pivotal Technique
A pivotal variable $V$ is a random variable which is a function of $X_1...X_n$ and is the same regardless of parameters $\theta$.  These are known as pivotal variables and can be used to create confidence intervals 

Let $v$ be a pivotal variable that is a function of $X_1,...,X_n$. Let $V$ be the CDF of $v$, we can create a confidence interval. We do this by rewriting 
$$
P(V^{-1}(x)\leq v\leq V^{-1}(y))=y-x
$$
to isolate the underlying parameters. An example of this would be $\theta T \sim \text{Gamma}(1,1)$ where $T$ is the sum of i.i.d exponential distributions. We can then write a statement in terms of $\text{Gamma}(1,1)$ and then arrange it to give us information about $\theta$

# Hypothesis Testing 
Hypothesis testing does exactly what it sounds like, it lets you test how supported that hypothesis is by the data. An example might be wether fruit that receive a specific type of fertilizer grow bigger than a type that don't. 

## Definition of Hypothesis testing
The parameter value $\theta \in \Omega$ can either exists in two different spaces $\Omega_0$ and $\Omega_1$ where $\Omega_0 \cup \Omega_1 = \Omega$.  As statisticians we want to determine wether or not the parameter is in $\Omega_0$ or $\Omega_1$ which is determined based off some test statistic. We define $H_0$ as $\theta \in \Omega_0$ which is known as our null hypothesis and $H_1$ as $\theta \in \Omega_1$ which is our alternative hypothesis. 

## Test Statistic/Critical Region
The critical region is a set of all data vectors which we reject $H_0$. Often it is difficult to think about what data vectors we are rejecting, so we instead define some function known as our test statistic $T:X\rightarrow \mathbb{R}$. We then based off our test statistic reject or fail to reject $H_0$. 

## Type I and II errors
A type I error is when reject the null hypothesis when it is true, and a type II error is when you fail to reject the null hypothesis when it is not true. 
Type I: Convicting a innocent person 
Type II: Failing to convict a guilty person 
## Power Function
For some test procedure $\delta$ the power function denoted as $\pi(\theta|\delta)$ is a function from $\Omega\rightarrow [0,1]$ where the output is the probability of rejecting the null hypothesis for a specific value of $\theta$.  Ideally we want the power function of our testing procedure to be high when $\theta \in \Omega_{1}$ and low when $\theta\in\Omega_0$ 
## Significance/Size/P-Value
A hypothesis test has a level $\alpha_0$ if for all values of $\theta \in \Omega_0$, $\pi(\theta)\leq \alpha_0$. This means its the highest power in the area of the null hypothesis. Can satisfy multiple different levels. 

The size of a hypothesis test is $\text{Sup}(\pi(\theta))$ where $\theta\in\Omega_0$. This is essentially the smallest level that the tests satisfies. 

For a given test the p-value is the smallest level $\alpha_0$ such that we would reject the null. 

## Common Types of Hypothesis tests
These are often related to the statistics from a distribution
### Likelihood ratio test 
The likelihood ratio test uses the statistic 
$$
\Lambda(x)=\frac{\text{sup}_{\theta\in\Omega_0}(f_n(x|\theta))}{\text{sup}_{\theta\in\Omega}(f_n(x|\theta))}
$$
And we reject the test whenever this value is less than some value $k$. This is essentially finding what is the maximum likelihood given that the null hypothesis is true, compared to what is the maximum likelihood in the whole space. Thus if $\Omega_0$ contains the point with the maximum likelihood, the likelihood ratio will return $1$
### Using Test Statistics 
An example of this would be using the $T$ statistic. If we have some assumption about the $\mu$ represented by $\mu \in \Omega_0$. We calculate the $\text{Sup}_{\mu_0\in \Omega_0}P(x\geq n^{1/2}(\bar{X}_n-\mu)/\sigma^{\prime}|\mu = \mu_0)=p$. This is saying that from all values of the null hypothesis, the probability of seeing this value or more extreme is $p$ which is our $p$ value
Additionally if we want to analyze the power function, we need to use the non-central T distribution since $\mu\neq \mu_0$ and then see the probability of getting a statistic that we reject. 

This example shows how since we know what distribution the statistic follows, we can find the probability that we see a statistic that extreme or more extreme. If we see a statistic that is incredibly extreme for our null hypothesis we might suspect that our null hypothesis isn't true.
Additionally if we want to analyze the power we have to consider the distribution of our statistic in a given $\mu$ was the true value. Since our test statistic follows the correct distribution only if the null hypothesis is true, we have to do some work to figure out what the distribution is, and then see the probability of this distribution give us a statistic which would lead to rejecting the null hypothesis  

# Non-Parametric Techniques
Non-parametric techniques don't assume that the data is from a specific distribution, and are often used to test if the data is from a specific distribution. 
## Goodness of Fit Testing
These techniques are used to determine wether some real world process follow a specific distribution. If we want to determine wether something follows a family of distributions we can estimate the parameters often using the MLE and then use that as our specific distribution 
### Chi Squared Binning 
This works on both categorical data and on continuous data. For categorical data if you have $k$ categories and then $p_i$ probability of being in the $i$th then the following statistic will follow the chi squared distribution with $n-1$ degrees of frequency, as $n\rightarrow \infty$
$$
Q=\Sigma_{i=1}^{k} \frac{(N_i- np_i)^2}{np_i}
$$
Where $N_i$ is the number of elements in the $i$th category, and $n$ is the total number of observations. Its easy to see that each individual part of this sum would be the normal distributions squared. The reason it has $n-1$ degrees of freedom is because if you knew the values of the first $k-1$ values for each category, then the last value would just be a constant because we know it. 

We never do a two tailed test using the Chi Squared because any deviation from the proposed probabilities will only increase the value of $Q$

We can also extend this away from categorical to continuous by creating "bins" from the CDF of the distribution. We then use these bins as as the categories and then calculate the chi squared statistic
### Test of Independence
It initially may seem like it would be different from goodness of fit testing, but it is actually very similar. If you knew the distribution of two random variables $X$ and $Y$ you could test if the joint random variable $(X,Y)$ follows the distribution $P(X=x,Y=y)=P(X=x)P(Y=y)$. But we don't know the distribution of the random variables because we are doing this on observed data.

But we can estimate the distribution of $X$ and $Y$ from the observed data. We do this by computing the marginals. And then using the proportion of elements in the marginal as the probability we get an estimate of the probabilities of being in each category. We then use the independent coupling as our proposed distribution, and calculate the Chi Squared statistic for that. This statistic will follow the $\chi^2$ with $(R-1)(C-1)$ degrees of freedom. This is because if you knew this many values and the marginals you would be able to determine every value. 

Again we never do a two tailed test using the Chi Squared because any deviation from the proposed probabilities will only increase the value of $Q$


# Linear Regression
A model is something that has the goal of predicting some some random variable $Y$ from another random variable $X$(Hopefully there is some connection between them). A linear model is a model that defines the relationship between $X$ and $Y$ in terms of $Y_i=\Sigma_{j=1} \phi_j(X_i)$ where $\phi_j$ is some function. 
## Simple Linear Models
Simple linear models define the relationship $Y=\beta_0+\beta_1 x +\epsilon$ where $\epsilon \sim \text{Norm}(0,\sigma^2)$. It makes the following assumptions
1. **Normality:** The distribution of $Y$ given $x$ is a normal distribution 
2. **Linear Mean:** There are parameters $\beta_0$ and $\beta_1$ such that the conditional value of $Y_i$ given $x_i$ is $\beta_0+\beta_1 x_i$
3. **Common Variance:** The variance of $Y$ given $x$ is $\sigma^2$ regardless of the $x$. 
4. **Independence:** The conditional random variables $Y_i$ and $Y_j$ are independent  
These assumptions boil down to have our model be predicting the conditional expectation $E[Y|X]$ where the joint random variable $(X,Y)$ is bivariate normal. 
We calculate the MLE of $\hat{\beta}_0$ and $\hat{\beta}_1$ to be the following
$$
\hat{\beta}_0=\bar{Y}-\hat{\beta_1}\bar{X}
$$
$$
\hat{\beta}_1=\frac{\Sigma_{i=1}^n (y_i-\bar{Y})(x_i-\bar{X})}{\Sigma_{i=1}^{n}(x_i-\bar{X})^2}
$$
### Hypothesis testing for Simple Linear Models
When testing hypothesis where we pick $c_0$, $c_1$ and $c_*$ of wether
$$
H_0:c_0\beta_0+c_1\beta_1=c_{*}
$$
$$
H_1:c_0\beta_0+c_1\beta_1\neq c_{*}
$$
We know that the following statistic follows the $t$ distribution with $n-2$ degrees of freedom
$$
U=[\frac{c_0^2}{n}+\frac{(c_0\bar{x}-c_1)^2}{s_x^2}]^{-1/2}(\frac{c_0\hat{\beta_0}+c_1\hat{\beta_1}-c_{*}}{\sigma^{\prime}})
$$
Initially I was confused about the formatting of this hypothesis test, but I realized that often used in ways like setting $c_0=0,c_1=1$ and $c_*=b$ where $b$ is some proposed or existing linearity to test the slope. 

## Generalized Linear Models
Generalized linear models rather than predicting the data in the form $\beta_0+\beta_1 x$ instead us a linear combination of functions instead, additionally we can use multiple variables to predict the output values $\{x_1,...,x_n\}$. This means that we are computing $E[Y]=\Sigma_{j=1}^{k}\Sigma_{i=1}^{n} \phi_{ij}(x_j)$ attempting the minimize the squared error. 

We compute this using $y$ a $n\times 1$ vector of observed values, $\beta$ a $p\times 1$ vector of parameters, $\hat{\beta}$ a $p\times 1$ vector of parameter estimates. The design matrix denoted where $\phi_{aj}(x_{ij})$ is $a$th function on the $j$th predictor variable evaluated on $j$th value of the $i$th observation
$$\mathbf{Z} = \begin{bmatrix} \phi_{11}(x_{11}) & \cdots & \phi_{p1}(x_{11}) & \phi_{12}(x_{12}) & \cdots & \phi_{pk}(x_{1k}) \\ \phi_{11}(x_{21}) & \cdots & \phi_{p1}(x_{21}) & \phi_{12}(x_{22}) & \cdots & \phi_{pk}(x_{2k}) \\ \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\ \phi_{11}(x_{n1}) & \cdots & \phi_{p1}(x_{n1}) & \phi_{12}(x_{n2}) & \cdots & \phi_{pk}(x_{nk}) \end{bmatrix}
$$ We then can compute the MLE finding $\hat{\beta}=(Z^{T}Z)^{-1}Z^Ty$ which gives us coefficients to go in front of each $\phi$ 

## ANOVA Testing
This is a way of testing wether multiple categories all have the same mean. The null and alternative hypothesis are as follows
$$
H_0:\mu_1=\mu_2=...=\mu_n
$$
$$
H_1: H_0 \text{ is not true}
$$
