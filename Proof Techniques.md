---
tags:
  - Pure
---

## Traditional Proofs
The main three proof techniques are direct proof $P\rightarrow Q$, Contrapositive $\neg Q \rightarrow \neg P$, and $\neg (P\land \neg Q)$. This is pretty much all you would ever need in most classes.

## Proof By Induction
This is like setting up dominos and proving if you knock over the $n\text{th}$ domino then you would knock over the $n+1\text{th}$ domino. You prove this by proving a base case (Simple small cases to start the dominos) and then proving the inductive hypothesis(proving that the $n+1\text{th}$ domino is knocked over if the $n\text{th}$ domino is knocked over) 

## Probabilistic Method 
This technique is used to prove the existence of an object. This is useful usually in combinatorics, and graph theory. 
1. **Using Expected Value:** If you find the expected value of a set of objects under some statistic, and find that value is greater than your goal. Then you know there exists some element with a statistic higher than your goal. 
2. **Using Non-Zero Probability:** If you set up some probabilistic situation and prove that the probability of a specific thing has a non-zero probability, you have successfully proved its existence


## Functional Proofs
You can use functions and the properties that they preserve to prove things. 
1. **Counting Via Bijection:** If you define a bijection between two sets of objects, then the order of the objects must be the same. Another way you could do this is by defining two injective functions one $A\rightarrow B$ and the other $B\rightarrow A$
2. **Isomorphisms preserving Properties:** If you wanted to prove that a group is abelian, then you could construct an isomorphism to another abelian group.
Additionally you could use these for contradiction and prove that there could never exist a bijection or isomorphism to prove things 



## Invariants 
These are properties that are preserved no matter how you represent something. An example would be the Euler Characteristic of a graph. If two graphs have different Euler Characteristic then they are not isomorphic. 