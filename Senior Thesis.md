
# Definition
An automorphism of a graph is a way of relabelling the vertices in a way that leaves it isomorphic. 
The fixing number is a set of vertices which stay the same allow only the trival automorphism. 
A fixing set is a set of vertices which when fixed leave only the trivial automorphism. 
A determining set is a set of vertices which then if two automorphism agree on then they are the same

# Open problem
The greedy fixing algorithm is 
1. Find the vertex with the largest orbit 
2. Fix it 
3. Repeat until all the stabilizers are trivial
This is because all the stabilizers are trivial 

Is the greedy fixing algorithm well defined for every graph. Additionally if it is prove that $\text{fix}_{greedy}(G)\geq \text{fix}(G)$  