$\langle \psi_0 | \psi_1 \rangle$ is the complex version of dot product but it conjugates the first vector $\psi _0$  

$|\psi_0\rangle\langle \psi_1|$ is normal matrix multiplication so it results in a matrix. It also has the nice touch that $|\psi_0\rangle\langle \psi_1|v=\langle \psi_0 |v\rangle |\psi_1\rangle$ 

A projective measure is a set of matrices $\{P_0,...,P_n\}$ such that $\Sigma P_n=I$. When you apply it to a qubit it results in the qubit collapsing to one of the mutually exclusive states with state $i$ having a probability of $\langle \psi |P_0|\psi \rangle$ or $TR(P_i |\psi\rangle\langle \psi |)$  


From above we know that $\frac{1}{2}P(0|\psi_0)+\frac{1}{2}P(1|\psi_1)$ equals $\frac{1}{2}\langle \psi_0|P|\psi_0\rangle+\frac{1}{2}\langle \psi_1|I-P|\psi_1\rangle$

Any vector can be decomposed into a vector in a subspace and a vector in the ortho complement. In fact a vector space is isomorphic to $V\oplus V^{\perp}$, and any matrix if you pick the right basis can be written in block form and when you expand it out it becomes appartant that only the part that maps $V$ to itself is important 

##### Proof Good
Let $n\in\mathbb{N}$. Let $|\psi_0\rangle$ and $|\psi_1\rangle$ be arbitrary distinct $n$-qubit states. 

Let $V$ be the subspace spanned by $\{\psi_0,\psi_1\}$. By the orthogonal decomposition theorem every vector $x$ can be written as $x=x_V+x_{V^{\perp}}$, where $x_{V}\in V$ and $x_{V^{\perp}}\in V^{\perp}$.

Let $P$ be an arbitrary projection operator. Note that our objective function is defined as $\frac{1}{2}\langle \psi_0|P|\psi_0\rangle+\frac{1}{2}\langle \psi_1|I-P|\psi_1\rangle$. 

The vectors $\psi_0$ and $\psi_1$ can be written as $\psi_{0V}+\psi_{0V^{\perp}}$ and $\psi_{1V}+\psi_{1V^{\perp}}$ respectively. 

Thus our objective function is $\frac{1}{2}\langle \psi_{0V}+\psi_{0V^{\perp}}|P|\psi_{0V}+\psi_{0V^{\perp}}\rangle+\frac{1}{2}\langle \psi_{1V}+\psi_{1V^{\perp}}|I-P|\psi_{1V}+\psi_{1V^{\perp}}\rangle$. But since $\psi_0$ and $\psi_1$ lie in $V$ by definition, so $\psi_{0V^{\perp}}=0$ and $\psi_{1V^{\perp}}=0$. Thus our objective function equals $\frac{1}{2}\langle \psi_{0V}|P|\psi_{0V}\rangle+\frac{1}{2}\langle \psi_{1V}|I-P|\psi_{1V}\rangle$. By linearity $\frac{1}{2}\langle \psi_{1V}|I-P|\psi_{1V}\rangle=\frac{1}{2}\langle \psi_{1V}|I|\psi_{1V}\rangle-\frac{1}{2}\langle \psi_{1V}|P|\psi_{1V}\rangle$ which further simplifies to $\frac{1}{2}\langle \psi_{1V}|\psi_{1V}\rangle-\frac{1}{2}\langle \psi_{1V}|P|\psi_{1V}\rangle$. Thus our objective function equals $\frac{1}{2}\langle \psi_{1V}|\psi_{1V}\rangle-\frac{1}{2}\langle \psi_{1V}|P|\psi_{1V}\rangle+\frac{1}{2}\langle \psi_{0V}|P|\psi_{0V}\rangle$.

Lets define a basis of $\{\psi_0,\psi_1\}$ and $2^{n}-2$ other vectors not in $V$. We can now define $P$ as a block matrix $\begin{bmatrix} P_{VV} & P_{VV^{\perp}} \\ P_{V^{\perp}V} & P_{V^{\perp}V^{\perp}} \end{bmatrix}$. Note that since we will only ever pass in $\psi_0$ and $\psi_1$ the two blocks $P_{V^{\perp}V}$ and $P_{V^{\perp}V^{\perp}}$ are irrelevant. Additionally $P_{V V^{\perp}}$ does not matter because it outputs a vector orthogonal to $\psi_1$ and $\psi_0$.  We can't set the blocks to zero but we do know that $P_{VV}$ is hermitian because $P$ is a projector  

Now we can prove that $P_{VV}$ is a $2$D projector because $P$ is a projector. Thus $P^2=P$ which implies that $\begin{bmatrix} P_{VV} & 0 \\ 0 & 0 \end{bmatrix}=\begin{bmatrix} P_{VV} & 0 \\ 0 & 0 \end{bmatrix}^{2}$ which further implies that $P_{VV}=P_{VV}^2$. Additionally since $P=P^{*}$ it implies that $\begin{bmatrix} P_{VV} & 0 \\ 0 & 0 \end{bmatrix}=\begin{bmatrix} P_{VV} & 0 \\ 0 & 0 \end{bmatrix}^{*}$ which further implies that $P_{VV}=P_{VV}^{*}$. Thus $P_{VV}$ is a projector. 



##### Proof
Let $n\in\mathbb{N}$. Let $|\psi_0\rangle$ and $|\psi_1\rangle$ be arbitrary distinct $n$-qubit states. 

Let $V$ be the subspace spanned by $\{\psi_0,\psi_1\}$. By the orthogonal decomposition theorem every vector $x$ can be written as $x=x_V+x_{V^{\perp}}$, where $x_{V}\in V$ and $x_{V^{\perp}}\in V^{\perp}$.

Let $P$ be an arbitrary projection operator. Note that our objective function is defined as $\frac{1}{2}\langle \psi_0|P|\psi_0\rangle+\frac{1}{2}\langle \psi_1|I-P|\psi_1\rangle$. 

Each vector $\psi_0$ and $\psi_1$ can be written as $\psi_{0V}+\psi_{0V^{\perp}}$ and $\psi_{1V}+\psi_{1V^{\perp}}$ respectively. 

Thus our objective function is $\frac{1}{2}\langle \psi_{0V}+\psi_{0V^{\perp}}|P|\psi_{0V}+\psi_{0V^{\perp}}\rangle+\frac{1}{2}\langle \psi_{1V}+\psi_{1V^{\perp}}|I-P|\psi_{1V}+\psi_{1V^{\perp}}\rangle$. But since $\psi_0$ and $\psi_1$ lie in $V$ by definition, $\psi_{0V^{\perp}}=0$ and $\psi_{1V^{\perp}}=0$. Thus our objective function equals $\frac{1}{2}\langle \psi_{0V}|P|\psi_{0V}\rangle+\frac{1}{2}\langle \psi_{1V}|I-P|\psi_{1V}\rangle$. By linearity $\frac{1}{2}\langle \psi_{1V}|I-P|\psi_{1V}\rangle=\frac{1}{2}\langle \psi_{1V}|I|\psi_{1V}\rangle-\frac{1}{2}\langle \psi_{1V}|P|\psi_{1V}\rangle$ which further simplifies to $\frac{1}{2}\langle \psi_{1V}|\psi_{1V}\rangle-\frac{1}{2}\langle \psi_{1V}|P|\psi_{1V}\rangle$. Thus our objective function equals $\frac{1}{2}\langle \psi_{1V}|\psi_{1V}\rangle-\frac{1}{2}\langle \psi_{1V}|P|\psi_{1V}\rangle+\frac{1}{2}\langle \psi_{0V}|P|\psi_{0V}\rangle$.

Now we can change the basis of $P$ so that it has a basis of $\{\psi_0,\psi_1\}$ and then the other basis vectors. Then we can define a block matrix with parts of $P_{VV},P_{VV^{\perp}},P_{V^{\perp}V},P_{V^{\perp}V^{\perp}}$. Since we are only gonna pass $\psi_0,\psi_1$ into $P$ the $P_{V^{\perp}V},P_{V^{\perp}V^{\perp}}$ don't matter. $P_{VV^{\perp}}$ results in zero because it will map the vector to something orthogonal. Thus the only thing we need to find is $P_{VV}$ which is a $2\times 2$ matrix
WANT TO PROVE
That $P_{VV}$ is itself a projector. $P_{VV}$ must be equal to its dagger because otherwise $P$ would not be an operator. It also much be its square for the same reason  
Prove that $1$ dimensional projectors are of the form $|u\rangle \langle u |$




So now we need to find the vector $u$ that maximizes $\frac{1}{2}\langle \psi_0||u\rangle\langle u||\psi_0\rangle+\frac{1}{2}\langle \psi_1|I-|u\rangle\langle u||\psi_1\rangle$. We can drop the half because it is irrelevant for optimization. 
$\langle \psi_0||u\rangle\langle u||\psi_0\rangle$ further simplifies to $|\langle u | \psi_0\rangle|^2$ because if you look at it thats thus we can write the problem as $|\langle u | \psi_0\rangle|^2 - |\langle u | \psi_1 \rangle|^2+\langle \psi_1||\psi_1\rangle$ 
which then we can remove all constants getting $|\langle u | \psi_0\rangle|^2 - |\langle u | \psi_1 \rangle|^2$
Which can be rewritten as $\langle u ||\psi_0\rangle \langle \psi_0 ||u\rangle-\langle u ||\psi_1\rangle \langle \psi_1 ||u\rangle$ which equals $\langle u||\psi_0\rangle \langle \psi_0|-|\psi_1\rangle \langle \psi_1 ||u\rangle$ 
WANT TO PROVE
that $|\psi_0\rangle \langle \psi_0|-|\psi_1\rangle \langle \psi_1 |$ is hermitian super easy to prove using the fact that $(A+B)^{*}=A^{*}+B^{*}$


This is now in Rayleigh quotient form which tells us that the maximimal value is the largest eigenvalue of the matrix. And that the eigenvector with the largest eigenvalue is the optimal vector
finding the eigenvalues are a known formula 
once you know the eigenvalues you can easily find the eigen space of that eigenvalue to find $u$. 

https://www.sjsu.edu/faculty/guangliang.chen/Math253S20/lec4RayleighQuotient.pdf

