## 8.1.2
Suppose that a random sample is to be taken from the normal distribution with unknown mean $θ$ and standard deviation $2$. How large a random sample must be taken in order that $E_θ(|X_n − θ |^2) ≤ 0.1$ for every possible value of $θ$?
First we normalize it(which we can do because of the linearity of expectation) by dividing by $(\frac{\sigma}{\sqrt{n}})^2$ resulting in this equation becoming $E[Z^2]\leq \frac{0.1}{(\frac{\sigma}{\sqrt{n}})^2}$ where $Z$ is standard normal squared. It is known that $E[Z^2]=1$ thus we can solve for $n$ getting $40 \leq n$


## 8.1.3
For the conditions of Exercise $2$, how large a random sample must be taken in order that $E_θ (|X_n − θ |) ≤ 0.1$ for every possible value of $θ$?
$E_θ (|X_n − θ |) ≤ 0.1$ which we normalize similarly to the previous one seeing that $E(\frac{|X_n-\theta|}{\frac{\sigma}{\sqrt{n}}})\leq \frac{0.1}{\frac{\sigma}{\sqrt{n}}}$ which we can then solve for $E(\frac{|X_n-\theta|}{\frac{\sigma}{\sqrt{n}}})=\int_{-\infty}^{0}z\phi(z)+\int_{0}^{\infty}z\phi(z)$ which we can solve for u substitution which I will not include finds this to be $2$ which then results in $20 \leq n$ 


## 8.1.4
For the conditions of Exercise 2, how large a random sample must be taken in order that $P(|\bar{X_n} − θ| ≤ 0.1) ≥ 0.95$ for every possible value of $θ$ ?
we know that $\bar{X}_n \sim \text{Norm}(\theta,\frac{4}{n})$ thus to normalize this probability we do $\frac{|\bar{X}_n - \theta|}{2/\sqrt{n}}\leq \frac{0.1}{2/\sqrt{n}}$. Now that we normalized this we want to find $P(-0.05\sqrt{n}\leq Z \leq 0.05\sqrt{n})=2\Phi(0.05\sqrt{n})-1$ which can further rearrange to $\Phi(0.05\sqrt{n})\leq 0.975$ which we recognize that $2$ so we have the equation $0.05\sqrt{n}\leq 2$ which we then solve for $n=(\frac{2}{0.05})^2$ which $n=1600$ 


## 8.2.4
Suppose that a point $(X, Y)$ is to be chosen at random in the xy-plane, where $X$ and $Y$ are independent random variables and each has the standard normal distribution. If a circle is drawn in the xy-plane with its center at the origin, what is the radius of the smallest circle that can be chosen in order for there to be probability $0.99$ that the point $(X, Y)$ will lie inside the circle?

$X,Y \sim \text{Norm}(0,1)$. We can define a new random variable $W=X^2+Y^2$ which is a chi squared distribution with two degrees of freedom. Thus we want to find $P(\chi_2 ^2\leq r)\leq 0.99$ which we find to be $r=9.21034$ so our answer is $r=\sqrt{9.21032}$



## 8.2.6
When the motion of a microscopic particle in a liquid or a gas is observed, it is seen that the motion is irregular because the particle collides frequently with other particles. The probability model for this motion, which is called Brownian motion, is as follows: A coordinate system is chosen in the liquid or gas. Suppose that the particle is at the origin of this coordinate system at time $t = 0$, and let $(X, Y, Z)$ denote the coordinates of the particle at any time $t > 0$. The random variables $X$, $Y$ , and $Z$ are i.i.d., and each of them has the normal distribution with mean $0$ and variance $σ^2t$. Find the probability that at time $t = 2$ the particle will lie within a sphere whose center is at the origin and whose radius is $4σ$ 

Similarly we solve for $P(\sqrt{X^2+Y^2+Z^2}\leq 4\sigma)$ which simplifies to $P(X^2+Y^2+Z^2\leq 16\sigma^2)$. Now if we can make this the sum of $n$ normalized normal distributions ew can express this as chi squared. Thus $P(\frac{X^2+Y^2+Z^2}{2\sigma^2}\leq 8)$ which is $P(\chi^2_3\leq 8)=0.9539$ 

## 8.2.10
Suppose that six random variables $X_1, . . . , X_6$ form a random sample from the standard normal distribution, and let $Y=(X_1+X_2+X_3)^2 +(X_4+X_5+X_6)^2$. Find $c$ such that $cY$ will have a $\chi^2$ distribution.
Lets define two new random variables $M=X_1+X_2+X_3$ and $D=X_4+X_5+X_6$. Note that $E[M]=0$ and $\text{Var}(M)=3$ thus to normalize this we need to divide by the standard deviation $\sqrt{3}$ to make $\frac{M}{\sqrt{3}},\frac{D}{\sqrt{3}}\sim \text{Norm}(0,1)$. Thus $(\frac{M}{\sqrt{3}})^2+(\frac{D}{\sqrt{3}})^2$ is a chi squared distribution thus we need $c=\frac{1}{3}$ 

## 8.3.4
Suppose that the random variables $X_1$, $X_2$, and $X_3$ are i.i.d., and that each has the standard normal distribution. Also, suppose that
$Y_1 = 0.8X_1 + 0.6X_2$
$Y_2 = \sqrt{2}(0.3X_1 − 0.4X_2 − 0.5X_3)$
$Y_3 = \sqrt{2}(0.3X_1 − 0.4X_2 + 0.5X_3)$
Find the joint distribution of $Y_1$, $Y_2$, and $Y_3$.

The since the sum of normal distributions is a normal distribution, we know that the joint distribution of these $Y_i$'s is a multivariate normal. The parameters of a multivariate normal is the three means and then the covariance matrix. 
Finding the three means is easy because of the linearity of expectation all the means are $0$. Then for calculating the covariance, we find that the covariance matrix is the identity matrix 




## 8.3.6
Suppose that $X_1, . . . , X_n$ form a random sample from the normal distribution with mean $μ$ and variance $σ^2.$ Assuming that the sample size $n$ is $16$, determine the values of the following probabilities:

 a. $P(\frac{1}{2}\sigma^2\leq \frac{1}{16} \Sigma(X_i - \mu)^2\leq 2\sigma^2)$
This can be rewritten into the form $P(8\leq \Sigma_{i=1}^{n}(X_i-\mu)\frac{1}{\sigma^2}\leq 32)$. Looking at the center of that equation we have a $\chi^2$ distribution with $16$ degrees of freedom. We can calculate using R to find that $P(8\leq \chi^2_{16}\leq 32)=0.939$ 

 b. $P(\frac{1}{2}\sigma^2\leq \frac{1}{n} \Sigma_{i=1}^{n}(X_i - \bar{X}_n)^2\leq 2\sigma^2)$
The sample variance is $S^2=\frac{1}{n-1}(X_i - \bar{X}_n)^2$ we have $\Sigma_{i=1}^{n}(X_i - \bar{X}_n)^2=(n-1)S^2$ 
So we can rewrite our equation as $P(\frac{1}{2}\sigma^2\leq \frac{n-1}{n} S^2\leq 2\sigma^2)$. We can rewrite it again to $n/2\leq \frac{(n-1)S^2}{\sigma^2}\leq 2n$ which $\frac{(n-1)S^2}{\sigma^2}\sim \chi_{n-1}^2$ and $n=16$ this we can solve for $P(8\leq \chi^2_{15}\leq32)=0.9935-0.076$ which looks right because they are roughly equal to the previous problem 