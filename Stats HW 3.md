u### 7.4.2
Suppose that the proportion $\theta$  of defective items in a large shipment is unknown, and the prior distribution of $θ$ is the beta distribution for which the parameters are $α = 5$ and $β = 10$. Suppose also that $20$ items are selected at random from the shipment, and that exactly one of these items is found to be defective. If the squared error loss function is used, what is the Bayes estimate of $θ$?
When you use the bayes estimate with the squared error loss function, it always returns the expected value of the posterior distribution. Because the beta distribution is a conjugate prior of the binomial distribution, so we know that the parameters of the posterior distribution. Out posterior distribution would be $\text{Beta}(\alpha = 6,\beta = 29)$ and then the expected value is $\frac{6}{35}$. This our bayes estimate of $\theta$ is $\frac{6}{35}$ 


### 7.4.3
Consider again the conditions of Exercise $2$. Suppose that the prior distribution of $θ$ is as given in Exercise $2$, and suppose again that $20$ items are selected at random from the shipment.
the variance of theta is the mean squared error $\text{Var}(\theta)=\text{Var}(\text{Beta}(5+x,30-x)=\frac{(5+x)(30-x)}{35^2\cdot 36}$ but since we care amount maximizing and minimizing this we see that $\text{Var}(\theta)\propto (5+x)(30-x)$ 

For what number of defective items in the sample will the mean squared error of the Bayes estimate be a maximum?
The variance is maximized when the equation is a square so we solve for $5+x=30-x$ and get $x=12.5$ so the mean squared error of the bayes estimator is maximized when $x=12,13$ 


For what number will the mean squared error of the Bayes estimate be a minimum?
The variance is minimized at the extremes so it is either $x=0,20$ 



### 7.4.8
Suppose that the heights of the individuals in a certain population have a normal distribution for which the value of the mean $θ$ is unknown and the standard deviation is $2$ inches. Suppose also that the prior distribution of $θ$ is a normal distribution for which the mean is $68$ inches and the standard deviation is $1$ inch. Suppose finally that $10$ people are selected at random from the population, and their average height is found to be $69.5$ inches.
$H\sim \text{norm}(\theta,2)$ and $\theta \sim \text{norm}(68,1)$. We know from question $7$ the posterior is $\theta \sim \text{norm}(69.07,\frac{2}{7})$ 
a)If the squared error loss function is used, what is the Bayes estimate of $θ$?
the squared error gives $E[\theta]$ which is just $69.07$ 

b)If the absolute error loss function is used, what is the Bayes estimate of $θ$?
because it is the normal distribution the mean, median and mode are all the same so it would be $E[\theta]$ again. 




### 7.4.9 
Suppose that a random sample is to be taken from a normal distribution for which the value of the mean $θ$ is unknown and the standard deviation is $2$, the prior distribution of $θ$ is a normal distribution for which the standard deviation is $1$, and the value of $θ$ must be estimated by us- ing the squared error loss function. What is the smallest random sample that must be taken in order for the mean squared error of the Bayes estimator of $θ$ to be $0.01$ or less? (See Exercise 10 of Sec. 7.3.)

$X_i \sim \text{norm}(\theta,4)$, $\theta \sim \text{norm}(\mu_0,1)$ 
The $MSE(\hat{\theta})=\text{Var}(\theta|x)=(\frac{1}{1^2}+\frac{n}{4})^{-1}$ 
$\frac{1}{1+\frac{n}{4}}\leq 0.01$ 
which then solves to be $n=396$ 



### 7.5.2
It is not known what proportion $p$ of the purchases of a certain brand of breakfast cereal are made by women and what proportion are made by men. In a random sample of $70$ purchases of this cereal, it was found that $58$ were made by women and $12$ were made by men. Find the M.L.E. of $p$.
Intuitively you would expect $\frac{12}{70}=p$ because the MLE maximizes the chance of seeing the data. If you want I derived it and it takes a while to write out but I did get $p=\frac{58}{70}$


### 7.5.3
Consider again the conditions in Exercise $2$, but suppose also that it is known that  $\frac{1}{2}≤p≤ \frac{2}{3}$.If the observations in the random sample of $70$ purchases are as given in Exercise $2$, what is the M.L.E. of $p$?
Because we can't have the optimal value and the derivative shows us that it is strictly increasing towards the maxima we will have $p=\frac{2}{3}$


### 7.6.2
Suppose that $X_1, . . . , X_n$ form a random sample from a Poisson distribution for which the mean is unknown. Determine the M.L.E. of the standard deviation of the distribution.
Let $X_i\sim \text{Poisson}(\lambda)$ note that the standard devation is the square root of $\lambda$ in the poisson distribution. Thus our likelyhood of lambda is $L(\lambda)=\Pi^{n} \frac{e^{\lambda} \lambda^{x_i}}{x_i!}$ which we can take the log of which results in $-n\lambda+\Sigma x_i \text{ln}\lambda$  plus some constants. when we take the derivative of this we get $-n+\frac{\Sigma x_i}{\lambda}=0$ which we solve for and get $\lambda$ is the average
Then we can use the theorem about bijections and MLEs and get $\sqrt{\text{average}}$ as our optimal value 


### 7.6.4
Suppose that the lifetime of a certain type of lamp has an exponential distribution for which the value of the parameter $β$ is unknown. A random sample of n lamps of this type are tested for a period of $T$ hours and the number $X$ of lamps that fail during this period is observed, but the times at which the failures occurred are not noted. Determine the M.L.E. of $β$ based on the observed value of $X$. 

For a singlular lamb the $P(\text{fails before T})=1-e^{-\beta T}$ which then makes the collection a binomial with $\text{binom}(n,p(\beta))$. Then the likelyhood function is $(1-e^{-\beta T})^{X}(e^{-\beta T})^{n-X}$ we take the log of this and get $X\text{ln}(1-e^{\beta T})-(n-x)\beta T$ which we differentiate and set to zero. Getting us $X\frac{T e^{-\beta T}}{1-e^{-\beta} T}-(n-X)\beta T$ which we solve for and get $\beta = \frac{1}{T}\text{ln}(\frac{n-X}{n})$  