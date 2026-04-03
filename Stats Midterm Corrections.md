#### Problem 1c)
$P(\bar{X}_n\geq \frac{2}{\sqrt{n}}+2)=P(\frac{\bar{X}_n-2}{2/\sqrt{n}}\geq 1)$ note that $\frac{\bar{X}_n-2}{2/\sqrt{n}}$ converges to the normal distribution according the CLT thus $P(\frac{\bar{X}_n-2}{2/\sqrt{n}}\geq 1)\approx 1-\Phi(1)$ 

#### Problem 2b)
The expected value of the prior distribution is $\frac{\alpha}{\alpha+\beta}$ 
The sample proportion is $\frac{\Sigma_{i=1}^{n} X_i}{n}$ 
The bayes estimator is $\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha + \Sigma_{i=1}^{n}X_i+\beta+ n - \Sigma_{i=1}^{n}X_i}=\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha +\beta+ n}$ 

we need to solve the equation to show  $c_1 \frac{\alpha}{\alpha+\beta}+c_2 \frac{\Sigma_{i=1}^{n} X_i}{n}=\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha +\beta+ n}$
we can see that $c_1 = \frac{\alpha+\beta}{\alpha+\beta+n}$ and $c_2 = \frac{n}{\alpha+\beta+n}$ are the constants by plugging them in $\frac{\alpha+\beta}{\alpha+\beta+n}\frac{\alpha}{\alpha+\beta}+\frac{n}{\alpha+\beta+n}\frac{\Sigma_{i=1}^{n} X_i}{n}=\frac{\alpha+\Sigma_{i=1}^{n}X_i}{\alpha +\beta+ n}$. Thus the bayes estimator is the weighted average of the sample proportion and bayes estimator 



#### Problem 3a)
$Y_n/\theta \sim \text{beta}(n,1)$ because it it is the maximum of $n$ standard uniforms. The expected value of the beta distribution is $\frac{\alpha}{\alpha+\beta}$ thus the the expected value is $\frac{n}{n+1}$ 


#### Problem 3b)
i) The cdf of $Y_n$ given $\theta$ is $1-(y/\theta)^n$ so therefore the the pdf of $Y_n$ is $n y^{n-1}/\theta^{n}$ which is proportional to $\theta^{-n}$. Note that $\theta^{-n}$ is decreasing with respect to $n$ thus the MLE estimate would be $Y_n$

ii) We are using the improper prior $\frac{1}{\theta}$ because it includes all values of $[0,\infty)$. Note that $P(\theta|Y_n)\propto\theta^{-n}\frac{1}{\theta}$. We need $\int_{y}^{\infty}c\theta^{-(n+1)}=1$ which we then solve for $c$. We get $c\frac{\theta^{-n}}{-n}|_{y}^{\infty}=1$ which means that $c\frac{y^{-n}}{n}=1$ meaning $c=ny^n$. Thus $P(\theta|Y_n)=ny^{-n}\theta^{-(n+1)}$ which we need to find the expected value of $\theta$. We see that the $\int_{y}^{\infty}\theta ny^n \theta^{-(n+1)}d\theta=ny^n \int_{y}^{\infty}\theta^{-n}d\theta=\frac{ny}{n-1}$    

#### Problem 3c)
The MLE is biased because it will always be less than $\theta$. This is because it estimates $\theta$ as $Y_n$ and $Y_n$ will always be less than $\theta$ because the probability of some $X_i=\theta$ is zero. 
The MLE is consistent because it estimates $\theta$ as $Y_n$ and as $n$ goes to infinity $Y_n$ approaches $\theta$. This is because the probability you have not seen a value above a specific number less than $\theta$ exponentially decays 

The bayesian estimator is $\frac{n}{n-1}y$ which as $n$ goes to infinity $\frac{n}{n-1}$ converges to $1$ and $y$ converges to theta as $n$ goes to infinity. Thus the estimator is consistent

The expected value of $Y_n$ is $\frac{n}{n+1}\theta$ because of the aces dividing the deck, so we would expect $\mathbb{E}[\hat{\theta}]$ to be $\frac{n}{n-1}\frac{n}{n+1}\theta=\frac{n^2}{n^2-1}\theta$. Note that $\frac{n^2}{n^2-1}\theta -\theta \neq 0$ thus the estimator is biased  


#### Problem 3d)
Using the posterior distribution $P(\theta|Y_n)=ny^{-n}\theta^{-(n+1)}$ and $n=4$ and $Y_n = 10$ find a $95\%$ confidence interval. We need to look at the cdf $1-(y/\theta)^n$ and find where $1-(10/\theta)^4 = 0.025$ and $1-(10/\theta)^4 = 0.975$. Solving these we get a lower bound of $10.06349525$ and upper bound of $25.14866$. 

#### Problem 4a) 
We know that $\frac{\sqrt{n}(\bar{X}_n-\mu_0)}{\sigma^{\prime}}\sim t_{n-1}$. Thus we know that $P(\frac{\sqrt{n}(\bar{X}_n-\mu_0)}{\sigma^{\prime}}\leq T^{-1}_{n-1}(1-\alpha))=1-\alpha$    