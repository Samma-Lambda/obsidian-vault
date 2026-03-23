---
tags:
  - Applied
---
Topological Data Analysis(TDA) is a way if analyzing data using the skills from topology. One of the most essential theorems within TDA is the nerve theorem 

# Simplexes 
A simplex is a generalization of points, lines, and tetrahedra in higher dimensions. More specifically a $k$-simplex is a convex hull(a set of points where every convex combination is an element of it) of $k+1$ vertices points
![[Pasted image 20251227004610.png|300]]


# Nerve Theorem
The nerve theorem states that given a good cover of a shape, we can create a simplicial representation of that shape such that the shapes are homotopy equivalent to it. 
A good cover is a cover where every non-empty intersection if contractable. We can then take that good cover and have each individual set count as a $0$ simplex, every intersection count as a $1$ simplex, every intersection of $n$ elements of the cover count as a $n-1$ simplex. Then this simplex is a representation represents the underlying shape 
![[Screenshot 2025-12-25 at 3.32.32 PM.png]]

# Vietoris Rips Complexes 
You might be wondering how we can apply these skills to data, and to do that we need to use Cech Complexes. We create one by taking a point cloud and then blowing up circles around each point in the point cloud with radius $\epsilon$. When then treat this as a cover for some shape. As you can see below we have detected that the points are in a circle 
![[Pasted image 20251227005013.png]]
Sometimes for computational efficiency, we instead use Vietoris Rips Complexes which  