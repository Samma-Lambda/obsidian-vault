### 9.1.1
Let $X$ have the exponential distribution with parameter $β$.Suppose that we wish to test the hypotheses $H_0:β≥1$ versus $H_1 : β < 1.$ Consider the test procedure $δ$ that rejects
$H_0$ if $X≥1$ 

a. Determine the power function of the test.
$X\sim \text{exp}(\beta)$ the power function is the probability that the null hypothesis is rejected for a given $\beta$. The power function is the probability of rejecting the null for a given $\beta$ so we just need to calculate $P(X\geq 1)$ which equals $\int_{1}^{\infty}\beta e^{-\beta x}dx=e^{-\beta}$ via u substitution. Thus our power function is $\pi(\beta)=e^{-\beta}$      

b. Compute the size of the test
To find the size of the test we need to find the $\text{sup}(P(X\geq 1))$ for a $\beta \in H_0$ which to be $e^{-1}$ because it is decreasing 


### 9.1.2
Suppose that $X_1, . . . , X_n$ form a random sample from the uniform distribution on the interval $[0, θ ]$, and that the following hypotheses are to be tested: $H_0: \theta \geq 2$ and $H_1: \theta <2$. Let $Y_n = \text{max}\{X_1, . . . , X_n\}$, and consider a test procedure such that the critical region contains all the outcomes for which $Y_n ≤ 1.5$.
a. Determine the power function of the test. 
Let $X_1,...X_n \sim \text{uniform}(0,\theta)$ the power function $\pi(\theta)=1,\forall \theta \leq 1.5$ and $\pi(\theta)=(\frac{1.5}{\theta})^n, \forall \theta \geq 1.5$ 

b. Determine the size of the test.
The size of this text is $\text{sup}(\pi(\theta)),\forall \theta \in H_1$ which is $\theta = 2$ giving us $(\frac{3}{4})^n$


### 9.1.4
Suppose that $X_1, . . . , X_n$ form a random sample from the normal distribution with unknown mean $μ$ and known variance $1$. Suppose also that $μ_0$ is a certain specified number, and that the following hypotheses are to be tested: $H_0: \mu = \mu_0$ and $H_1:\mu \neq \mu_0$ Finally, suppose that the sample size $n$ is $25$, and consider a test procedure such that $H_0$ is to be rejected if $|X_n − μ_0| ≥ c$. Determine the value of $c$ such that the size of the test will be $0.05$.

We can rewrite the probability of $P(|\bar{X}_n-\mu_0|\geq c)$ as $P(c\leq \bar{X}_n-\mu_0 \leq c)$. we can normalize it by dividing everything by $\frac{1}{\sqrt{25}}$ which gives us $P(5c\leq Z \leq 5c)$ where $Z\sim \text{norm}(0,1)$. Now we want to solve for $c$ in $P(5c\leq Z \leq 5c)$ which then we rewrite for $2(1-\Phi(5c))=0.05$ which then solves for $c=0.392$ 



### 9.1.6
Suppose that a single observation $X$ is to be taken from the uniform distribution on the interval $[θ − \frac{1}{2} , θ + \frac{1}{2}]$ and suppose the following hypothesis are tested:
$H_0: θ≤3, H_1: θ≥4$ Construct a test procedure $δ$ for which the power function has the following values: $π(θ|δ) = 0$ for $θ ≤ 3$ and $π(θ|δ) = 1$ for $θ ≥ 4$.

The test procedure that we can create that will have this power function is reject $H_0$ if $X\geq 3.5$. 
If $\theta \leq 3$ then we fail to reject the null every time, and if $\theta \geq 4$ then we reject the null hypothesis every time. 


### 9.1.8
Assume that $X_1, . . . , X_n$ are i.i.d. with the normal distribution that has mean $μ$ and variance $1$. Suppose that we wish to test the hypotheses $H_0:  μ ≤ μ_0$, $H_1:  μ > μ_0$ Consider the test that rejects $H_0$ if $Z ≥ c$, where $Z$ is defined in Eq. (9.1.10).

a. Show that $P(Z≥c|μ)$ is an increasing function of $μ$. 
Note that $P(Z\geq c|\mu)=P(\frac{\bar{X}_n-\mu_0}{\sigma/\sqrt{n}}\geq c|\mu)$
Which can further be rewritten to $P(\frac{\bar{X}_n-\mu}{\sigma/\sqrt{n}}\geq c-\frac{\mu}{\sigma/\sqrt{n}}+\frac{\mu_0}{\sigma/\sqrt{n}})$
which equals $1-\Phi(c-\sqrt{n}\mu+\sqrt{n}\mu_0|\mu)$
which taking the derivative equals $-\phi(c-\sqrt{n}\mu+\sqrt{n}\mu_0)(-\sqrt{n})$ which is a negative number times a negative number so its positive showing its increasing 

b. Find $c$ to make the test have size $α_0$.
The supermum is  $P(\frac{\bar{X}_n-\mu}{\sigma/\sqrt{n}}\geq c|\mu\in H_0)$ and since the function is increasing in $\mu$ we know that the supermum happens at $H_0$ which can rewrite as $1-\Phi(c)$ because $1-\Phi(c-\sqrt{n}\mu+\sqrt{n}\mu_0|\mu)$ which we can then solve as $1-\Phi(c)=\alpha_0$ solves for $c=\Phi^{-1}(\alpha_0-1)$


### 9.1.10
In Exercise $8$, assume that $Z = z$ is observed. Find a formula for the p-value.

$p=\text{Sup}(P(Z>z|\mu \in H_0))=1-\Phi(z)$


### 9.5.1
Use the data in Example $8.5.4$, comprising a sample of $n = 10$ lactic acid measurements in cheese. Assume, as we did there, that the lactic acid measurements are a random sample from the normal distribution with unknown mean $μ$ and unknown variance $σ^2$. Suppose that we wish to test the following hypotheses: $H_0:  μ ≤ 1.2$ , $H_1:  μ > 1.2$

a. Perform the level $α_0=0.05$ test of these hypotheses. 
We observe the following samples $0.86, 1.53, 1.57, 1.81, 0.99, 1.09, 1.29, 1.78, 1.29, 1.58$ so we get $\bar{X}_n=1.397$ and $S^2=0.1074$. Thus our test statistic is $T=\frac{\bar{X}-1.2}{0.328/\sqrt{10}}=1.73$. Then we compute $T^{-1}_{0.95}=1.83$ which means that we fail to reject $H_0$ 


b. Compute the p-value.
To calculate the p-value we solve for $P(T_{9}\geq 1.73)=0.058$ 


### 9.5.7
Consider the normal distribution with unknown mean μ and unknown variance $σ^2$, and suppose that it is desired to test the following hypotheses: $H_0:  μ ≤ μ_0$, and $H_1: \mu > \mu_0$. Suppose that it is possible to observe only a single value of $X$ from this distribution, but that an independent random sample of $n$ observations $Y_1, . . . , Y_n$ is available from the normal distribution with known mean $0$ and the same variance $σ^2$ as for $X$. Show how to carry out a test of the hypotheses $H_0$ and $H_1$ based on the $t$ distribution with $n$ degrees of freedom.

Let $X\sim \text{Norm}(\mu,\sigma^2)$ and $Y_i \sim\text{Norm}(0,\sigma^2)$. We can estimate $\sigma^2$ using the sample variance of $Y_i$, $S^2 = \frac{1}{n}\Sigma Y_i^2$ and $\frac{n S^2}{\sigma^2}\sim t_{n}$ because its the sum of $n$ standard normal distributions squared. 

Then we can standardize $X$ assuming that the $H_0$ is true becoming $\frac{X-\mu_0}{\sigma}$ and we can just use $S$ instead of $\sigma$
We can rewrite $\frac{X-\mu_0}{S}$  as $\frac{X-\mu_0/\sigma}{S/\sigma}$ by multiplying by $\frac{\sigma^{-1}}{\sigma^{-1}}$ which becomes $\frac{Z}{\sqrt{\frac{nS^2}{\sigma^2}/n}}$ once you expand it out becomes $\frac{Z}{\sqrt{U/n}}$ which is the $t$ distribution with $n$ degrees of freedom which I cannot figure out how this is the the $T$ distribution with $n$ degrees of freedom but I will ask you about in class 

