---
tags:
  - Pure
---
# Group Definition and Axioms
Groups are the most fundamental algebraic structure, they are simply put a set equipped with a single binary operation. They satisfy the following axioms 
- **Associativity** $(a+b)+c=a+(b+c)$ This basically takes a binary operation and allows it to take in any number of elements at the same time making our living considerably easier
- **Identity** $\exists e \in G$ such that $e+x=x+e=e, \forall x \in G$. This serves to allow us to have a "zero" element 
- **Closure** $\forall x,y \in G, (x+y)\in G$ this ensures that you can't escape this group via adding. An example of this would be adding two real numbers always gives you another real number 
- **Inverses** $\forall x \in G, \exists x^{-1}\in G$ such that $x+x^{-1}=e$. This is the final part that allows us to do "algebra" in the group by allowing ourselves to subtract

A set that satisfies these axioms allows us to do algebra on this set, which allows us to derive the following properties from the axioms 
- **Socks Shoes** This property states that $(AB)^{-1}=B^{-1}A^{-1}$ this is colloquially known as the socks shoes lemma, as when you put your socks on then shoes on to undo that you need to take your shoes off then socks off
- **There is only one identity** It is easy to prove that there is only one identity element in a group, because if there was two then they would be equal 
- **Inverse of the Inverse** This says that $(x^{-1})^{-1}=x$
- **The identity is its own inverse** $e^{-1}=e$ 
Importantly note that nowhere in the axioms does it require the binary operation to be commutative. This is by design as $\text{GL}(n)$ which is the set of all $n \times n$ matrices is a group but it is not commutative.


# Subgroups
A subgroup is exactly what it sounds like, it is a group entirely contained within another group. An example of this would be $(\mathbb{R},+)$ is a subgroup of $(\mathbb{C},+)$. This may not seem very useful but buy using cosets and normal subgroups we can actually study groups in a new way using their subgroups 

## Cosets
Let $G$ be a group and let $H$ be a subgroup of $G$. We can create a set of cosets by taking $H$ and multiplying it by some element in $G$ resulting in our cosets looking like $\{aH\text{ or }Ha|a\in G\}$. You may think that we can create a group from this cosets but that is not the case because $aH \text{ and } Ha$ are not the same. We need the original subgroup to be a normal subgroup for that to work 

## Normal Subgroups
Normal subgroups are defined two equivalent ways. They are either defined as being closed under conjugation meaning $\forall h \in H$ and $\forall g\in G$ it implies that $ghg^{-1}\in H$. Or it is alternately defined as the left and right cosets of $H$ are the same. 
You may be wondering why this is useful but it actually might be the most useful property in all of abstract algebra. Using a normal subgroup, you can create a quotient group which is a group where the elements are cosets. An example of this might be $\mathbb{Z}$ with the normal subgroup of $5\mathbb{Z}$, using this normal subgroup we can create the group $\mathbb{Z}/5$ which can tell us interesting properties about the integers mod $5$

## Lagranges Theorem
This states that a that the order of any subgroup must divide the order of the group. This is incredibly useful as it can quickly tell you if a set is a valid subgroup. Note beneath 
Additionally it enables RSA encryption and the mod power algorithm. 
$$
H\leq G \rightarrow |H|\Big||G|
$$
[[Mod Power Algorithm-RSA Encryption]]



# Orbit Stabilizer Theorem 
The orbit stabilizer theorem states that for a finite group $G$ we know that for $x\in G$ that $$|\text{Orb}(x)|\cdot|\text{stab}(x)|=|G|$$
where the orbit is all the places $x$ can reach. Formally defined as $\{g\cdot x:g\in G\}$
and the stabilizer is the set of all elements which leave $x$ fixed. This has some useful properties for combinatorics  


# Ways of Constructing Groups
It is useful to define ways of combining two groups into a larger group. For example a set of bits on a computer might be considered $\mathbb{Z}/2$ connected with more $\mathbb{Z}/2$. Because of this it can be useful to define ways of combining groups to make more groups. Additionally if we can prove that a group is isomorphic to the composition of groups, it can result in understanding the group in new ways allowing for computation efficiencies like multithreading.
## External Direct Product 
The direct product of a group is denoted using the symbol $\oplus$. We can create a group $G_1 \oplus G_2$ by having every single element be a tuple $(x,y)$ such that $x\in G_1$ and $y\in G_2$  and the binary operation between elements of this group are $(x_1,y_1)+(x_2,y_2)=(x_1+x_2,y_1+y_2)$. This is incredibly useful as it allows perfect multithreading
Examples are:
- $\mathbb{R}^2=\mathbb{R}\oplus \mathbb{R}$
- A string of $n$ bits is $\mathbb{Z}/2^{\oplus n}$ 

## Semi-direct Product
While having the groups be completely separate when you combine them is nice. But sometimes you want to have one of them to twist another. An example would be a group encoding rotation and translations. 
We denote this using $\ltimes$ so $N\ltimes H$ is our group.
In order to do this we need a homomorphism 
$$
\phi:H\rightarrow \text{Aut}(N)
$$
and the elements of $N\ltimes H$ are $(x,y)$ where $x\in N$ and $y\in H$. The binary operation is denoted $(x_1,y_1)+(x_2,y_2)=(x_1\phi_{y_1}(x_2),y_1+y_2)$.
Examples are:
- $SE(3)$ encoding translations and rotations 
- $D(n)$ the dihedral group 

## Wreath Product 
This is another way to construct a group. For two groups $A$ and $B$ the wreath product is denoted $A\int B$. The two components are 
1. The base group: $A^{|X|}$ meaning the direct product of $|X|$ $A$'s one for each element of $A$
2. The top group: $B$ which is a group acting on the elements of $X$ 
We can define the $A\int B$ as $A^{|X|}\ltimes B$ where $\phi:B\rightarrow \text{Aut}(A^{|X|})$ is defined as $\phi(b)(f)(a)\rightarrow f(b^{-1}\cdot x)$. Where $b^{-1}$ is shuffling the elements of $A^{|X|}$ the way that it would with elements of $X$(which is why we have one element for each element of $X$). 
Examples 
- Rubik Cube 

## Free Product
The free product of two groups $G$ and $H$ is denoted as $G*H$. It works by taking all the elements of $G$ and all the elements of $H$ and then creating words out of them by alternating from each group(technically its not alternating but because groups are closed it is going to look like its alternating) This creates a group of words
This is useful as if there exists homomorphism $\phi_G:G\rightarrow K$ and $\phi_H:H\rightarrow K$ then there exists a unique homomorphism from $\phi:G*K\rightarrow K$
