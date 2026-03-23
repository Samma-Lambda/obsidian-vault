---
tags:
  - Pure
---
# Introductory Definitions

## Knots 
A knot within math if defined as a closed loop in space. This means that knots are strings with no lose ends, they so they are circles altered in some way. 
![[Screenshot 2025-12-01 at 10.41.48 AM.png]]

## Links
A **Link** are a collection of closed loops connected in some way. It is important to note that a collection of knots and a link are different things as it allows interaction between the knots
Knots can represented a variety of ways either as string in 3D space(though this is often hard to work with) or a 2D crossing diagram. 

## Reidemeister Moves 
Reidemeister Moves otherwise known as R-moves are actions you can do on a knot diagram that leave the knot
![[Pasted image 20251201120741.png]]

# Knot Invariants 
Since knots are often incredibly hard to tell apart, its often nice to define **invariants** on them. **Invariants** are functions which map from a knot into some other space such that all equivalent knots have the same output. 
It is very important that two inequivalent knots can have the same knot invariant and still not be the same, but two knots can't have the same invariant and be the equivalent knots. 

## Crossing Number
The crossing number of a knot is the minimum number of crossings needed to represent the knot using a knot diagram. This is an invariant, but can often be hard to find but always is the result of a series of R-moves

## Unknotting Number
This is the number of self intersections that would result in the knot being R-equivalent to the unknot 

## Chirality 
This is like Chirality in chemistry, this is defined as a knot is equivalent to its mirror image. If a knot is equivalent to its mirror image, then it is considered Achiral. If it is knot equivalent to its mirror image then it is considered chiral. An example of this would be the trefoil knot


## $p$-Colorability/Knot Determinate 
Let $p$ be on odd prime, a knot is considered $p$ colorable if each arc of the diagram can be labeled with $\{0,1,2,...,p\}$ such that 
1. There are two distinct labels 
2. At each crossing $2a-b-c\equiv 0 \text{ mod }p$ 
![[Pasted image 20251201130236.png|300]]


# Knot Representations 
There are a large way of representing a knot, and while they all represent a closed loop in 3D. There are some invariants that can only be calculated when looking at a knot under a specific representation 
## 3D space
This is what a knot is in the "Real World" it is a closed loop. This is a really difficult representation to work with so we have invented other representations ![[Pasted image 20251204202001.png|200]]
## Crossing Diagram 
This is typically the easiest way to draw a knot. It shows the crossings and looks like below 


# Special Types of Knots
