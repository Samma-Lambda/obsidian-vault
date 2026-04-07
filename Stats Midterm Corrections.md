#### Problem 1
Suppose we have r.v $X$ that represents the number of pets that a randomly chose willamette student has
##### c)
Let $E(X)=2$ and variance $\text{Var}(X)=\sigma^2=4$, what is $\text{lim}_{n\rightarrow \infty}$ of $P(\bar{X}_n\geq \frac{2}{\sqrt{n}}+2)$
$P(\bar{X}_n\geq \frac{2}{\sqrt{n}}+2)=P(\frac{\bar{X}_n-2}{2/\sqrt{n}}\geq 1)$ note that $\frac{\bar{X}_n-2}{2/\sqrt{n}}$ converges to the normal distribution according the CLT thus $P(\frac{\bar{X}_n-2}{2/\sqrt{n}}\geq 1)\approx 1-\Phi(1)$ 

#### Problem 2
Suppose we have iid $X_1,...,X_n$ where $X_i\sim \text{Bernouli}(\theta)$ use a $\text{Beta}(\alpha,\beta)$ prior for $\theta$ 
##### b) 
Show that the Bayes estimator $E(\theta|X)$ is the weighted average of the prior mean and the sample proportion $\bar{X}_n$ 

The expected value of the prior distribution is $\frac{\alpha}{\alpha+\beta}$ 
The sample proportion is $\frac{\Sigma_{i=1}^{n} X_i}{n}$ 
The bayes estimator is $\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha + \Sigma_{i=1}^{n}X_i+\beta+ n - \Sigma_{i=1}^{n}X_i}=\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha +\beta+ n}$ 
we need to solve the equation to show  $c_1 \frac{\alpha}{\alpha+\beta}+c_2 \frac{\Sigma_{i=1}^{n} X_i}{n}=\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha +\beta+ n}$
we can see that $c_1 = \frac{\alpha+\beta}{\alpha+\beta+n}$ and $c_2 = \frac{n}{\alpha+\beta+n}$ are the constants by plugging them in $\frac{\alpha+\beta}{\alpha+\beta+n}\frac{\alpha}{\alpha+\beta}+\frac{n}{\alpha+\beta+n}\frac{\Sigma_{i=1}^{n} X_i}{n}=\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha +\beta+ n}$. Thus the bayes estimator is the weighted average of the sample proportion and bayes estimator 



#### Problem 3
Let $X_1,...,X_n$ be conditionally iid $\text{Unif}(0,\theta)$ with known parameter $\theta >0$ let $Y_n=\text{Max}\{X_1,...X_n\}$
##### a)
Find $E(Y_n|\theta)$ 
$Y_n/\theta \sim \text{beta}(n,1)$ because it it is the maximum of $n$ standard uniforms. The expected value of the beta distribution is $\frac{\alpha}{\alpha+\beta}$ thus the the expected value is $\frac{n}{n+1}$ 


##### b)
Using $Y_n$ estimate $\theta$ in $2$ ways 
##### i) 
MLE based on $Y_n$, not the actual $X_i$

The cdf of $Y_n$ given $\theta$ is $1-(y/\theta)^n$ so therefore the the pdf of $Y_n$ is $n y^{n-1}/\theta^{n}$ which is proportional to $\theta^{-n}$. Note that $\theta^{-n}$ is decreasing with respect to $n$ thus the MLE estimate would be $Y_n$

##### ii)
Bayesian estimate based on the expected value of the posterior distribution(You can use any prior you want including improper, just state what it is)

We are using the improper prior $\frac{1}{\theta}$ because it includes all values of $[0,\infty)$. Note that $P(\theta|Y_n)\propto\theta^{-n}\frac{1}{\theta}$. We need $\int_{y}^{\infty}c\theta^{-(n+1)}=1$ which we then solve for $c$. We get $c\frac{\theta^{-n}}{-n}|_{y}^{\infty}=1$ which means that $c\frac{y^{-n}}{n}=1$ meaning $c=ny^n$. Thus $P(\theta|Y_n)=ny^{-n}\theta^{-(n+1)}$ which we need to find the expected value of $\theta$. We see that the $\int_{y}^{\infty}\theta ny^n \theta^{-(n+1)}d\theta=ny^n \int_{y}^{\infty}\theta^{-n}d\theta=\frac{ny}{n-1}$    

#### Problem 3c)
Are the estimates in $b)$ unbiased? consistent? Explain briefly 

The MLE is biased because it will always be less than $\theta$. This is because it estimates $\theta$ as $Y_n$ and $Y_n$ will always be less than $\theta$ because the probability of some $X_i=\theta$ is zero. 
The MLE is consistent because it estimates $\theta$ as $Y_n$ and as $n$ goes to infinity $Y_n$ approaches $\theta$. This is because the probability you have not seen a value above a specific number less than $\theta$ exponentially decays 

The bayesian estimator is $\frac{n}{n-1}y$ which as $n$ goes to infinity $\frac{n}{n-1}$ converges to $1$ and $y$ converges to theta as $n$ goes to infinity. Thus the estimator is consistent
The expected value of $Y_n$ is $\frac{n}{n+1}\theta$ because of the aces dividing the deck, so we would expect $\mathbb{E}[\hat{\theta}]$ to be $\frac{n}{n-1}\frac{n}{n+1}\theta=\frac{n^2}{n^2-1}\theta$. Note that $\frac{n^2}{n^2-1}\theta -\theta \neq 0$ thus the estimator is biased  


#### Problem 3d)
Suppose that $Y_4=10$ use the posterior distribution of $\theta$ from $bii$ to form an approximate $95\%$ confidence interval for $\theta$ 

Using the posterior distribution $P(\theta|Y_n)=ny^{-n}\theta^{-(n+1)}$ and $n=4$ and $Y_n = 10$ find a $95\%$ confidence interval. We need to look at the cdf $1-(y/\theta)^n$ and find where $1-(10/\theta)^4 = 0.025$ and $1-(10/\theta)^4 = 0.975$. Solving these we get a lower bound of $10.06349525$ and upper bound of $25.14866$. 

#### Problem 4
Suppose we have $25$ iid $X_1,...,X_{25}\sim\text{N}(\mu,\sigma^2)$ with both $\mu$ and $\sigma^2$ unknown
#### a) 
Write down an expression for the rejection region of a one sided test of $H_0:\mu\leq \mu_0$ versus $H_1:\mu > \mu_0$. 

We know that $\frac{5(\bar{X}_n-\mu_0)}{\sigma^{\prime}}\sim t_{24}$. We also know that this is a one sided test from the null and alternative hypothesis. We can calculate $x = T^{-1}_{24}(1-\alpha)$ and if $\frac{5(\bar{X}_n-\mu_0)}{\sigma^{\prime}}\geq x$ then we reject 

#### b)
Write down an expression for the power $\pi(\theta|\delta)$ of the same level-$\alpha$ one-sided test of $H_0:\mu \leq \mu_0$ versus $H_1: \mu > \mu_0$. Find the power in terms of an arbitrary value $\theta$.(You can assume $\theta>\mu_0$ if it makes it easier to think about although its not nessacary) 

The power function returns  $P(\frac{5(\bar{X}_n-\mu_0)}{\sigma^{\prime}}\geq T^{-1}_{24}(1-\alpha))$ we can rewrite $\frac{5(\bar{X}_n-\mu_0)}{\sigma^{\prime}}=\frac{5(\bar{X}_n-\theta)}{\sigma^{\prime}}+\frac{5(\theta-\mu_0)}{\sigma^{\prime}}$. Note that this random variable follows the $T$ distribution with $\mu = \theta$ and a non-centrality parameter of $\frac{5(\theta - \mu_0)}{\sigma^{\prime}}$. Defining the non-centrality parameter as $\frac{5(\theta - \mu_0)}{\sigma^{\prime}}$ initially weirded me out but since we know $\theta$ and $\mu_0$ its fine. 
So if we calculate $T_{24}^{-1}(1-\alpha)=x$ and then calculate $1-T_{24,\frac{\theta - \mu_0}{\sigma^{\prime}}}^{-1}(x)$ we will ge the power function $\pi(\theta)$. Here I am using $T_{24,\frac{\theta - \mu_0}{\sigma^{\prime}}}^{-1}(x)$ to represent the $T$ distribution with $24$ degrees of freedom with a non-centrality parameter of $\frac{\theta-\mu_0}{\sigma^{\prime}}$

#### c)
For $n=25$, $\bar{X}=12.4$, $s=3.5$, $\mu = 11.0$ and $\alpha =0.05$ find the appropriate test statistic and write the $p$-value in terms of the CDF of the distribution.

We calculate our test statistic to be $\frac{12.4-11.0}{3.5/5}=2$ thus our p value is $1-T_{24}(2)$ 

#### d)
A researcher claims that using a larger sample size would always lead to rejecting $H_0$ based on the rejection region described in a). Is this correct? Explain why or why not

This is incorrect because if the null hypothesis is actually true than increasing the $n$ does not guarantee rejection. But it makes it easier to detect differences between $\mu$ and $\mu_0$