#domain
The current problem that we are trying to solve is to find the parameters of the distribution that models motors binding and unbinding, and the density of myosin on the surface.
To do this we are able to track the individual actin filaments in which we get $L$ the length of the actin filaments, $T$ time of diffusion but some filaments may not diffuse

Parameters to find:
- $\lambda_1,\lambda_2,\lambda_3,\lambda_4$ that determine the transition rates between bound and unbound 
- $\alpha_1$ which is the number of myosin attached to a filament $F_1$ 

Assumptions 
- That $L_1 \propto \alpha_1$   
- All myosin are the same
- $\lambda_1 = $


The myosin transitions from bound to unbound with time $T_1 \sim \text{Hyperexpo}(\lambda_1,\lambda_2)$ and transitions from unbound to bound $T_2 \sim \text{Hyperexpo}(\lambda_3,\lambda_4)$. 

When all myosin are in the unbound state the actin diffuses. 



## Modeling a filament diffusing assuming all Myosin start bound

Continuous time Markov chain for a single myosin with states $\{1,2,3,4\}$
$$
M=\begin{bmatrix}  
-\lambda_1 & \lambda_1 & 0 & 0\\  
0 & -\lambda_2 & \lambda_2 & 0\\
0 & 0 & -\lambda_3 & \lambda_3 \\
\lambda_4 & 0 & 0 & -\lambda_4
\end{bmatrix}
$$
But if we want to encode the states of multiple myosin we use the Kronecker product. So to get the matrix of $k$ myosin we make the matrix $M^{(k)} = \sum_{i=1}^k I^{\otimes (i-1)} \otimes M \otimes I^{\otimes (k-i)}$ which will have states $\{1,2,3,4\}^{\times k}$. 

To find the expected diffusion time of $k$ myosin we need to calculate the hitting time of the state $4...4$. Calculating a hitting time is the same at the absorption time if we have all the hitting states become absorbing(for the sake of calculation)

In the context of myosin this means setting the row corresponding to $(44444)$ and then 
