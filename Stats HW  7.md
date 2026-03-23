## 9.6.1
In Example 9.6.3, we discussed Roman pottery found at two different locations in Great Britain. There were samples found at other locations as well. One other location, Island Thorns, had five samples $X_1, . . . , X_n$ with an average aluminum oxide percentage of $\bar{X} = 18.18$ with $\Sigma^5_{i=1}(X_i −\bar{X})^2 =12.61$. Let $Y_1,...,Y_5$ be the five sample measurements from Ashley Rails in Example 9.6.3. Test the null hypothesis that the mean aluminum oxide percentages at Ashely Rails and Island Thorns are the same versus the alternative that they are different at level $α_0 = 0.05$

The Ashley rails site has $\bar{Y}=17.32$ and $S^2_y=11.01$ with $n=5$, the island thorns has $\bar{X}=18.18$ and $S^2_x = 3.125$ with $m=5$. We can calculate the test statistic $\frac{(5+5-2)^{1/2}(18.18-17.3)}{(\frac{1}{5}+\frac{1}{5})^{1/2}(3.125+11.01)^{1/2}}=1.0764$
Finding $T^{-1}_{8}(1-\alpha_0/2)=2.306$ since the absolute value of the test statistic is less than that we fail to reject the null.

## 9.6.8
In Example 9.6.5, determine the power of a level $0.01$ testify $|μ_1−μ_2|=σ$.

The non-centrality parameter of a $t$ distribution is $\frac{\mu_1-\mu_2}{\sigma(\frac{1}{m}+\frac{1}{n})^{1/2}}$. Since $\mu_1-\mu_2=\sigma$ the parameter is $\frac{1}{(\frac{1}{m}+\frac{1}{n})^{1/2}}=\frac{1}{(\frac{1}{8}+\frac{1}{10})^{1/2}}=2.108$. We calculate $T_{16}^{-1}(0.995)=2.921$ so we reject if our test statistic is $|t|>2.921$. We then calculate $1-T_{16}(2.921-2.108)$ for the shifting one being more than this point and $T_{16}(-2.921-2.108)$. Thus the power is $(1-T_{16}(2.921-2.108))+T_{16}(-2.921-2.108)$ 



## 9.7.7
Consider two different normal distributions for which both the means $μ_1$ and $μ_2$ and the variances $σ_1^2$ and $σ_2^2$ are unknown, and suppose that it is desired to test the following hypotheses: $H_0: σ_1^2≤σ_2^2, H_1: σ_1^2>σ_2^2$. Suppose further that a random sample consisting of 16 observations for the first normal distribution yields the values $\Sigma_{i=1}^{16}X_i=84$ and $\Sigma_{i=1}^{16}X_i^2=563$ 
, and an independent random sample consisting of 10 observations from the second normal distribution yields the values $\Sigma^{10}_{i=1}Y_i=18$ and $\Sigma^{10}_{i=1}Y_i^2=72$
a. What are the M.L.E.’s of $σ_1^2$ and $σ_2^2$?
the MLE of variance with unknown mean and unknown variance is $\frac{1}{n}\Sigma X_i^2-\bar{X}^2$(I looked this up)
first we calculate $\bar{X}=5.25$ and $\bar{Y}=1.8$ and we calculate $\hat{\sigma}_x = 563/16-(5.25)^2$ and $\hat{\sigma_y}=72/10-(1.8)^2$ as our MLE estimates


b. If an F test is carried out at the level of significance $0.05$, is the hypothesis $H_0$ rejected or not?
Note that $S^2_{x}=\Sigma(X_i-\bar{X})^2=\Sigma X_i^2- \Sigma 2X_i\bar{X}+\Sigma \bar{X}^2=\Sigma X_i^2 - n \bar{X}$ which see can find 
Thus $S^2_{x}=563-(5.25)(16)=479$ and $S^2_{y}=72-1.8(10)=54$ we get an F statistic of $\frac{479/16}{54/10}$  
which using the inverse cdf of F gives 0.006773308. Thus we reject the null

## 9.7.9
Consider again the conditions of Exercise 7, but suppose now that it is desired to test the following hypotheses:
$H_0: σ_1^2=σ_2^2$ 
$H_1: σ_1^2 \neq σ_2^2$
Suppose also that the statistic V is defined by Eq. (9.7.4), and it is desired to reject $H_0$ if either $V ≤ c_1$ or $V ≥ c_2$, where the constants $c_1$ and $c_2$ are chosen so that when $H_0$ is true, $P(V ≤ c_1) = P(V ≥ c_2) = 0.025$. Determine the values of $c_1$ and $c_2$ when $m=16$ and $n=10$, as in Exercise 7.
Under the null hypothesis $\frac{S^2_{x}}{S^2_{y}}\sim F_{15,9}$ so we can just use the quantiles to find the constants $c_1=0.3202345$  and $c_2=3.7$



## 10.1.2
show that if $p^0_i=1/k$ for $i=1,...,k$ then the statistic $Q$ defined by Eq. (10.1.2) can be written in the form $Q = (\frac{k}{n}\Sigma_{i=1}^k N_i^2)-n$

see that $\Sigma \frac{(N_i-n p_i^{0})^2}{np_i^0}=\Sigma \frac{(N_i-n/k)^2}{n/k}=\frac{k}{n}\Sigma(N_i-n/k)^2=\frac{k}{n}\Sigma( N_i^2-2N_i\frac{n}{k}+\frac{n^2}{k^2})=\frac{k}{n}(\Sigma N_i^2-\frac{2n^2}{k}+\frac{n^2}{k})$$=\frac{k}{n}(\Sigma N_i^2-\frac{n^2}{k})=(\frac{k}{n}\Sigma_{i=1}^k N_i^2)-n$

## 10.1.4
According to a simple genetic principle, if both the mother and the father of a child have genotype Aa, then there is probability $1/4$ that the child will have genotype AA, probability $1/2$ that she will have genotype Aa, and probability $1/4$ that she will have genotype aa. In a random sample of $24$ children having both parents with genotype Aa, it is found that $10$ have genotype AA, 10 have genotype Aa, and four have genotype aa. Investigate whether the simple genetic principle is correct by carrying out a $\chi^2$ test of goodness-of-fit.

We calculate the statistic as $Q = \frac{(10-24(1/4))^2}{24(1/4)}+\frac{(10-24(1/2))^2}{24(1/2)}+\frac{(4-24(1/4))^2}{24(1/4)}=3.66$ then you plug this into $1-(\chi^2_{3})^{-1}(3.66)=0.3$ 


## 10.1.8
Suppose that the distribution of the heights of men who reside in a certain large city is the normal distribution for which the mean is 68 inches and the standard deviation is 1 inch. Suppose also that when the heights of 500 men who reside in a certain neighborhood of the city were measured, the distribution in Table 10.4 was obtained. Test the hypothesis that, with regard to height, these 500 men form a random sample from all the men who reside in the city.
Table 10.4 Data for Exercise 8 Height
![[Screenshot 2026-03-19 at 4.06.43 PM.png|300]]
We take the continuous data and bin it by using the cdf giving us the following probabilities 
$p_0 = \Phi^{-1}(-2)$
$p_1 =\Phi^{-1}(-0.5) -\Phi^{-1}(-2)$
$p_2 =\Phi^{-1}(0.5) -\Phi^{-1}(-0.5)$
$p_3 =\Phi^{-1}(2) -\Phi^{-1}(0.5)$
$p_4 =\Phi^{-1}(2)$

Then we do the chi squared test like before but using these probability getting a test statistic of $Q=27.50$ 
Then we plug it into $(\chi^2_{4})^{-1}(27.50)$  and get a $p$ value of almost $0$ 



## 10.2.2
At the fifth hockey game of the season at a certain arena, 200 people were selected at random and asked how many of the previous four games they had attended. The results are given in Table 10.7. Test the hypothesis that these 200 observed values can be regarded as a random sample from a binomial distribution; that is, there exists a number $θ$ $(0 < θ < 1)$ such that the probabilities are as follows:
$p_0=(1−θ)^4, p_1=4θ(1−θ)^3, p_2=6θ^2(1−θ)^2, p_3=4θ^3(1−θ), p_4=θ^4$
![[Screenshot 2026-03-19 at 4.48.52 PM.png|300]] 
The likelihood is $L(\theta)=\binom{N}{N_1,...,N_k}\Pi p_i^{N_i}$. Which to optimize we can drop the constant and log it giving us the equation $N_0\text{log}(p_0)+...N_4\text{log}(p_4)$ which we then solve for the MLE and get $\theta=\frac{2}{5}$. I DO NOT WANT TO TYPE ALL OF IT OUT

Then using this MLE we can calculate out the test statistic $Q=47$ which we then place in $(\chi^2_{4})^{-1}(47)$ which gives us a $p$ value that is almost zero  

## 10.2.4
Consider again the sample consisting of the heights of 500 men given in Exercise 8 of Sec. 10.1. Suppose that before these heights were grouped into the intervals given in that exercise, it was found that for the $500$ observed heights in the original sample, the sample mean was $\bar{X}_n = 67.6$ and the sample variance was $S_n^2/n = 1.00$. Test the hypothesis that these observed heights form a random sample from a normal distribution.

To do this we have to get the expected values of under the null hypothesis of each category which is $27,202,177.9,88,4$ which we then find the test statistic of $11.19$ the degrees of freedom are $2$ and we calculate $(\chi^2_{2})^{-1}(0.05)=5.99$. thus we reject the null hypothesis