# Specific Topics
Specific Topics
• Statistics and Parameters
Parameters are a characteristic of the population, this might be the true mean and deviation for a specific population. 
Statistics are a characteristic of a sample, for example sample mean or sample variance. Often we are trying to find the parameters using statistics in statistics. 

• Supervised vs Unsupervised
Supervised learning is based on a known characteristic you are trying to predict(an example might be cancer vs non-cancer), while unsupervised machine learning involves identifying patterns in the data without knowing about the patterns ahead of time(clustering customers to find specific groups to target) 

• Regression vs Classification
Regression is the process of trying to predict a numeric variable based off some data, while classification is for a categorical variable 

• Prediction vs Inference
Inference is the study of how $Y$ changes as a function of $X$, basically rather than predicting the value its stating how they are related. Prediction is studying how knowing one might let you predict the other. 

• Testing vs Training and cross validation for model selection
You want to be able to understand how the model will work on unseen data, so you typically will break the data up $80-20$ and train the model on $80$ of the data and then test it on $20$ of the data. 
With less training data you will have a higher variance of parameter estimates, where less testing data results in higher variance in assessment 


• Bias vs Variance (overfitting means wiggly, high variance due to fitting “noise”)
For parameters the definition of variance is $E[(\hat{\theta}-\theta)^2]$ so this is the expected squared distance away from the true parameter 
where as the definition of bias is $E(\hat{\theta})-\theta$. This is the expected distance from the true parameter. If the difference is zero then we consider that estimator unbiased
The bias variance tradeoff says that simpler models will have high bias but low variance, but more complicated models will have low bias but high variance 



# Concepts
## Linear Regression 
This models an output variable $Y$ as 
$Y=\beta_0+\beta_1 X_1 +...+\beta_n X_n$ 
in a way that minimizes the squared error. There are the following assumptions to be checked 
Make with interaction with * vs without interaction is +
``` R
model <- lm(observatory_variable~explanatory_1+explantory_2+...+explantory_n, data = dataframe)
```
or for just a visualization 
``` R
ggplot(data = newCaseDate, aes(x=Days, y=Daily_Cases))+
  geom_point(alpha = 0.5)+
  geom_smooth(method = "lm", se = FALSE, color = "red")

```

To analyze said model 
``` R
summary(model)
```
This will output an intercept(The base value when all the numerics are set to zero and the categorical variables are at a baseline)
Either the slope for each numeric variable or how much each categorical variable alters the baseline value. 
And the column that says $Pr(>|t|)$ which is the probability that given that the coefficient is zero seeing the data that we observed 

There are the following assumptions to be checked 
1. Linear relationship: There is a linear relationship between $X_i$ and $Y$ 
2. Independence of residuals: there is no correlation between consecutive residuals 
3. Homoscedasticity: The residuals have constant variance at every level of x.
4. Normality: The residuals are normally distributed
To check these use the following code 
``` R
model <- lm(observatory_variable~explanatory_1+explantory_2+...+explantory_n, data = dataframe)

plot(model)
```
1. Residuals vs Fitted if the red line deviates away from the dashed line it is non-linear. Just think about the fact it is plotting the residuals. This checks the normality of the residuals 
2. Q-Q is plotting the quantiles of each variable against each other. This means if they they are from the same distribution it will show up as linear relation. This checks the linearity 
3. Scale Location shows you homoscedasticity, you want the redline to be horizontal 
4. Residuals vs Leverage look for values in the upper right corner or the lower right corner 

### Specific Types of Linear Regression 
1. Parallel line linear regression:
This is where you split it based off a categorical it results in parallel lines 
``` R
mod2 <- lm(vote_percent ~ edu_percent + region, data = Election, na.action = na.exclude)
ins_aug <- broom::augment(mod2, newdata = Election)
ggplot(data=ins_aug, aes(x=edu_percent, y=vote_percent, color=region))+
  geom_point(alpha = 0.5)+
  geom_line(aes(y=.fitted)) 
summary(mod2)
```
2. Multiple Linear Regression:
This is just with more variables technically above is multiple regression  
## Polynomial Regression 
This models an output variable $Y$ as 
$Y=\beta_0+\beta_1 X +...+\beta_n X^n$ to make one use the following code 
``` R
model2 <- lm(data = newCaseDate, formula = observatory_variable ~ poly(explanatory_variable,2))
```


## GAM(General Additive Model)
This is a model predicts $Y$ using a formula 
$Y= \beta_0 + f_1(x_1)+..._+f_m(x_m)$ and the code to make a GAM is ???



## Cross Validation 
This is used to see if you model generalizes well. For example if you add a term to a polynomial regression it will always fit the data better, but it might not apply to the real world better. Thus you use cross validation 
``` R
#this is for train test split 
library(rsample)
split_1  <- initial_split(nsw, prop = 0.8)
train  <- training(split_1)
test   <- testing(split_1)
model<-lm(re78~education + married, data = train)

RMSE <- sqrt(sum((test$output -predict(model,test$input))^2)/(length(test$input))

#this is for the k fold cross validation 
set.seed(125)
library(caret)
train_control <- trainControl(method = "cv", number = 5)
model1 <- train(vote_percent~edu_percent, data = Election,
               method = "lm",
               trControl = train_control,
               na.action = na.omit)
print(model1)
```
The formula for RMSE 
$$ 
Y= \sqrt{\frac{\Sigma^{N}_{i=1}(x_i-\hat{x_i})^2}{N}}
$$
Also if you need the residual standard deviation you can call
```R
poly_model<-lm(re78~ poly(education, 3), nsw)
sigma(poly_model)
```