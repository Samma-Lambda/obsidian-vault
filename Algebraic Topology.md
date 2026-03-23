---
tags:
  - Pure
---
The goal of algebraic topology is to better understand topological spaces using skills from abstract algebra

# Manifold 
Manifold is a word that I feel likes gets thrown around a lot in math but never really gets specified what it is. A manifold is a 


# Homotopy
Two functions $f:X\rightarrow Y$ and $g: X\rightarrow Y$ are considered homotopic if there exists some continuous map $H:X\times[0,1]\rightarrow Y$ such that $H(X,0)=f$ and $H(X,1)=g$. This basically is a movie from one function to another, which we will later use to define equivalence relation on loops 

# Fundamental Group
A loop is defined as a path(paths are just functions $f:[0,1]\rightarrow X$) such that $f(0)=f(1)$. The fundamental group of a space $X$ and a base point $x_0$ is defined and the loops starting and ending at $x_0$ up to homotopy. This creates a set of equivalence classes, that have the binary operation of concatenation 
$$
(f \cdot g)(s)= 
\begin{cases} 
      f(2s) & 0 \leq s\leq \frac{1}{2}\\
      g(2s) & \frac{1}{2}\leq s\leq 1 \\
\end{cases}
$$
As expected this creates an actual group denoted $\pi_{1}(X,x_0)$  


[[Topological Data Analysis]]