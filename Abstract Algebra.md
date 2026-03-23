---
tags:
  - Pure
---
Abstract algebra studies fundamental algebraic structures. These structures can be studied individually but it is often better to study them in the following order, as you can define them in reference to each other 


### Groups 
A group is the most basic structure, can be thought of as a set equipped with a binary operations
[[Groups]]

### Rings
The next natural progression would be a ring which is a set equipped with two binary which are commonly denoted as addition and multiplication 
[[Rings]]

### Fields 
Due to the nature of rings, the specific case of rings where every element has a multiplicative inverse(except the additive identity) denotes a special name known as fields
[[Field]] 

### Modules/Algebras
Then often the next step is studying vector spaces, modules and algebras. Due to the fact that I have already written about vector spaces in the linear algebra section, I will only be going over modules/algebras
[[Modules-Algebras]]


# Isomorphisms/Homomorphism/Automorphism
An homomorphism within the context of abstract algebra is a operation preserving function. This means that you can do "math" on either side of the function. An example of a Ring/Group homomorphism would be the natural map from $f: \mathbb{Z} \rightarrow \mathbb{Z}/2$. Notice that $f(a+b)=f(a)+f(b)$ which can easily be proven using parity. 
An isomorphism is a bijective homomorphism, which within the context of abstract algebra we typically consider two structures to be the same structure if there exists an isomorphism. This allows us to study both different structures, and gain insight into either. 
An example of this being useful is quaternions and $2\times 2$ complex matrices being isomorphic is super nice because matrices are way more computationally nice for computers(so you might as well represent it as matrices)
Additionally an automorphism is an isomorphism from a group to itself 