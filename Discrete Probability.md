---
tags:
  - Pure
---
Discrete probability is exactly what it sounds like, when there are a finite number of outcomes discrete probability is at play

There are some often occurring patterns in discrete random variables called distributions beneath is a list of distribution and their descriptions
# Distributions
## Bernoulli 
**Support:** $\{0,1\}$
**Expected Value:** $p$
**Parameters:** $p$ the probability of success
**PMF:** $$ P(k) = p^{\,k}(1-p)^{\,1-k}$$
**Description:** This is the probability distribution a single Bernoulli trial follows, this could be a single coin flip or a single lottery ticket. Additionally the PMF looks weird but you'll notice it works out when $k$ is $0$ or $1$  

## Binomial 
**Support:** $\{0,...,n\}$
**Expected Value:** $np$
**Parameters:** $p$ the probability of success $n$ the number of trials
**PMF:** $$P(k)=\binom{n}{k}p^k(1-p)^{n-k}$$
**Description:** This is the distribution that counts the number of successes of a series of $n$ Bernoulli trials. The PMF can be derived by permuting $k$ successes and $n-k$ failures. Often this is thought of as sampling with replacement.
For large enough number of trials it can be quicker to do a poisson approximation, as the poisson distribution is the binomial distribution as it goes to infinity 

## Poisson 
**Support:** $\{0,1,...,\infty\}$
**Expected Value:** $\lambda$
**Parameters:** $\lambda$ the rate of successes(average rate in the real world)
**PMF:** $$ P(k) = \frac{\lambda^ke^{-\lambda}}{k!}$$
**Description:** An example of this would be if I got one email an hour, I could have it binned by the hour and then I could get anywhere from $0$ to $1$ emails. But I could bin it by $15$ minutes and then I could get from $0$ to $4$ emails. This creates a binomial distribution. The poisson distribution comes from the allowing the size of the bins to be infinitely small but holding the expected value of the number of emails I get the same. This is often useful when it comes to modeling things like time. n


## Hypergeometric 
**Support:** $\{\text{max}(0,n+K-N),...,\text{min}(n,K)\}$
**Expected Value:** $n \frac{K}{N}$
**Parameters:** $N$ population size, $K$ number of success states, $n$ is the number of draws
**PMF:** $$P(k)=\frac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{k}}$$
**Description:** Where the binomial distribution represents the number of successes when drawing with replacement, this represents drawing without replacement. 

## Connection between Hypergeometric and Binomial 
As you increase the population size of a hypergeometric while keeping the ratio of successes and failures the same it converges to be a binomial distribution. This is why when we sample from a large population we just treat it like a binomial. 
Additionally if we have $X\sim \text{Binom}(n,p)$ and $Y\sim \text{Binom}(m,p)$ if we condition on $X+Y=r$ we get a hypergeometric distribution $\text{Hgeom}(n,m,r)$.
This allows us to derive the [[Fisher Exact Test]]

## Geometric Distribution
**Support:** $\{0,1,2 ...\}$
**Expected Value:** $\frac{1-p}{p}$ 
**Parameters:** $p$ the probability of success
**PMF:**
$$
P(k)=(1-p)^kp
$$
**Description:** This distribution measures the number of failures until the first success. It is closely related and pretty much the same thing as the first success distribution. If $X$ is geometric then $X+1$ is the first success distribution 

## Negative Binomial Distribution
**Support:** $\{0,1,2 ...\}$
**Expected Value:** $r(\frac{1-p}{p})$ 
**Parameters:** $p$ the probability of success and $r$ is the number of successes allowed 
**PMF:**
$$
P(k)=\binom{k+r-1}{k}(1-p)^kp^r
$$
**Description:** This is the distribution that describes the likely-hood of getting $n$ failures before the $r\text{th}$ success 


For a given discrete probability distribution we can find the "distance" between then using KL divergence 


# Multinomial



# Applications
This is how you measure the distance between two discrete probability distributions, and a design of a cost function that works well for classification. 
[[KL Divergence-Cross Entropy Loss Function]]