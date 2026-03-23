---
tags:
  - Pure
---
Low key I don't know what a tensor is right now 


# Dual Vector Spaces
For a given $F$-vector space $V$ we can define another vector space $V^{*}$ that is $\{\phi:V\rightarrow F| \phi \text{ is linear}\}$. We know that this is $F$-vector space because if you scale it by something from $F$ it will still be a linear function, adding functions together results in a linear function, we call this vector space the dual and call the vectors from this space co-vectors
## Basis of a Dual Vector Space
Considering that $\phi: V \rightarrow F$ is linear we only really need to know what happens to the basis vectors of $V$ to be able to define the basis of the whole space. Because of this we can define a basis of the dual space as $\delta_{i}$ where $\delta_{i}(v_i)=1,\delta_{i}(v_{j\neq i})=0$ 


# Tensor Product 
The tensor product is a way of combining vectors spaces this is used for things like encoding the state of two qubits. 
We construct the tensor product by starting with $V\times W$ where $V$ and $W$ are both $F$ vector spaces. We want to enforce some useful rules 
1. $a\otimes (b+c)-(a+b)\otimes (a+c)$ 
2. $(a+b)\otimes c-(a+b)\otimes (a+c)$ 
3. $\lambda (a \otimes b)-\lambda a \otimes b$
4. $\lambda (a \otimes b)-a\otimes(\lambda b)$
From this we can pull across scalars
## Basis of Tensor Product 
If $V$ has a basis of $\{e_1,e_2,...e_n\}$ and $W$ has a basis of $\{j_1,j_2,...,j_m\}$ then then the tensor product has a basis of $\{e_1\otimes j_1, e_2\otimes j_1, ... ,e_n\otimes j_1,e_1\otimes j_2,...,e_n,\otimes j_2,...,e_n\otimes j_n\}$  

## Universal Property of Tensor Products
