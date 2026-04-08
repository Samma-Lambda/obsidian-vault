Using definition of TV 
We know that $||X^{(t)}_{x_0=i}-\pi||_{tv}$ is $\text{Max}_{A\in S}|X^{(t)}_{x_0=i}(A)-\pi(A)|$ 

Rewriting $\pi(A)$ 
we can rewrite $\pi(A)$ as $\Sigma_{i=0}^n P(X_t\in A|X_0=i)P(X_0=i)$ because it won't change with the steps. We know that $P(X_t\in A|X_0=i)=X^{(t)}_{X_0=i}(A)$ by definition, and that $P(X_0=i)=\pi_i$
Thus $\pi(A)=\Sigma_{i=0}^{n} X^{(t)}_{x_0=i}(A)\pi_i$ 
USE MATRIX MULTIPLICATION $\pi_i=\Sigma \pi_j P_{ji}$

We can rewrite $\text{Max}_{A\in S}|X^{(t)}_{x_0=i}(A)-\pi(A)|$ as $\text{Max}_{A\in S}|X^{(t)}_{x_0=i}(A)-\Sigma_{j=0}^n X^{(t)}_{X_0=j}(A)\pi_j|$ which since $\Sigma_{j=0}^n \pi_j=1$ we can rewrite again as $\text{Max}_{A\in S}|\Sigma_{j=0}^{n}\pi_i(X^{t}_{x_0=i}(A))-X^{t}_{x_0=j}(A))|$. 

$\text{Max}_{A\in S}|\Sigma_{j=1}^n\pi_i(X^{t}_{x_0=i}(A))-X^{t}_{x_0=j}(A))|$ is less than $\text{Max}_{i,j\in S}(\text{Max}_{A\in S}|X^{t}_{x_0=i}(A)-X^{t}_{x_0=j}(A))|)$. This is because 