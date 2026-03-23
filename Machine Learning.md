---
tags:
  - Computer
---
Machine learning is the process of training an algorithm to classify training data based off specific traits and then applying that to real world data in order to predict things about the data. An example could be a blood cancer detector taking in your bio-information and then predicting wether you have blood cancer or not 

# Supervised vs Unsupervised 
One of the biggest distinction between machine learning algorithms is wether they are supervised or unsupervised. The main distinction is that supervised models required labelled data usually labeled by people, and unsupervised machine learning does not.
An example of supervised classification would be the blood cancer detection above. The example of unsupervised classification would be clustering customers for types of advertising.  


# Classification vs Regression
Other than supervised vs unsupervised the next biggest distinction is classification vs regression. Classification is trying to place the data observations in bins(for multi-class classification its still single class but more complicated, IE a class is $[0,0,1]$ or $[1,1,1]$ with each bit being a "class"), where regression is trying to find a continuous value based off the data(like a cholesterol level for someones bio-data)


# Supervised Classification Architectures
These are the Supervised Architectures that are used to classification 
## Support Vector Machines
Support vector machines work by by creating an affine decision boundary(a subspace with a support vector to make it off center). You might think that a simple linear boundary might not be able to divide a space, but by mapping a space to a higher dimension we are able to create a more effective boundary.
![[Pasted image 20251218205330.png|650]]


## Decision Tree
This is another architecture that use a series of "questions" to classify it. It works by "splitting" the into two child nodes. The goal of the splitting is to minimize some function on each level(either entropy or a more complicated function) until we each a node where we are almost certain that it is a specific classification(if the entropy at the node is zero then we do know its that class)
![[Pasted image 20251218213732.png|600]]



# Regression Architectures 
The cored idea of regression is to output some value $Y$ based some input $X$ where $X$ is a vector of observations from a random variable. 
## Linear Regression 
Linear regression creates a **Linear** model which fits data points by creating a line and then minimizing the squared error.  It also has a noise parameter $\epsilon$ which once you have the line you can calculate. This is calculated by taking the sum of squared residuals and then dividing by the degrees of freedom. This results in a function which looks like 
$$ Y=\beta_0+\beta_1 X_1+...+\beta_nX_n+\epsilon$$
with $\epsilon \sim N(0,\sigma^2)$ 

## GAM 



## Regression Trees




# Performance Metrics 
## Confusion Matrix 
This is a metric on how a classification model works. It communicates what type of mistakes the model is making. 
![[Pasted image 20260205153211.png|300]]

## AUC/ROC Curve 
This is a metric which tells you how well a binary classification model preforms. While a confusion matrix tells you how a classification model does for a specific classification threshold this curve tells you across multiple thresholds how the model will preform 
![[Pasted image 20260205154248.png|650]]










There is a more specialized field for specifically classifying images known as computer vision 
[[Computer Vision]]