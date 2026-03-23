---
tags:
  - Pure
---
# Introductory Definitions 
## Topological Space
A topological space is a set of objects $X$ and a subset of $P(X)$ denoted $\mathcal{T}$. The set $\mathcal{T}$ is known as a topology on $X$ and needs to satisfies the following properties 
- $X,\emptyset \in \mathcal{T}$ 
- $\mathcal{T}$ is closed under arbitrary union 
- $\mathcal{T}$ is closed under finite intersection 

## Open Sets
Elements of the topology are known as open sets. This is the way that we define closeness without a distance. The complement of open sets are known as closed sets, so for every open set $U\in \mathcal{T}$, there is a corresponding open set $X-U$. 
This definition means that open set and closed sets are not opposites and actually there are some sets that are "Clopen". Finally you an actually define a topology based off the closed sets but the axioms of a topology are slightly changed.


# Parts of a Set
## Closure
A closed set is a set that contains all its limit points. A simple example would be the sets $[0,1]$ in the standard topology. Similarly the closure of a set $A$ denoted as $\overline{A}$ is $A$ and all the limit points of $A$. This means that a set is only considered closed if $A=\overline{A}$ 
## Interior of a set
Similar to the closure of a set, the interior of a set is a way of generating an open set from some set $A$. The interior of $A$ denoted $\text{Int}(A)$ is the union of all the open sets entire contained within $A$

## Boundary of a set
These are the points that are inside and outside of the set, formally defined as $\overline{X}\cap \overline{X-A}$


# Limit Points
For a given set $A$(Not necessarily open or closed) the limit points are the points $x\in A$ such that for all open sets $U\in\mathcal{T}$ that contain $x$, $(U-\{x\})\cap A\neq\emptyset$. These intuitively are points which using the topology can't be separated from the rest of the points. 
An example would be the set $\{\frac{1}{n}|n\in \mathbb{N}\}$ in $\mathbb{R}_{\text{Std}}$ would have a limit point of $0$





# Sequences
A sequence is formally defined as function $f:\mathbb{N}\rightarrow X$, a sequence is said to converge to a point $x$ if for every single open set $U$ containing $x$ there exists some $i\in\mathbb{N}$ such that $f(i)\in U, \forall j \geq i$. An example of a sequence converging in $\mathbb{R}_{\text{Std}}$ would be the sequence $\{\frac{1}{n}|n\in \mathbb{N}\}$ converges to $0$


# Topological Basis 
A basis is another way of representing a topology, sometimes referred to as a topology in a suitcase. A basis is a set of sets that every element of a topology can be generated from the union(possibly infinite) of these sets. 
Examples of this could be the open balls of points within distance $\epsilon$ away from a point $x$ in $\mathbb{R}_{\text{Std}}$ 


# Topological Sub-Basis 
A set is considered to be a topological Sub-Basis if it generates a basis for some topology under finite intersection. 
An example of this would be the collection of rays in $\mathbb{R}$ being the set $\{x|x>a \text{ for some } a\in \mathbb{R}\}$


# Subspace Topology
In a given topological space $(X,\mathcal{T})$ if you have a set $Y\subseteq X$ then you can create a subspace topology. The sets within the topology of the subspace topology are defined as $\{U\cap Y| U\in \mathcal{T}\}$. 
An example of a subspace topology within $\mathbb{R}_{\text{Std}}$ would be $\mathbb{Q}$
![[Screenshot 2025-11-30 at 1.02.02 AM.png]]


# Product Topology
Again you can define a new topology from two smaller topologies by doing the "Cartesian Product" of two topologies. 


# Classification of Topological spaces
There are different types of topological spaces based off how separable spaces are 
- $\mathbf{T_1}$: In this space for all $x,y \in X$ such that $x\neq y$  exists $U_1,U_2\in \mathcal{T}$ such that $x\in U_1, y\not\in U_2$ and $x\not\in U_2, y\in U_1$ 
- **Hausdorff:** In this space for all $x,y \in X$ such that $x\neq y$  exists $U_1,U_2\in \mathcal{T}$ such that $x\in U_1, y\not\in U_2$ and $x\not\in U_2, y\in U_1$ and $U_1\cap U_2 = \emptyset$
- **Regular:** In this space for all $x\in X$ and every closed set $A\subset X$ such that $x\not\in A$, there exists $U_1,U_2\in\mathcal{T}$ such that $x\in U_1$ and $U_2\subseteq A$ and $U_1 \cap U_2 = \emptyset$ 
- **Normal:** In this space for all $A,B \subseteq X$ such that $A\cap B =\emptyset$ there exists $U_1$ and $U_2$ such that $A\subseteq U_1$ and $B\subseteq U_2$ and $U_1 \cap U_2 = \emptyset$ 
Basically there topological space classifications are defined by how separable they are. $T_1$ means that points can be separated but not entirely, **Hausdorff** means any two points can be fully separated, **Regular** means that any point and collection of points are separable, and **Normal** means that any two collection of points is separable.
A lot of really strong theorems stem from these types of spaces
