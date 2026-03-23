---
tags:
  - Pure
---
# Categories
A category $C$ is a collection of objects $\text{Obj}(C)$ and morphisms $\text{Hom}_C(a,b)$ individual arrows are known as morphisms. It can help to think of categories as graphs with morphisms as edges and objects as nodes. It obeys the following properties 
1. if there exists $\text{Hom}_C(a,b)$ and $\text{Hom}_C(b,c)$ then there is some morphism $\text{Hom}_C(a,c)$ this makes every category a commutative diagram
2. Composition of morphisms is associative $(f\cdot g) \cdot h=f\cdot (g \cdot h)$
3. For each object there is an identity morphism $I$ such that $f\cdot I$ 
A category is consider **Small** if its collection of objects is a set, and **Finite** if its collection of objects is finite. 
Examples of categories include $\mathbb{R}$ and $\geq$, Vector spaces and their linear transformations, groups and their isomorphisms.
By the construction of our categories we can always create another opposite category $C^{\text{op}}$ such that $\text{Hom}_C(x,y)=\text{Hom}_{C^{\text{op}}}(y,x)$. An example of this relationship could be homology and cohomology 

# Subcategories 
A subcategory is exactly what it sounds like its a subset of the objects and morphisms of some category. We consider a subcategory $C\subseteq D$ to be **full** if $\forall a,b \in C$ $\text{Hom}_C(a,b)=\text{Hom}_D(a,b)$ 


# Initial/Terminal Objects
An object $x$ in a category is considered **Initial** if for every single object $y$ in $C$ there is some morphism from $x$ to $y$. Similarly an object $x$ is considered to be terminal if every object $y$ in the category has some morphism $y$ to $x$. An example of a Initial object might be $\emptyset$ in the category of set, and in the category $\text{Open}(X)$ then $X$ itself is terminal 


# Functor
A functor $F$ is a function which maps from one category to another. It can be thought of as a function one mapping the objects to other objects $F_\text{obj}:\text{Obj}(C)\rightarrow \text{Obj}(D)$ and functions $F_{iso}:\text{Hom}_C(a,b)\rightarrow \text{Hom}_D(a,b)$ for all $a,b \in C$. 
