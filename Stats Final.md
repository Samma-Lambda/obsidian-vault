![[Screenshot 2026-05-05 at 10.05.24 PM.png]]
a) the likilyhood is the probability of having a specific value of $\beta$ given some observations. Thus the likelyhood in this situation is $\Pi \frac{1}{\beta}e^{-x/\beta}$, the log likelyhood is just $\log(\Pi \frac{1}{\beta}e^{-x/\beta})$. This simplifies nicely as  $\Pi \frac{1}{\beta}e^{-x/\beta}=(\frac{1}{\beta})^n e^{-\Sigma x_i/\beta}$ also logs cancel e. Thus $\log(\Pi \frac{1}{\beta}e^{-x/\beta})=n\log(\frac{1}{\beta})+-\Sigma x_i/\beta=-n\log(\beta)+-\Sigma x_i/\beta$ . 

b) now to find the MLE of this we take the derivative of this with respect to $\beta$ which gives us $\frac{-n}{\beta}+\frac{\Sigma x_i}{\beta^2}$ we set it to zero to get the maxima getting $\frac{-n}{\beta}+\frac{\Sigma x_i}{\beta^2}=0$ which we mulitply by $\beta^2$ to get $-n\beta=-\Sigma x_i$ which can be arranged to be $\beta = \Sigma x_i/n=\bar{X_i}$

c) an estimator is unbiased if $E[\hat{\beta}]=\beta$. because the MLE is $\bar{X}=\frac{1}{n}\Sigma X_i$ meaning that $E[\beta]=E[\bar{X}]=\frac{1}{n}E[\Sigma X_i]=n\frac{1}{n}E[X_i]=\beta$ which means its unbiased 

![[Screenshot 2026-05-05 at 10.16.46 PM.png]]
a) The CDF is just $\int f(x)$ which works to be $x^3$ capped at $1$

b) Using the universaility of the uniform we can simulate it. Because the percentile of a random observation is uniform, we can use $F^{-1}(U)=X$. This works because $F^{-1}$ brings percentiles to values in our distribution. Also $F^{-1}=x^{\frac{1}{3}}$  

c) our simulated value of $X=(0.512)^{1/3}$

![[Screenshot 2026-05-05 at 11.47.08 PM.png]]
a) we sample with replacement $5$ values and then compute the median. We store all these medians and then calculate the standard error amoung them to estimate the standard error of the medians 
b) we would estimate $\beta$ somehow and then generate data with that distribution. Then we would compute the median using the generated data and then see the standard error of the median 
c) If I knew the distribution or strongly suspected the data was from a specific distribution(possibly using tests to see if that is reasonable) then I would use a parametric method. Otherwise not I would use non-parametric 



![[Screenshot 2026-05-05 at 10.28.46 PM.png]]
a) the null hypothesis is that $\mu\leq 2300$(when testing thinking about it as what if the hypothesis isn't true) and alt hypothesis is $\mu\geq 2300$. 

b) I think this is a t-test, so the t statistic is $\frac{\bar{X}-\mu}{s/\sqrt{n}}$, $s=\sqrt{400}$ because it is the square root of $6000$ divided by $15$. This gives us $t=\frac{2400-2300}{\sqrt{400}/\sqrt{16}}=20$ this seems really big 
(possibly try to make an argument with the gamma de f of t distribution for siz e)

c) The power function is based off the non-central t distribution where $\mu_1=\theta$ and $\mu_2=???$

![[Screenshot 2026-05-05 at 10.43.17 PM.png]]
a) I think that the null hypothesis is just that $\sigma_1^{2}=\sigma_2^2$ and the alternative is that  $\sigma_1^{2}\neq \sigma_2^2$

b) the right test statistic would be the F statistic, $f=\frac{90/9}{210/14}$ 

c) I have no clue, it seems like so because if its not from the normal distribution than our test statistic times the true variances isn't going to be $f$ because the top and bottom aren't gonna be chi squared $\frac{\sigma_1^2}{\sigma_2^2}V\sim F_{m-1,n-1}$ only because it causes the top and bottom to be chi squared

![[Screenshot 2026-05-05 at 11.54.45 PM.png]]
a) the null hypothesis is that high BP and exervcise frequency are independant 
b) the probability of being in yes assuming independant is $\frac{80}{200}$ and the probability of being in low is $70/200$ given independant so we expect there to be $\frac{80\cdot 70}{200^2}200$(this can't be correct)
c) 2 because the test statistic is the chi squared and there is $(3-1)(2-1)$ degrees of freedom



![[Screenshot 2026-05-06 at 12.03.02 AM.png]]
a)we can compute it using ![[Screenshot 2026-05-06 at 12.05.09 AM.png|200]] which gives us $\hat{\beta}_1=\frac{200}{80}$ and $12-\hat{\beta_1}5=\hat{\beta}_0$
b) I have no clue how to do this I am completely spacing
c) if we knew some pivotal varaible we could hypothesis test

![[Screenshot 2026-05-05 at 11.07.27 PM.png]]
a)
$Y$ is $n\times 1$, one output for each input. $X$ is $n\times p$ rows are observations and columns are values of the observation. $\beta = p\times 1$ one coefficent for each parameter, I think the error vector is $n\times 1$ 

b) 
Homoskadacity(no clue how to spell this) equal variance on any point in the line. Meaning that $\text{Var}(Y|X=x)=\text{Var}(Y|X=x_2)$ for all $x_1$ and $x_2$

normally residuals, the residuals are normally distributed

Data is known 

Linear relationship between the predictors and the thing we are trying to predict 

c)
$X=\begin{bmatrix}1,-1\\ 1,0\\1,1\end{bmatrix}$ and we calculate our $\beta$'s using $(X^{\prime}X)^{-1}X^{\prime} Y$. First we calculate $X^{\prime}X$ which is easy because the columns are orthogonal, meaning the off diagonals are zero giving us $\begin{bmatrix}3,0\\ 0,2\end{bmatrix}$ which is easy to invert giving us $\begin{bmatrix}1/3,0\\ 0,1/2\end{bmatrix}$. Then calculating $X^{\prime}Y=\begin{bmatrix}0\\ 1\end{bmatrix}$ thus we get $\beta = X^{\prime}Y=\begin{bmatrix}0\\ 1/2\end{bmatrix}$

![[Screenshot 2026-05-05 at 11.29.50 PM.png]]
a) we know because there are $29$ degrees of freedom that there are $30$ observations. We know the degrees of freedom between groups is the number of groups minus $1$, tnus there are three groups and $10$ observations in each group
b) The null hypothesis is that all the groups have the same mean and the alternative is that at least two differ
c) following the formula on the sheet $U^2=\frac{S^2_{bet}/(p-1)}{S^2_{res}/(n-p)}=\frac{180/(2)}{270/(27)}$