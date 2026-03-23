---
tags:
  - Pure
---
Information theory studies how do we study the information we get from a signal. 
A useful though experiment is that a binary channel with 100% noise rate is just as good as a channel with 0% noise rate(you can just encode things as the opposite). But a channel with a 50% noise rate communicates no information because it might as well be random(no matter the underlying probability distribution of 1's and 0's). 
Additionally later information theory studies how to encode data effectively using codes.

# Entropy and Information Definitions
## Self Information 
To define the amount of information an event gives us we want to define a function $S: \text{Events}\rightarrow \mathbb{R}$ such that the following hold 
1. We want the information gained from an event $A$ to depend continuously on $P(A)$
2. The higher the probability of $A$ the less information it contains. 
3. The self information of two independent event is additive. IE $S(A\cap B)=S(A)+S(B)$ if they are independent
Interestingly there is actually only one function that satisfies all of these properties which is
$$
S(A)=-\log (P(A))
$$
The base of the log can vary and changes the units in which information is measured. When you use base $2$, the units that information is measured in is bits. 

## Entropy
Entropy is a measure of uncertainty of a probability distribution. For example a fair coin toss has the entropy of $1$ bit two fair coin tosses has the entropy of $2$ bits and $n$ fair coin tosses has $n$ bits of entropy.  The formula for calculating the entropy is the average information for all possible outcomes 
$$
H(X)=\Sigma_{x\in X}P(X=x)\text{log}(P(X=x))
$$
But there is a problem where we can have an event have probability $0$ so we define $0\log(0)=0$ 
This is very similar to variance(which can be defined as $E(X-E(X)$) because this is $E(-Log(p(X))$, its the expected self information 


## Divergence
For two PMFs $P$ and $Q$ we calculate their divergence as 
$$
D(P||Q)=\Sigma\, p(x)\log (\frac{p(x)}{q(x)})
$$
with $0\log(0)=0$ and $D(P||Q)=\infty$ if there exists an element of the support of $P$ that is not in the support of $Q$. 
Interestingly this function is actually asymmetric which seems hard to deal with but can actually be nice in some cases. An example would be given $X=\{0,1\}$ and two coins $p$ and $q$ with $p(1)=0.5$ but $q(1)=1$ the divergence $D(p||q)=\infty$ but $D(q||p)=1$. This is reflected as if you got coin $p$ you would know you had it after you saw one $0$ but if you got coin $q$ you could never be certain that you didn't have coin $p$ 
This is reflected in the property that after $n$ samples the data favors $P$ over $Q$ by about $2^{nD(P||Q)}:1$ odds 


## Mutual Information 
Mutual information denoted $I(X,Y)$ is the amount of information that know $X$ tells you about $Y$. You might be thinking that this is just the same thing as correlation, but correlation only measures linear relationships. This measures how much we reduce the entropy of $X$ given we know the value of $Y$. An equation for calculating it can be written as 
$$
I(X;Y)=\Sigma \Sigma P(X=x,Y=y)\log(\frac{P(X=x,Y=y)}{P(X=x)P(Y=y)})
$$
But this can be written into $H(X)-H(X|Y)$ 
An example of this would be given two random variables modeling two flipped coins. $X$ has the values $\{00,10,01,11\}$ and $Y$ has the values $\{0,1\}$ just modeling the value of the first flipped coin. 
Note that if you knew $Y$ then the entropy of $X$ would be $1$(Seen in $H(X)-H(X|Y)=2-1=1$ ), where if you knew the value of $X$ then the entropy of $Y$ would be zero(because you now know the value of $Y$) which is seen in $H(Y)-H(Y|X)=1-0=1$.
If two random variables are independent then their mutual information is $0$
Additionally this mutual information can be expanded into conditonal information but it behaves exactly how you would expect 
## Conditional Entropy 
While conditional expected value is a function($E(X|Y=y)$ is often written in terms of $y$), conditional entropy is not, it is a singular value. It represents the expected entropy of $X$ given a random value of $Y$. Thus it is calculated using 
$$
H(Y|X)=\Sigma P(X=x)H(Y|X=x)
$$

## Conditional Divergence
Similar to conditional entropy, conditional divergence is the average divergence of $p$ and $q$ given all values of what variable is given. Thus 
$$
D(p_{x|y}||q_{x|y}|p_x)=\Sigma p_x(x)D(p_{y|x}(\cdot|x)||q_{y|x}(\cdot|x))
$$
therefore the conditional divergence is also a single number rather than a function of $X$


# Test
## Data Processing Inequality
This is fundamental to machine learning and statistical analysis. In its core it says that you can't gain any new information from processing data. For a function $f:X\rightarrow Y$ then $H(f(X))\leq H(X)$ because functions can only compress information. This can also be explained using markov chains but I don't understand that yet. 