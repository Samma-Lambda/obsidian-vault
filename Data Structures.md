---
tags:
  - Computer
---
# Hash Functions 
Hash function are not very useful on their own but they are essential in more complicated data structures. A hash function is a function which maps a variable size input of data into a fixed size value. This means that it can take in strings, integers, floats, ect and will still output the same sized value.
There a few properties that all has functions should have 
1.  **Deterministic:** A hash function should always output the same value if the same input is inputed
2. **Uniformly Distributed:** All outputs should be equally likely, this helps minimize the collision chance
3. **Pre-image Resistance:** It should be incredibly hard to synthesize an input that gives you a specific output
4. **Sensitive to small perturbations:** Changing the input value slightly will result in a massively different hash value
These functions are useful in situations where you want to generate a user ID


# Linked List
This is pretty much the simplest data structure, and it is nicely described in the diagram beneath 
![[Pasted image 20251128233756.png]]
The first type is the singly linked list, it is a single node with a value and then the address of the next node. This lets you "Pull" yourself along until you find the value you are searching for. This results in very little RAM being used when searching. 


# Queue/Stack
This data structure is exactly what it sounds like. It is an array where you can only either retrieve the top element or the bottom element based on wether it is a queue or a stack.


# Hash-map
A hash map is a hash function which evenly divides the data into linked its. It works by taking in a value, hashing it and then appending the start of that number of linked list. ![[Screenshot 2025-12-25 at 9.12.24 PM.png]]


# Filters
These are structures that you can add that only look at a element whenever it gets added to an array. Thus they increase the insertion time only slightly but offer better benefits like keeping track of the number of elements of a specific type
## Bloom Filters
This is something that you could add to a hash map or a similar data structure. It works by creating an array of $n$ bits where $n$ can be any size you want. Then whenever you append an element to the structure, you pass the element through multiple hash functions mod $n$ and then flip those bits.
Now if you want to check if an element has been appended to your data structure, you can quickly tell by checking the bits that would have been flipped by hashing it. This won't tell you if an element is in your data structure, but it can tell you if something is not in your data structure 

## Hyperloglog
This allows you to get a rough estimate to the number of distinct elements that have been added to a structure. It works by taking in an element and then assigning it to a random stream(there is a pre-established set number of them). Then each steam hashes the element and keeps track of the number of leading zeros $0010101$ has $2$ leading $0$'s.
Then you take the harmonic mean of all the streams estimated number of distinct elements and then you get an estimate for the number of distinct elements that have been entered. 
Intuitively this works because given $4$ elements entered we expect to see $1$ element that hashes with $2$ leading $0$'s. We split it into steams to get a better estimate because otherwise our cardinality estimate is restricted to a power of $2$ 

## Min-Sketch 
Min sketch is similar to Hyperloglog but it estimates the number of times a specific element passes though a data stream. It works by setting up an array which each row has a specific has function, then whenever an element is added to our underlying structure, we hash each element and then mod it by the number of columns incrementing the spot which is the hash value mod the number of columns. 
Then if you want an estimate of the number of times a specific element gets added you just look at all the places it hashes to and take the minimum value



# Trees
Trees are technically graphs with no cycles. Often this results in a graph that is used to represent parent child relationships 
## Trie(Prefix Tree)
Rather than something like a binary tree where the keys are stored in the nodes, in this the part of a node represents a relationship or prefix. An example of this could be used for autocomplete which is shown below. These trees are incredibly useful when you have partial information and need to complete it or see how it can be completed 
![[Screenshot 2025-12-27 at 12.13.24 AM.png]]

## AVL Tree
An AVL tree can be thought of as a balanced B-tree. This means it avoids the problem where the B-tree becomes unbalanced and then becomes a linked list(when everything gets placed to the left or right on every insert). This means that the height of the tree will always be $\log n$ meaning the smallest search time will be $\log n$.

## Quad Trees
A quad tree is a way of storing 2D spatial information. It works by having a starting tree that divides the space into $4$ quadrants. Then if any of the quadrants contain multiple points then it recurses and splits that quadrant into $4$ quadrants. This makes it so finding the number of points within a specific bounds really quickly