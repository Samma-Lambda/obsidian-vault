---
tags:
  - Pure
---
This fields studies finding zeros to more complicated polynomials like $x^2+y^2-1$ or even more complicated ones. The study of linear algebra can be thought of as studying a subfield of algebraic geometry 

### Monomial
A monomial is the product of the form $x_1^{\alpha_1}x_2^{\alpha_2}...x_n^{\alpha_n}$ which can be a pain to write. So often we write it as $x^{\alpha}=x_1^{\alpha_1}x_2^{\alpha_2}...x_n^{\alpha_n}$ where $\alpha=(\alpha_1,\alpha_2,...,\alpha_n)$. The degree of a monomial is $\Sigma \alpha_n$

### Polynomial 
A polynomial is formally defined as a linear combination of monomials. For example you could denote this as $\mathbb{R}[x_1,x_2,x_n]$. 
- The number of unique monomials in the polynomial is the number of **Terms** 
- The total degree of a polynomial is highest sum of the monomials exponents 
- We can say that a polynomial divides another by the normal definition $f|h\rightarrow f=gh$
Polynomials satisfy all the axioms of a field expect multiplicative inverses so it is called a commutative ring 

### Affine Space 
An affine space for some field $k$ is a collection of points defined as $k^n=\{(a_1,a_2,...,a_n)|a_i\in k\}$. Note that polynomials act a functions from $k^n \rightarrow k$ 
Its important to note that just because $f \in \mathbb{F}[x_1,x_2,..,x_n]$ is the zero function, does not mean that it is the $f=0$. A specific example of this would be $x^2-x\in \mathbb{F}_2[x]$ because $x^2-x=x(x-1)$. But if the field is infinite then this is not the case. 


### Affine Variety 
This is a generalization of the null space, an algebraic variety is defined as $V(f_1,..., f_s) = \{(a_1,..., a_n) \in k_n : f_i(a_1,..., a_n) = 0 \forall ,1 \leq i \leq s\}$. This can be more intuitively thought of as the set of all points which satisfy all the polynomials in the set. You can combine varieties by $V\cap W =V(f_1,..., f_s,g_1,...,g_t)$ and $V\cup W=V(f_i g_j : 1≤i≤s,1≤j≤t)$

### Ideal 
$I\subset k[x_1,...,x_n]$ is a ideal iff 
- $0\in I$
- $f,g\in I$ implies that $f+g\in I$
- $f \in I$ and $a \in k[x_1,...,x_n]$ implies that $af\in I$
if $f_1,...,f_n \in k[x_1,...,x_n]$ then the set $\langle f_1,...,f_n \rangle$ is an ideal. Additionally if $\langle f_1,...,f_n \rangle$ and $\langle g_1,...,g_n \rangle$ generate the same ideal that $V(f_1,...,f_n)=V(g_1,...,g_n)$.


### Relationship between ideal and variety
If you have two different bases of ideals $\langle f_1,...,f_n \rangle=\langle g_1,...,g_n \rangle$ then their varieties are the same. 
Beyond that for any variety we can create an ideal from it $I(V)={f ∈k[x_1,...,x_n]: f(a_1,...,a_n)=0\, \forall(a_1,...,a_n)\in V}$
Finally if $V,W$ are affine varieties and $V\subset W$ then $I(V)\subset I(W)$