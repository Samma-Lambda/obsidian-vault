---
tags:
  - Applied
---
Topological Data Analysis(TDA) is a way if analyzing data using the skills from topology. It can be used for a variety of techniques but it mostly is used on point clouds. There are a few ways to generate point clouds from non-point cloud based datasets
## Forms of Point Clouds
### Raw Point Clouds
Since these are already point clouds you don't need to process them, often they are generated using Lidar Scanners or from 3D models
### Signals
By doing a delayed time embedding it is possible to turn a signal into a point cloud and then analyze it
### Images
You can actually turn images into point clouds but often there are better ways to analyze it 
### Data Capable of Vectorization
If you can turn some data into vectors then you can use TDA, this could be using some form of compression like an auto encoder. 

# Simplexes 
A simplex is a generalization of points, lines, and tetrahedra in higher dimensions. More specifically a $k$-simplex is a convex hull(a set of points where every convex combination is an element of it) of $k+1$ vertices points
![[Pasted image 20251227004610.png|300]]
There are oriented and unoriented simplexes. A simplex denoted $\{v_0,v_1,v_2,...v_n\}$ is unoriented while $(v_0,v_1,v_2,...v_n)$ is an orientated surface 
## The Boundary Operation
The boundary operation takes a $k$ simplex and outputs $k-1$ lower dimensional simplexes. 

# Simplicial Complex
A simplicial complex is a shape constructed from Simplexes. Formally it is 
1. A collection of $Z$ of $0$-simplexes
2. For each $k$ there exists a set of $k$-simplexes $\sigma=[z_0,z_1,...,z_k]$ where $z_k\in Z$, possibly the empty set 
3. Each $k$-simplex has $k+1$ faces, and all the faces must be contained within the simplicial complex. The faces are a $k$ simplex is $\{v_1,v_2,...,v_k\}$ are all the subsets containing $k-1$ elements
## Euler Characteristic
The Euler Characteristic of a simplicial complex is the alternating sum of the number of $k$ simplexes. It is denoted $\chi (S)=\Sigma_{d=0}^n (-1)^d (\text{number of k simplexes})$ 
## Cycles and Boundary 
The boundary is the output of some simplex with the boundary operation. A cycle is a the set that would be the output of the some simplex but is not 

# Chains
Chains are vectors in a vector space which is an algebraic way to represent simplexes. $C_k$ denotes the vector space of simplexes of dimension $k$. We do get to pick the field which is used as scalars within our vector field. 
The basis of each space is just the $k$-simplexes of the space
## The boundary operator as a homomorphism
The boundary operator being applied to the vector space yields a linear homomorphism to a lower dimension. For some simplicial complex $\delta_1:C_1(P)\rightarrow C_0(P)$  works as a linear homomorphism.
We can actually represent this function using a matrix mapping between the vector spaces, but this is tedious to do so I am not including it. Additionally in $\mathbb{Z}_2$ the boundary operator outputs cycles as the $0$ vector.
Further the composition of $\text{img}(\delta_{k-1})\subset \text{kern}(\delta_{k})$ leading to the sequence of the boundary operator being an exact sequence 
## Homology Group
We now can define the definition of a homology group specifically $H_k(X)=\frac{\text{kern}(\delta_k)}{\text{img}(\delta_{k+1})}$. Intuitively this is the the number is the group of $k$ dimensional holes. We can see this because the boundary operator maps cycles to $0$, but not all the cycles mapped to zero are "valid holes". There are some that are boundaries to higher dimensional simplexes and thus are filled in. 
## Betti Numbers
Now we have all the definitions to be able to define what a Betti number is, the $k$th betti number is $b_k=\text{rank}(H_k(X;\mathbb{Z}))$


# Algorithms 
## Persistant Homology
A filtration of a simplicial complex $X$ is a collection of sub-complexes $\{X_t|t\in\mathbb{R}\}$ such that $X_t\subset X_{t^{\prime}}$. Typically this $t$ is our distance value. We then can make barcodes which denote the value of the $k$th beti number over each value of $t$. 
Alternatively you can create a persistence diagram which communicates more about how the homology groups are changing. 
## ATOL


## Mapper 
The mapper algorithm is a way of getting a graphical representation of some high dimensional point cloud. It works by mapping the point cloud into some lower dimensional space, in which this lower dimensional space has 

## Ball Mapper


## Zigzag Persistance

## UMAP