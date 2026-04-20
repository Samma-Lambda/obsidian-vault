---
tags:
  - Pure
---
This section will be things that are universally shared between discrete probability and continuous probability. It is mostly on probability distributions which model the range of values something random can take and the likelihood of it taking that specific value 

# Introductory Definitions
## Probability Space 
A probability space is composed of two components a sample space $S$ and a probability function $P:\mathcal{P}(S)\rightarrow [0,1]$. Additionally it must follow two axioms
1. $P(S)=1$ and $P(\emptyset)=0$ AKA the probability of something happening in our sample space is $1$
2. For any partition of $S$ called $\{A_i\},i\in \Omega$ where $\Omega$ is an index set. $P(\bigcup \{A_i\})=1$

These axioms result in a few convenient properties 
1. $P(A^c) = 1 - P(A)$ 
2. if $A\subseteq B$ then $P(A)\leq P(B)$ 
3. $P(A\cup B)=P(A)+P(B)-P(A\cap B)$ This can be extended using the usual inclusion exclusion rules to handle even more sets 

## Conditional Probability 
Often in the real world we be interested how additional information effects the chance of a specific outcome. An example might be how a specific gene changes the likelihood of specific illness.
The conditional probability is denoted $$P(A|B)=\frac{P(A\cap B)}{P(B)}$$
This can be thought of as what is the probability of $A$ if we know that an event in $B$ will happen. This formula is derived by finding the probability $A$ and $B$ happen and then properly scaling it by the "size" of $B$.
Like the previous part of the notes we can derive a few useful rules from this like $P(A\cap B)=P(B)P(A|B)=P(A)P(B|A)$ or in the following section 

## Independent Events 
Intuitively two events are independent if knowing one happened gives you no information over whether the other one happened. Formally this is defined as 
$$
P(A\cap B)=P(A)P(B)
$$
This is also equivalent to $P(A|B)=P(A)$

## Random Variables 
Random variables are a function from our sample space into a measurable space. For the most part this is mapping into $\mathbb{R}$. An example of a random variable might be the number of heads in $n$ coin tosses or the IQ of a randomly picked person. 


# Problem Solving Techniques
## Law of the Unconscious Statistician 
The Law of the Unconscious Statistician or LOTUS is a way of calculating the expected value of a random variable once a function has been applied to it. It states
$$
E(g(x))=\Sigma_{x_i\in\text{Support}}P(X=x_{i})g(x)
$$
Or this alternative formula in the continuous state
$$
E(g(x))=\int_{-\infty}^{\infty}g(x)f(x)dx
$$
## Law of Total Probability 
This is one of the most important properties of probability. For a given partition $\{A_1,...,A_n\}$ and an event $B$ we see that $P(B)=P(B|A_{1})+...+P(B|A_n)$. This allows you to break down a probability problem into smaller easier probability problems 

## Bayes' Rule 
Bayes' rule states the following 
$$
P(A|B)=\frac{P(A)P(B|A)}{P(B)}
$$
This lets you switch conditional probabilities in a useful way 

An example would be if you have two possible coins $C_1$ with $\{H:0.9,T:0.1\}$ and $C_2$ with $\{H:0.5,T:0.5\}$. We see the string of flips $HHH$ and we want to calculate $P(C_1|HHH)$ we can instead calculate $\frac{P(C_1)P(HHH|C_1)}{P(HHH)}$. This is way easier to calculate because all of these are know(but you will have to use LOTP to solve the denominator). 

## Indicators
Indicators seem stupid at first but are incredibly useful an indictor for an event denoted $I_A$ equals $1$ if the event happens and $0$ if the event does not. This makes indictors have some nice properties 
1. $(I_A)^k=I_A$
2. $I_{A^c}=1-I_A$
3. $I_{A\cap B}=I_{A} I_{B}$ 
4. $I_{A\cup B}=I_{A}+I_{B}-I_{A\cap B}$ 
5. $P(A)=E(I_A)$ 
If we want to find the expected value of $X$ and we can write it as a sum of simpler indicators then it is way easier to solve the the expected value of $E(X)=E(I_1)+E(I_2)+...+E(I_n)$.
An example of this would be the number of distinct birthdays among $n$ people, rather than doing a complicated counting argument instead write the number of distinct birthdays as $X=I_1+...+I_{365}$ we can then easily calculate $E(I_1)=1-(\frac{364}{365})^n$  

## Change of Variables 
This is a way of finding the PDF of random variable when it it expressed as a monotonic(monotonic). Formally its expressed 
$$
f_y(y)=f_x(x)|\frac{dx}{dy}|
$$
An example of this would be if $X\sim \text{Expo}(1)$ and $X^7=Y$ then we can find $f_y(y)$ by finding $|\frac{dx}{dy}|$(by writing $X$ as in terms of $Y$ and then differentiating it with respect to $Y$) and the $f_x(x)$ is known 

## Convolutions
When given two independent random variables $X$ and $Y$ often we want to be able to define a PDF for the random variable $T=X+Y$ we are able to do this using convolutions. For the discrete case the formula is 
$$
P(T=t)=\Sigma_x P(Y=t-x)P(X=x)
$$
and for the continuous case the formula is 
$$
P(T=t)=\int_{-\infty}^{\infty}P(Y=t-x)P(X=x)dx
$$
## Moment Generating Functions
The moment generating function of a random variable is defined as $M(t)=E[e^{Xt}]$. If you calculate $M^{(n)}(0)$ we then get the value $E[X^{n}]$. This may seem difficult but sometimes it can make calculating the $n$th moment way easier. Additionally it is used in Chernoff Bounds which are incredibly useful. Sometimes you are able to explicitly calculate the value of the $n$th moment as a simple function, but this can be very difficult to do. 





# Descriptors of Distributions
## Expected Value
Expected value is the average statistic you can expect to get long run per trial. The expected value does not need to be in the support of a distribution, for example in a Bernoulli the support is $\{0,1\}$ but the expected value is $p$. 
The expectation of a discrete probability space is 
$$
	E(X)=\Sigma_{x_i\in\text{Support}}x_iP(X=x_i)
$$
Where the expectation of a continuous probability space is 
$$
E(X)=\int xf(x)dx
$$


A simple example might be when rolling a dice the expected value of the roll would be $3.5$ which is derived from $\frac{1}{6}(1+...+6)$. Another interpretation is that it is the center of mass of the PMF. It has a few nice properties 
1. $E(aX)=aE(X)$
2. $E(X+Y)=E(X)+E(Y)$ 

## Variance 
This is a measure of how spread out your values are. Formally it is defined as the expected squared deviation away from the mean. It has two formulas 
$$
\text{Var}(X)=E(X-E(X))
$$
or 
$$
	\text{Var}(X)=E(X^2)-E(X)^2
$$
Often this will require using LOTUS to be able to find.
Variance has the following nice properties 
1. If $X$ and $Y$ are independent $\text{Var}(X+Y)=\text{Var}(X)+\text{Var}(Y)$
2. $\text{Var}(X+c)=\text{Var}(X)$ because we are making it centered at zero before the calculation 
3. $\text{Var}(cX)=c^2\text{Var}(X)$ 


## Covariance/Correlation 
This is a measure of how much two random variables are related to each other. It works by normalizing the points so the centroid of the shape is $(0,0)$ and then counting then looking at the number of variables in the first and third quadrant. There are two formulas for this the first of which is 
$$
\text{Cov}(X,Y)=E((X-E(X))(Y-E(Y)))
$$
Or the computational 
$$
	\text{Cov}(X,Y)=E(XY)-E(X)E(Y)
$$
You may realize that this number is unbounded, which brings us to correlation which is bounded between $[-1,1]$ 
ITS IMPORTANT TO NOTE THAT THIS MEASURES HOW THEY RELATE TO EACH OTHER LINEARLY


## Entropy
The entropy of single event $x_i$ is calculated using $-\text{log}_2(p_i)$. This formula is not derived it is defined this way so that 
1. Independant events have additive information
2. Less common events have more information than common events(If something always happens than it has no information) an example would be that the sunrises tomorrow, knowing this gives me almost no information

The entropy of a probability distribution if the expected entropy of all events and can be concisely written as $\Sigma p_i (\text{log}_2(p_i))$. Interestingly it also gives a lower bound on the number of bits required to encode the this setting. 



# Types of Convergence in Statistics
There are a few different types of convergence in probability.
## Converges in Probability
A sequence of random variables $X_n$ converges in probability to a value $x$ if $P(|X_n-x|)<\epsilon$  $\forall \epsilon >0$ as $n\rightarrow \infty$. An example of this would be if you let $X_n$ be the proportion of heads in $n$ coin tosses

## Almost Sure convergence
This is where $n\rightarrow \infty$ we see that $P(X_n=x)=1$ where $x$ is just some value. An example of this would be having a head before the $n$th flip 

## Converges in Distribution
This is where as $n\rightarrow \infty$ a distribution converges to another distribution. An example of this would be the binomial random variable $\text{Bin}(n,\frac{\lambda}{n})$ as $n\rightarrow \infty$ converging to the poisson distribution 

# Notable Convergences
## Law of Large numbers
This states that the sample mean of i.i.d random variables $\bar{X}_n$ converges in probability to $E[X]$ as $n\rightarrow \infty$. This is proven using chebyshev's inequality 
## Central Limit Theorem
This states that the distribution of the sum of $n$ i.i.d random variables will converge to the normal distribution. This can be proven in a complicated way using MGFs
## Binomial to Poisson 
When you take a binomial random variable $\text{Bin}(n,\frac{\lambda}{n})$ as $n\rightarrow \infty$ it converges to the poisson distribution 


# Notable Inequalities
A common effect within statistics is that the estimation of things because better as you get more data. For example the sample mean becomes more and more reliable as the sample size gets larger and larger(because the variance of its distribution gets smaller). 
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
This is another specific case of Markov's Inequality. We start with 
$$P(X>a)=P(e^{tX}>e^{ta})\leq \frac{E[e^{tX}]}{e^{ta}}=\frac{M_{X}(t)}{e^{ta}}$$
Where $M_X(t)$ is the moment generating function of $X$. This may seem arbitrary but this holds for any $t>0$ so you get to find the minimal $t$ value.  
## Jensen's Inequality
This is proven using a Taylor approximation of function. For any convex function we have 
$$
E[f(x)]\geq f(E[x])
$$
You can prove this using the Taylor expansion, but I am not including the proof 


# Next
Now that we have gone over the basics of overall probability we are now going to divide it into discrete probability and continuous probability
[[Discrete Probability]]
[[Continuous  Probability]]
[[Information Theory]]
[[Statistics]]