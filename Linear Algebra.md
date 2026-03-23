---
tags:
  - Pure
---

## Vector Space
A vector space is a additive abelian group with a group action on it from a field. This colloquially is described as things that can be added and multiplied. It follows the following axioms where $V$ is a $F-\text{Vector Space}$ 
1. $u+v=v+u$
2. $(u+v)+w=u+(v+w)$
3. $\exists 0 \in V \text{ such that } v+0=v$
4. $(-x)+x=x+(-x)=0$
5. $0x=0$
6. $1x=x$
7. $c(x+y)=cx+cy$
8. $(c+d)x=cx+dx$
Vector spaces are always equipped with the following 
- **Basis:** A minimal set of linearly independent vectors that every vector can be defined as a unique linear combination of. You can change basis using linear maps which can do useful things like convert from one coordinate system to another, or write a function as the product of sine waves using a Fourier transform 
- **Coordinate Mapping:** From the basis we can take whatever weird vector space we are working in an instead work in $F^n$ or $F^{\infty}$. This is where the "Traditional" linear algebra happens as the vectors look like $\mathbf{v} =\begin{bmatrix} v_1 \\v_2 \\\vdots \\v_n\end{bmatrix}$ 
- **Subspace:** A subspace is a vector space which is entirely contained within another vector space. Notable subspaces are the Null-space, Image-space, Trivial Subspace, and restricting a basis to a subset of the basis vectors. Additionally every subspace has another subspace connected to it called the orthogonal complement denoted by $W^{\perp}$ which is every vector orthogonal to every vector in $W$
- **Dimension:** The dimension of a vector space is the number of vectors in a basis



# Matrices/Linear Maps
While vector spaces are interesting on their own, often we want to study the functions between vector spaces either from one to another or one to itself. Since linear maps often preserve essential properties we often study those.
In finite dimensional spaces(or approximations of infinite dimensional spaces) we often encode these linear maps into a matrix. Matrices/Linear Maps might encode the transition from time $t$ to time $t+1$ in a Markov Chain or represent the way pixels will change when you zoom in on an image. Sometimes to encode a linear transformation you need to do the coordinate mapping first 
- **Determinants:** When a linear map is encoded as a matrix, we can calculate the determinate using a variety of techniques but the most common is probably cofactor expansion.  The determinate takes a linear transformation and then maps them into the field $F$. Geometrically the determine represents the amount the volume of a given space gets scaled. Additionally the composition of linear transformations has the nice property that for two matrices $A$ and $B$, $\text{Det}(A)\text{Det}(B)=\text{Det}(AB)$. This is incredibly useful in proofs. 
- **Eigenvalues/Eigenvectors:** When studying a linear map, sometimes you will find vectors that remain on their own span but get scaled by some value. These vectors are known as eigenvectors and are incredibly useful. Often if you are going to apply the same linear transformation over and over it is useful to change basis onto the eigenvectors. 
- **Null Space/Image Space:** When you have a linear transformation there will be some vectors that get mapped to the zero vector. These vectors form a subspace, the orthogonal complement is the space of all vectors that don't get mapped to the zero vector. 
- **Rank Nullity Theorem:** For a given linear transformation we have the property that the dimension of the image space plus the dimension of the null space
# Inner Product Space 
An inner product space if a vector space with additional properties. Specifically it is equipped with a function $\langle\cdot,\cdot \rangle :V\times V \rightarrow F$ that satisfies the following properties for $x,y,z \in V$ and $a,b \in F$.
1. $\langle x,y \rangle = \overline{\langle y,x \rangle}$ 
2. $\langle ax+by,z \rangle =a \langle x,z \rangle + b\langle y,z \rangle$  
3. $\langle x,x \rangle >0$ 
By having that simple function it gives us a notion of the following 
- **Length:** We have the canonical norm which is defined as $\sqrt{\langle x,x \rangle }$  which gives us a notion of how long a vector is
- **Cosine Similarity:** By using $\text{cos}(\theta) = \frac{\langle u,v \rangle}{||u||\, ||v||}$ when $\theta$ is $1$ that means that the the vectors lie on each others span and when $\theta$ is $0$ that means that the vectors are orthogonal
- **Projection:** From Cosine Similarity we can start to project vectors onto the span of another vector using the formula $\text{proj}_{u}(v)=\frac{\langle u,v \rangle}{\langle u,u \rangle }u$ 

# Hilbert Space 
If a inner product space is complete(meaning every sequence converges to something within the space) is considered a Hilbert space. 
The intuition behind this is that you might have the infinite dimensional vector space of all polynomials with the orthonormal basis of $\{x^0,x^1,x^2...,x^\infty\}$ and then project the function $\text{sin}(x)$ onto this space. You will be given a linear combination of these polynomials that represents $\text{sin}(x)$, but $\text{sin}(x)$ is not a polynomial. 


# Applications
[[PCA-Dimensionality Reduction]]
[[Fourier Transformation]]
[[Singular Value Decomposition]] 

# Further Applications
[[Tensors]]