#domain
The current problem that we are trying to solve is to find the parameters of the distribution that models motors binding and unbinding, and the density of myosin on the surface.
To do this we are able to track the individual actin filaments in which we get $L$ the length of the actin filaments, $T$ time of diffusion but some filaments may not diffuse

Parameters to find:
- $\lambda_1,\lambda_2,\lambda_3,\lambda_4$ that determine the transition rates between bound and unbound 
- $\alpha_1$ which is the number of myosin attached to a filament $F_1$ 

Assumptions 
- That $L_1 \propto \alpha_1$   
- All myosin are the same


The myosin transitions from bound to unbound with time $T_1 \sim \text{Hyperexpo}(\lambda_1,\lambda_2)$ and transitions from unbound to bound $T_2 \sim \text{Hyperexpo}(\lambda_3,\lambda_4)$. 

When all myosin are in the unbound state the actin diffuses. 



## Modeling a filament diffusing assuming all Myosin start bound 
In the case of two myosin:
THIS IS CURRENTLY NOT CORRECT BECAUSE IT DOES NOT ACCOUNT FOR UNBINDING 
$P(\text{Diffusion in time}[t_1,t_2])=$$P(\text{Myosin 1 unbinds for the first 1st before }t_2 \text{ and does not rebind until after }t_2\text{ and Myosin 2 unbinds for the 1st time at in }[t_1,t_2])$$+$$P(\text{Myosin 1 unbinds for the 2nd time before }t_2 \text{ and does not rebind until after }t_2\text{ and Myosin 2 unbinds for the 1st time at in }[t_1,t_2])$$+$
$...$
$+$$P(\text{Myosin 1 unbinds for the nth time before }t_2 \text{ and does not rebind until after }t_2\text{ and Myosin 2 unbinds for the 1st time at in }[t_1,t_2])$$+$$P(\text{Myosin 1 unbinds for the first 1st before }t_2 \text{ and does not rebind until after }t_2\text{ and Myosin 2 unbinds for the 2nd time at in }[t_1,t_2])$$...$
$+$$P(\text{Myosin 1 unbinds for the nth  before }t_2 \text{ and does not rebind until after }t_2\text{ and Myosin 2 unbinds for the 2nd time at in }[t_1,t_2])$$+$
$...$
$+$$P(\text{Myosin 1 unbinds for the nth 1st before }t_2 \text{ and does not rebind until after }t_2\text{ and Myosin 2 unbinds for the nth time at in }[t_1,t_2])$
$P(\text{Myosin 1 is bound at time } t)=P(\text{Myosin 1 stays bound until }t)+P(\text{Myosin 1 unbind plus bind}<t \text{ stays bound until t})$ 
$P(\text{Myosin 1 stays bound until }t)$ is $1-\text{CDF of bound to unbound}$ 
$P(\text{Myosin 1 unbind plus bind}<t)$ is the CDF of the convolution 




Myosin 1 unbinds for the first time at time $x$ and then rebinds fro the first time at time $y$ 