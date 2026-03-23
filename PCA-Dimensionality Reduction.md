---
tags:
  - "#Applied"
---
The core idea behind PCA for dimensionality reduction it to find a subspace to project all the vectors onto that preserves the most variance of the points. This allows this lower dimensional embedding to accurately reconstruct the higher dimensional space when you project it back up. It is a lossy compression algorithm.

This can be useful for visualizing high dimensional spaces and simplifying data for machine learning. An intuitive way of thinking of PCA of dimensionality reduction is taking an image and capturing the most of the scene from that one dimension. 


If we start with a matrix representing our observations where each row is an observation and each column is a dimension of our observations, we first normalize our data by computing the mean of each column and then subtracting that from the column. This normalizes our data, meaning it have a centroid at $(0,0)$ 

We then take this normalized matrix $X$ and compute its covariance matrix which is $C =\frac{1}{n-1}X^T X$. This matrix the value $C_{ij}$ is the sample covariance between the dimensions $i$ and the dimension $j$ 

We then find the eigenvalues and eigenvectors of $C$ and find that the biggest eigenvectors are the best vectors to preserve variance. So we then project our data onto the subspace spanned by the $m$ top eigenvectors.

Beneath is an image of the MNIST dataset being reduced down from $28\times 28$ dimensions to just two dimensions. Notice how they nicely cluster 
![[MNIST PCA IMAGE.png|600]] 