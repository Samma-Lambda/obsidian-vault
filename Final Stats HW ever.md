![[Screenshot 2026-04-24 at 8.59.37 PM.png]]
To prove that the expected value of this function is infinite we first look at something less than the expected value $\int_{1}^n x \frac{1}{x^2}$ which is just part of the expected value formula. We find that $\int_{1}^n x \frac{1}{x^2} = \ln{n}$ which by picking higher and higher values of $n$ becomes infinite 

I would expect as we do bigger and bigger samples for the average to get bigger(I don't know how to put it formally but it would converge to infinity). But I think that it would diverge pretty slowly because the partial expected value is $\ln(n)$ 

To simulate this we need to find the CDF which is $1-1/x$. The inverse cdf is $\frac{1}{1-x}$

Here is the python code for this ![[Screenshot 2026-04-24 at 9.15.24 PM.png|600]]
and the histogram generated 
![[Figure_1.png]]



![[Screenshot 2026-04-24 at 9.18.11 PM.png]]![[Screenshot 2026-04-24 at 9.18.28 PM.png]]

Here is my code to do this 
![[Screenshot 2026-04-24 at 9.25.49 PM.png|427]]
![[Screenshot 2026-04-24 at 9.25.02 PM.png|433]]
The expected value of this is 0 so the sample mean did the best. I kinda expected k=2 to be the best because its removing the higher range 2 that are created from -10 to 10. I also expected the median to do the best because I feel like it would cause the randomness to cancel 



![[Screenshot 2026-04-24 at 9.28.24 PM.png]]

Here is my code for this ![[Screenshot 2026-04-24 at 9.37.51 PM.png]]
and i got the output 
![[Screenshot 2026-04-24 at 9.38.34 PM.png]]
Part a the output answers the question. For part b the trim2 having the lowest variance makes sense to me. I am suprised by how high the variance of the median is


![[Screenshot 2026-04-24 at 9.40.51 PM.png|483]]
![[Screenshot 2026-04-24 at 9.41.07 PM.png|481]]

Here is the code
![[Screenshot 2026-04-24 at 9.51.51 PM.png|351]]

The sample mean by the CLT will converge to $\text{Norm}(\mu,\frac{\sigma^2}{n})$ 
using stuff from earlier in the class we have a $n\%$ confidence interval is 
$\bar{\mu}\pm\Phi^{-1}(0.995)\frac{\sigma}{\sqrt{n}}$. With our estimates of $\sigma^{\prime}=\sqrt{1.212}$ we get a confidence interval of $1.32\pm \Phi^{-1}(0.995)\frac{\sqrt{1.212}}{\sqrt{n}}$  we need $\Phi^{-1}(0.995)\frac{\sqrt{1.212}}{\sqrt{n}}=0.01$ which we solve for and get $(\Phi^{-1}(0.995)\frac{\sqrt{1.212}}{0.01})^2=n$


![[Screenshot 2026-04-24 at 10.10.47 PM.png|477]]
We can notice that if $X\sim \text{Expo}(1)$ then our intergral is $E[\log(1+X)]$ 
Here is the code for part a
![[Screenshot 2026-04-24 at 10.22.34 PM.png]]
which gave the output 
![[Screenshot 2026-04-24 at 10.22.52 PM.png]]


to do part b what we are doing is the intergral of 
$\int\frac{\ln(1+x)e^{-x}}{g(x)}g(x)dx$ which is just $E[\frac{\ln(x+1)e^{-x}}{g(x)}]$ in our case the $g(x)$ is the pdf of our gamma random variable. Writing out $g(x)$ fully we can actually simplify it $E[\frac{\ln(x+1)e^{-x}}{g(x)}]=E[\Gamma(1.5)\frac{\ln(1+x)}{\sqrt{x}}]$ where $x$ is a gamma random variable. We use the approximation that $\frac{\sqrt{\pi}}{2}=\Gamma(1.5)$ and use the linearity of expectation to find that $\frac{\sqrt{\pi}}{2}E[\frac{\ln(x+1)}{\sqrt{x}}]$ we then simulate this a bunch of time  ![[Screenshot 2026-04-24 at 11.34.30 PM.png]]
which gave the output 
![[Screenshot 2026-04-24 at 11.34.54 PM.png]]
which has a standard error of about a four of the other way

method b appears to be more efficient due to the fact that the standard error was lower. I don't fully understand why these methods are different. I think its more stable becuase $\ln(1+x)$ where $x$ is from the exponential has higher variance then $\frac{ln(1+x)}{\sqrt{x}}$ where $x$ is $\text{gamma}(1.5,1)$

![[Screenshot 2026-04-29 at 11.12.24 AM.png]]
Parametric bootstrap is where you get some data, and then fit some distribution to the data using an estimate of the parameters. Then you do simulations using that distribution, and study the distribution of some statistic of your simulations. 
In our case we have sample samples from an exponential distribution ![[Screenshot 2026-04-29 at 11.29.20 AM.png|363]] 
and I got a variance of 0.073

![[Screenshot 2026-04-29 at 11.30.18 AM.png|504]]
![[Screenshot 2026-04-29 at 11.31.39 AM.png]]
Here is my code 
![[Screenshot 2026-04-29 at 11.40.14 AM.png|237]]

I got the first one seems scewed left and the second one seems better but a little scewed right. The last one seems the best it is the most centered around our datas true median 