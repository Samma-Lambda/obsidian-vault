---
tags:
  - Pure
---
# What is a knot? 
A knot is the image of an embedding $f:S^1\rightarrow \mathbb{R}^3$ two knots are equivalent if there exists some ambient isotopy between two knots. This definition prevents bad knots from being formed with a few examples below![[Screenshot 2026-07-02 at 4.28.51 PM.png|427]]

## Representations of knots 
Due to the difficulty working with $3$ dimensional representations of knots we have developed other representations  
### Knot Diagram 
Knot diagrams work in a way similar to the graphic below
![[Screenshot 2026-07-02 at 11.12.18 AM.png|412]]
This works by projecting the knot down down into $2$ dimensions, in a way that is injective expect a finite number of double points(these are the knot intersections). At each of these double points we denote one going under vs over to be able to recover the knot. 
Additionally we assume that these double points are transverse meaning the way that they cross is linearly independent. 
#### Reidemeister Moves
Reidemeister moves are moves that you can do on a knot diagram that leave the knot diagram equivalent. Here are the three moves 
![[Screenshot 2026-07-02 at 11.33.26 AM.png]]
When defining invariants on knots, you need the invariant to not change under reidemeister moves. Thus the invariant doesn't change under representations   

## Prime Knots and the Connect Sum
An orientation of a knot is direction that you travel along a knot. If we take two knots with an orientation, we can connect them using an arc like the diagram below. 
![[Screenshot 2026-07-02 at 11.39.10 AM.png|445]]
A knot is composite if it can't be represented as the connect sum of two knots. Otherwise it is a prime not 

# Useful Types of Functions
## Embedding
Let $X\subset \mathbb{R}^n$ and let $f:X\rightarrow \mathbb{R}^m$ be a diffeomorphism. Then the induced map $f:X\rightarrow f(X)$ is an embedding 
## Homomorphism
This is a continuous bijective function with a continuous inverse 
## Diffeomorphism
This is a homeomorphism which both $f$ and $f^{-1}$ are smooth
## Smooth
A function $f:U\rightarrow \mathbb{R}^n$ is considered smooth if it at every point $p\in U$ if all the partial derivatives exist for all orders. Additionally $U$ must be an open subset of $\mathbb{R}^n$ \
## Ambient Isotopy 
This is very similar to a homotopy if is a function 


