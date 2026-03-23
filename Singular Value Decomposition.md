---
tags:
  - Applied
---
Singular Value Decomposition(SVD) is a process where you take a matrix $A$ that is a $n\times m$ matrix and decomposes it into $A=U\Sigma V^T$ where $U$ is a $n\times n$ orthogonal matrix, $\Sigma$ is $n \times m$ diagonal matrix, and $V^T$ is a $m\times m$ orthogonal matrix. 

We calculate this by finding the eigenvectors of $A^TA$ which are the columns of $V$ and $AA^T$ which are the columns of $U$. Then the square roots of the eigenvalues of both of these become the diagonal entries $\Sigma$. Geometrically this can be interpreted as the matrix being composed of a rotation, stretching or shrinking each dimension and then another rotation. 

This works because the first $V^T$ aligns the right singular vectors of $A$(vectors such that $Av_i=\sigma_i v_i$) with the standard basis. Then the matrix $\Sigma$ scales those vectors by $\sigma_i$ along dimension $i$, then finally $U$ rotates the matrix so that the basis is normal again.
Basically it is rotate it so that the "eigenvectors" align with the standard basis, stretch/shrink/erase the dimensions and then rotate back.


# Compression
If we rank the singular values from greatest to least, the greatest value represents the most important feature in the transformation. By considering on the first $i$ columns of $U$ the first $i$ singular values of $\Sigma$ and the first $i$ columns of $V$ we can get a compressed version of $A$.
This can take the matrix $A$ which can be represented using $n\cdot m$ values and then represent it using $i\cdot n + i + i\cdot m=i(n+m+1)$ which can be more efficient.  