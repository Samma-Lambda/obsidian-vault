### 10.3.1
![[Screenshot 2026-04-08 at 7.39.22 PM.png|500]]
We calculate the test statistic $Q=\Sigma\Sigma \frac{(N_{ij}-\bar{E}_{ij})^2}{\bar{E}_{ij}}$. Assuming the variables are independent we compute the following table using the marginals 

|       | Good Grades  | Athletic Ability | Popularity   |     |
| ----- | ------------ | ---------------- | ------------ | --- |
| Boys  | (227/478)247 | (227/478)90      | (227/478)141 | 227 |
| Girls | (251/478)247 | (251/478)90      | (251/478)141 | 251 |
|       | 247          | 90               | 141          |     |
|       |              |                  |              |     |

Which we then do $1-(\chi^{2}_2)^{-1}(Q)$ to find the p-value of test which we get $Q=21.56$ and thus get a ridiculusly small $p$ value thus we reject the null hypothesis 

### 10.3.5
We are doing pretty much the exact same test as above except with more degrees of freedom. We get $Q=8.6$ which $1-(\chi^{2}_3)^{-1}(Q)=0.0351$ which means that we reject the null hypothesis 
![[Screenshot 2026-04-09 at 1.36.28 PM.png|300]]
### 10.4.1
Again we are just calculating $Q$ but instead this time it has degrees of freedom $4$. We calculate $Q=18.8$ which we then calculate $1-(\chi^{2}_4)^{-1}(Q)=0.0009$ so we reject the null hypothesis 
 ![[Screenshot 2026-04-09 at 1.48.04 PM.png|300]]



### 10.5.6
It was believed that a certain university was discriminating against women in its admissions policy because 30 percent of all the male applicants to the university were admitted, whereas only 20 percent of all the female applicants were admitted. In order to determine which of the five colleges in the university were most responsible for this discrimination, the admissions rates for each college were analyzed separately. Surprisingly, it was found that in each college the proportion of female applicants who were admitted to the college was actually larger than the proportion of male applicants who were admitted. Discuss and explain this result.

Me and Alex discussed and explained this result. This is exactly like the example you showed us in class. It was because the women are applying to the harder to get into school and thus there were more women being rejected. This is an example of simpsons paradox. 
Here is an example table that would show this 

| College | Men Admitted | Men Applied | Men Rate | Women Admitted | Women Applied | Women Rate |
| ------- | ------------ | ----------- | -------- | -------------- | ------------- | ---------- |
| Easy    | 80           | 100         | 80%      | 18             | 20            | 90%        |
| Hard    | 10           | 100         | 10%      | 36             | 180           | 20%        |
From this table we can see that men are admitted at a $45\%$ rate and women are admitted at a $25.2\%$ rate 

### 11.1.1
![[Screenshot 2026-04-09 at 1.57.55 PM.png]]
To start we write $\Sigma^{n}_{i=1}(c_1x_i+c_2)^2=c_1^2\Sigma x_i^2 +2c_1c_2n\bar{X}+nc_2^2=n(2c_1c_2\bar{X}+c_2^2)+c_1^2\Sigma x_i^2$ 
Note that $n(c_1\bar{X}+c_2)^2-nc_1^2\bar{X}^2=n(2c_1c_2\bar{X}+c_2^2)$
Thus we know that $n(2c_1c_2\bar{X}+c_2^2)+c_1^2\Sigma x_i^2=n(c_1\bar{X}+c_2)^2-nc_1^2\bar{X}^2+c_1^2\Sigma x_i^2$
Now all we need to do is show that $-nc_1^2\bar{X}^2+c_1^2\Sigma x_i^2=c_1^2\Sigma(X_i-\bar{X})^2$
Thus we have proven that $\Sigma^{n}_{i=1}(c_1x_i+c_2)^2=c_1^2\Sigma(X_i-\bar{X})^2+n(c_1\bar{X}+c_2)^2$
### 11.1.3
![[Screenshot 2026-04-09 at 2.08.20 PM.png]]
First we plug in $\hat{\beta_0}+\hat{\beta_1}\bar{X}$ we then use the definition of $\hat{\beta_0}=\bar{Y}-\hat{\beta_1}\bar{X}$ we get $\hat{\beta_0}+\hat{\beta_1}\bar{X}=\bar{Y}-\hat{\beta_1}\bar{X}+\hat{\beta_1}\bar{X}=\bar{Y}$ 

### 11.1.6
Suppose that both the least-squares line and the least- squares parabola were fitted to the same set of points. Explain why the sum of the squares of the deviations of the points from the parabola cannot be larger than the sum of the squares of the deviations of the points from the straight line.

A parabola has more flexibility than the line, if a line is optimal then the parabola can become a line by setting the $a$ in $ax^2+x+b$ to $0$ 

### 11.2.2
Show that $E[\hat{B}_1]=B_1$
Let $w=[\Sigma_{i=1}^{n}(X_i-\bar{X})^{2}]^{1/2}$. Note that $\hat{B}_1=\frac{\Sigma(x_i-\bar{X})Y_i}{w^2}$ so $E(\hat{B})=\frac{\Sigma(x_i-\bar{X})E(Y_i)}{w^2}=\frac{\Sigma(x_i-\bar{X})(B_0+B_1x_i)}{w^2}$ 
which we then distribute getting $\frac{B_0\Sigma(x_i-\bar{X})+B_1x_i\Sigma(x_i-\bar{X})}{w^2}$ which $B_0\Sigma(x_i-\bar{X})=0$ thus we get 
$\frac{B_1(\Sigma x_2-n\bar{X}^2)}{w^2}=\frac{B_1(\Sigma x_2-n\bar{X}^2)}{\Sigma_{i=1}^{n}(X_i-\bar{X})^{2}}=\frac{B_1(\frac{1}{n}\Sigma x_2-\bar{X}^2)}{\frac{1}{n}\Sigma_{i=1}^{n}(X_i-\bar{X})^{2}}=B_1$. Thus we have proven that $E[\hat{B}_1]=B_1$ 

### 11.2.3
Show that $E(\hat{β}_0 )=β_0$ 
$E(\hat{β}_0 )=E(\bar{Y}-\hat{\beta_1}\bar{x})=E(\bar{Y})-\hat{\beta_1}\bar{x}=\beta_0+\beta_1\bar{x}-\beta_1\bar{x}=\beta_0$


### 11.2.12
Here is the table 
![[Screenshot 2026-04-09 at 2.15.21 PM.png|300]]
We compute $\hat{\beta}_0=\bar{Y}-\hat{\beta_1}\bar{x}$ and compute $\hat{\beta}_1=\frac{\Sigma_{i=1}^n(Y_i-\bar{Y})(X_i-\bar{X})}{\Sigma_{i=1}^{n}(x_i-\bar{X})^2}$. We compute $\hat{\sigma}^2=\frac{1}{n}\Sigma_{i=1}^{n}(y_i)-\hat{\beta_0}-\hat{\beta_1}x_i)^2$ and $\text{Var}(\hat{\beta_0})=\hat{\sigma}^2(\frac{1}{n}+\frac{\bar{x}^2}{w^2})$ and $\text{Var}(\hat{\beta_1})=\frac{\hat{\sigma}^2}{w^2}$  
We then compute this getting $\hat{\beta_1} =0.55$, $\hat{\beta}_0=40.89$, $\hat{\sigma}^2=0.96577$, $\text{Var}(\hat{\beta_0})=0.586$ and $\text{Var}(\hat{\beta_1})=0.091$ 