---
tags:
---
#domain 
This is the study of how probability can lead to computational advantages
# Chapter 1: Introduction to Probability 
In this chapter they introduce basic concepts like the axioms of probability, bayes rule and LOTP. I don't feel the need to go into detail 

## Theta Notation 
Given a function $g$ and $f$ we would say that $f$ is in $\Theta(g)$ if there exists some $c_1,c_2,n_0 \in\mathbb{R}$ such that $c_1 g(n)\leq f(n) \leq c_2 g(n)$ for all $n\geq n_0$. This can be though of as an exact time complexity rather than a upper or lower bound. Conceptually and definitionally this is a set of functions 

## Big O notation
Given a function $g$ and $f$ we would say that $f$ is $O(g)$ if there exists some $c,n_0 \in\mathbb{R}$ such that $f(n) \leq c g(n)$ for all $n\geq n_0$. This can be though of as an upper bound of the function. Conceptually and definitionally this is a set of functions 

## Little O notation 
Given a function $g$ and $f$ we would say that $f$ is $o(g)$ if there exists some $c,n_0 \in\mathbb{R}$ such that $f(n) < c g(n)$ for all $n\geq n_0$


## Polynomial Equality Verification
Given two polynomials one factored(in the form of $g(x)=(x-a_1)(x-a_2)...(x-a_n)$) and one in canonical form($f(x)=b_1x^d+b_2x^{d-1}+...+b_n$). To deterministically solve this we would have to factor out the factored form which would take $\Theta(d^2)$ multiplication operations where $d$ is the degree.
But we can actually solve this non-deterministically, using the fact that if $f(x)=g(x)$ then $f(x)-g(x)=0$. Thus if we plug in some value $\alpha$ and we get $f(\alpha )\neq g(\alpha)$ then we know the polynomials are not equal.
Additionally since polynomials are closed under addition, we know that $f(x)-g(x)$ is a polynomial with degree at most $d$, meaning that it has at most $d$ real roots. 
Thus if we create the set $\{0,1,...,100d\}$ there are at most $d$ roots in this set, meaning that the probability or randomly selecting a root is $\frac{1}{100}$ 
If we have some randomly selected value $\alpha$, we can find the value of $f(\alpha)$ and $g(\alpha)$ with time complexity $O(d)$. If we find that $f(\alpha)\neq g(\alpha)$ then we return false, if $f(\alpha)=g(\alpha)$ then we can try another random value if we want, or if we have done enough trials we can conclude that $f(x)=g(x)$ 
If we test $c$ of these values we have a probability of less than $(\frac{1}{100})^c$ of returning the wrong answer with a time complexity of $\Theta(cd)$. Its important to note that if $c=d$ then $\Theta(cd)=\Theta(d^2)$ which is the complexity as the deterministic algorithm.  


## Matrix Equality Verification
Given three matrices $A,B,C\in M_{n\times n}(\mathbb{Z}/2)$ we want to be able to verify wether $AB=C$. If we were to find this using matrix multiplication it would take roughly $\Theta(n^3)$ operations(Counting the number of element multiplications which take place).
But similarly to the polynomial equality verification if $AB=C$ then for all vectors $r$ $ABr=Cr$. 
We can compute $ABr$ as $A(Br)$ with a time complexity of $\Theta(n^2)$.
Let $D=AB-C$ and assume that $D\neq 0$ thus there exists at least one element in $D$ that is non-zero, arbitrarily named $d_{11}$.
We we create a uniformly random vector $r$(filled with ones and zeros) if $Dr\neq 0$ then we return false, if $Dr=0$ then we know that $\Sigma_{j=1}^n d_{1j}r_j=0$ which can be rewritten into $r_1 = -\frac{\Sigma_{j=2}^{n}d_{1j}r_j}{d_{11}}$ the left side either takes a value $0$ or $1$ and the $r_1$ has a 50% chance of taking on that value.
Thus our algorithm where we plug in $k$ vectors has a time complexity of $\Theta (kn^2)$ and a probability of failure of $(\frac{1}{2})^k$ 
In line with what we have previously done for any finite field $F$ the given $n$ samples the probability of failure is $(\frac{1}{|F|})^n$. This even holds for continuous matrices which then its often still better to use bit vectors as the inputs because then the math is super quick


## Min-Cut Algorithm
For a graph the min cut is the minimal set of edges who's removal result in the graph becoming two disjoint connected components. In order to understand this algorithm you need to know what an edge contraction is, for some edge $\{u,v\}$ we contract it by making $u$ and $v$ into a single vertex with all edges connected to $u$ and $v$ now connected to this new vertex. Two vertexes are allowed to have more than one edge connecting them. 
The algorithm works by uniformly selecting an edge in the graph, and then contracting it. It does this process $n-2$ times until there are two vertices left. The edges between the final two vertices are the edges for our proposed min-cut. It will always return a cut set but not necessarily the minimum one. 
We can calculate the probability of it returning the min-cut as follows. Let $C$ be the set of edges that constitute the min-cut.
Let $E_i$ be the event that at step $i$ the edge contracted was not in $C$ and let $F_i-\bigcap_{j=1}^n E_{j}$. If we can calculate $P(F_{n-2})$ then we have calculated the probability of returning the min cut. First we calculate the $P(F_1)=P(E_1)=1-\frac{2k}{nk}$ we get this because if $|C|=k$ then every single vertex of the graph has at least $k$ edges(otherwise we could just cut the vertex edge away). Thus the graph has at least $\frac{nk}{2}$ edges. Thus $P(E_1)=1-\frac{k}{\frac{nk}{2}}=1-\frac{2k}{nk}=1-\frac{2}{n}$. 
Then we can calculate $P(E_i|F_{i-1})=1-\frac{k}{k(n-i+1)/2}$ 
Thus $P(F_{n-2})=P(E_{n-2}\cap F_{n-3})=P(E_{n-2}|F_{n-3})P(F_{n-3})=P(E_{n-2}|F_{n-3})P(E_{n-3}|F_{n-4})...P(F_1)\geq\Pi_{i=1}^{n-2}(1-\frac{2}{n-i+1})$ The final product can be rewritten using $\Pi_{i=1}^{n-2}(\frac{n-i+1}{n-i+1}-\frac{2}{n-i+1})=\Pi_{i=1}^{n-2}(\frac{n-i-1}{n-i+1})=(\frac{n-2}{n})(\frac{n-3}{n-1})(\frac{n-4}{n-2})...(\frac{3}{5})(\frac{2}{4})(\frac{1}{3})=\frac{2}{n(n-1)}$ 
Thus our probability of getting the min-cut is $\frac{2}{n(n-1)}$ 
We can run this multiple times we can get a higher chance of getting the min cut, and if we run it $n(n-1)\text{ln}(n)$ times we get $(1-\frac{2}{n(n-1)})^{n(n-1)\text{ln}(n)}$. Using the property that $1-x\leq e^{-x}$ we get
$(1-\frac{2}{n(n-1)})^{n(n-1)\text{ln}(n)}\leq e^{-\frac{2}{n(n-1)}n(n-1)\text{ln}(n)}=\frac{1}{n^2}$ 

# Chapter 2: Random Variable and Expectations
In this chapter they introduce random variables and expected value but I am not going explain it because I already know it. 
## Coupons Collector Problem 
The coupon collector problem is model for someone trying to collect $n$ distinct objects where each trial you get a uniformly distributed object. To find the expected value of this, we can write the time that it takes to get the final coupon as $1+\text{Geom}(\frac{n-1}{n})+\text{Geom}(\frac{n-2}{n})+...+\text{Geom}(\frac{1}{n})$ which has the expected value is $\Sigma_{i=1}^{n} \frac{n}{n-i+1}=n\Sigma_{i=1}^{n} \frac{1}{n-i+1}=n\Sigma_{i=1}^{n}\frac{1}{i}$. The value of $\Sigma_{i=1}^{n}\frac{1}{i}$ is known as the $n\text{th}$ harmonic number and has a value of $\text{ln}(n)+\Theta(1)$ and thus the coupons collectors problem has an expected value of $n\text{ln}(n)+\Theta(n)$ 

## Expected time of Quick-sort
The quick sort algorithm runs by doing the following. For some list of distinct elements $S=\{x_1,x_2,...,x_n\}$ it starts by picking some random pivot which we can call $x_{p_1}$ which will act as our pivot. Then it takes all the other elements and then divides the element into two sublists $S_1$ and $S_2$ based off wether $x_i<x_{p_i}$. It then recursively runs on on the two sublists and returns $S_1,x_{p_1},S_2$ which will be sorted

To derive the expected time complexity we define $y_1,...,y_n$ to be the full sorted $x_1,...,x_n$. We define indicator variables $I_{ij}=1$ if element $y_i$ is compared to element $y_j$ with $i<j$. Thus the expected number of comparisons are $\Sigma_{i=1}^{n-1}\Sigma_{j=i+1}^{n}I_{ij}$ and $E[\Sigma_{i=1}^{n-1}\Sigma_{j=i+1}^{n}I_{ij}]=\Sigma_{i=1}^{n-1}\Sigma_{j=i+1}^{n}E[I_{ij}]$ by the linearity of expectations. Thus we just need to find the probability that $I_{ij}=1$ 

We know that $y_i$ and $y_j$ get compared if they are both in the same list(or sublist) and one of them gets selected as the pivot. But it all works out to only matter wether an element between them is selected before one of them are selected. Thus $P(I_{ij}=1)=\frac{2}{j-i+1}=E[I_{ij}]$

Thus $E[X]=\Sigma_{i=1}^{n-1}\Sigma_{j=i+1}^{n}\frac{2}{j-i+1}$ which setting $k=j-i+1$ equals $\Sigma_{i=1}^{n-1}\Sigma_{k=2}^{n-i+1}\frac{2}{k}$ using a change of summation variables(when $j=i+1$ then $k=2$ and when $j=n$ then $k=n-i+1$). We can write this further because looking that the values that $k$ can take we see that $k<n-i+1$ which means that $i<n-k+1$ and that the highest value of $k$ can be achieved when $i=1$ which says $k<n$. Thus we can rewrite out bound as $\Sigma_{k=2}^n \Sigma_{i=1}^{n+1-k}\frac{2}{k}$ which equals $\Sigma_{k=2}^n (n+1-k)\frac{2}{k}$. Next we can rewrite this as $\Sigma_{k=2}^{n}(n+1)\frac{2}{k}-2=2(n+1)\Sigma _{k=2}^{n}\frac{1}{k}-2(n-1)$. We want to write $\Sigma^{n}_{k=2}\frac{1}{k}$ starting from $k=1$ so that it is a harmonic number thus $\Sigma_{k=2}^n\frac{1}{k}=\Sigma_{k=1}^n\frac{1}{k}-1$. Thus when we substitute it in we get $(2n-2)\Sigma_{k=1}^n \frac{1}{k} -4n$ which works out to mean that $E[X]=2n\text{ln}(n)+\Theta(n)$ 


# Chapter 3: Moments and Deviations
This chapter introduces Markov's inequality, Chebyshev's inequality, what a moment of a random variable is $E[X^n]$ and what variance is. These let us get bounds on the chance of something or greater happening 
## Randomized Median Algorithm 
This algorithm finds the median of some array of $n$ elements $S$ and returns the median of it. It works by finding two elements in the array $d,u$ such that the median $m$ is between then and there is not many elements between them(specifically $o(n/\text{log}\,n)$). 
The size allows us to run a standard sorting algorithm with a time complexity of $O(n\, \text{log}\,n)$ and still have the algorithm complete in linear time. This works out to be linear time complexity by setting $n=\frac{m}{\text{log}\,m}$ which makes the complexity $O(\frac{m}{\text{log}\,m} \text{log}\,(\frac{m}{\text{log}\,m}))=O(\frac{m}{\text{log}\,m}(\text{log}\,m - \text{log}\,\text{log}(m)))=O(m-\frac{m\text{log(}\text{log}\,m)}{\text{log}\,m})=O(m-m\frac{\text{log(}\text{log}\,m)}{\text{log}\,m})=O(m)$ Note that $\frac{\text{log(}\text{log}\,m)}{\text{log}\,m}$ is less than $1$ 

So now instead of finding the median we just need to have an algorithm which finds $d$ and $u$. We sample with replacement $\lceil n^{\frac{3}{4}}\rceil$ elements and call this set $R$. We then sort $R$ and select the $\lfloor n^{\frac{3}{4}}/2-\sqrt{n}\rfloor$th element as $d$ and the $\lfloor n^{\frac{3}{4}}/2+\sqrt{n}\rfloor$th element as $u$. When then take all the elements of $S$ and place then in the following sets $l_d=\{x\in S| x\leq d\}$, $C = \{x\in S| d\leq x \leq u\}$ and  $l_c = \{x\in S| u\leq x\}$. If $|l_c| \geq n/2$ or $|l_d| \geq n/2$ FAIL the attempt(This ensures the median is within $C$), additionally if $|C|\geq 4n^{\frac{3}{4}}$ then FAIL the attempt(This ensures that $C$ is sufficiently small). Sort the $C$ and output the $\lfloor\frac{n}{2}\rfloor - l_d +1$ element. 

We know that this will return the incorrect median, only if the median is not in $C$. But we would catch this case if $|l_c| \geq n/2$ or $|l_d| \geq n/2$. Thus if the algorithm returns a value then it is the median.

Thus because the algorithm is always correct when it does not fail. We just need to make a statement about the probability of failure. We see that failure is equivalent to these three events 
1. $\mathcal{E}_1: |\{r\in R |r\leq m\}|< \frac{1}{2}n^{3/4}-\sqrt{n}$ 
2. $\mathcal{E}_2: |\{r\in R |r\geq m\}|< \frac{1}{2}n^{3/4}-\sqrt{n}$ 
3. $\mathcal{E}_3:|C|>4n^{3/4}$
We know that $\mathcal{E}_1$ is equivalent to $|l_c|\geq n/2$ because of the following proof. 
$\mathcal{E}_1 \rightarrow |l_c|\geq n/2$
$\mathcal{E}_1$ means that $d>m$ thus $|l_c|\geq n/2$ by definition of median
$|l_c|\geq n/2  \rightarrow \mathcal{E}_1$
If $|l_c|\geq n/2$ then $d>m$ which since we sampled $\lceil n^{\frac{3}{4}}\rceil$ elements and $d$ is the $\lfloor n^{\frac{3}{4}}/2-\sqrt{n}\rfloor$ element there are at least $\lfloor n^{\frac{3}{4}}/2-\sqrt{n}\rfloor$ elements greater than it. Which implies $\mathcal{E}_1$

Now that we need to find $P(\mathcal{E}_1 \cup \mathcal{E}_2 \cup \mathcal{E}_3)$. 
Finding $\mathcal{E}_1$ and $\mathcal{E}_2$  
Let $Y$ be a random variable representing the number of elements in $R$ such that $r\leq m$. We can express $Y$ as a sum of indicator variables for each sample because we are sampling with replacement. $X_i=1$ if the $i$th selected element is less than $m$. $P(X_i=1)=\frac{(n-1)/2+1}{n}=\frac{1}{2}+\frac{1}{2n}$ because there are $n$ elements and the $(n-1)/2+1$ of them are less than the median. Thus we can easily because $Y\sim \text{binom}(n^{3/4},\frac{1}{2}+\frac{1}{2n})$ we find that $\text{Var}(Y)=n^{3/4}(1+\frac{1}{2n})(1-\frac{1}{2n})<\frac{1}{4}n^{3/4}$, and $E(Y)=\frac{1}{2}n^{3/4}+\frac{1}{2n^{1/4}}$
Thus $P(\mathcal{E}_1)=P(Y=\Sigma_{i=1}^{n^{3/4}}X_i<\frac{1}{2}n^{3/4}-\sqrt{n})$. Because $\frac{1}{2n^{1/4}}$ is so small we say that $E(Y)\approx\frac{1}{2}n^{3/4}$. Thus by Chebyshevs we see that $P(Y<\frac{1}{2}n^{3/4}-\sqrt{n})\leq P(|Y_1-E[Y]|>\sqrt{n})\leq \frac{\text{Var}(Y)}{n}<\frac{\frac{1}{4}n^{3/4}}{n}=\frac{1}{4n^{1/4}}$  
Finding $\mathcal{E}_3$
At least one of the two sub-events occur if $|C|>4n^{3/4}$ 
$\mathcal{E_{3,1}}:$ $2n^{3/4}$ elements are greater than $m$
$\mathcal{E_{3,2}}:$ $2n^{3/4}$ elements are less than $m$
Think about if it was evenly split both would need to happen and any shift still results in one of them still being true. We can treat these two different events using symmetry
Assume there are at least $2n^{3/4}$ elements in $C$ greater than $m$. Thus $u$ placed in the sorted order is $\frac{1}{2}n+2n^{3/4}$ in the set $S$(we know that $m$ is at position $\frac{1}{2}n$) and we know $R$ has at least $\frac{1}{2}n^{3/4}-\sqrt{n}$ samples(because $u$ is the $\frac{1}{2}n^{3/4}+\sqrt{n}\,$th element of $R$ and there are $n^{3/4}$ elements in $R$) from the elements of $S$ greater than or equal to $\frac{1}{2}n+2n^{3/4}\,$th element. 

Next we define $X$ such that $X=\Sigma^{n^{3/4}}_{i=1}X_i$ where $X_i=1$ if the $i$th sample of $R$ is greater than the $\frac{1}{2}n+2n^{3/4}\,$th largest element of $S$. We see that the $P(X_i=1)=\frac{1}{2}-2n^{-1/4}$ and there are $n^{3/4}$ elements and this is a binomial random variable thus $E[X]=\frac{1}{2}n^{3/4}-2n^{1/2}$ and $\text{Var}[X]=n^{3/4}(\frac{1}{2}-2n^{-1/4})(\frac{1}{2}+2n^{-1/4})\leq \frac{1}{4}n^{3/4}$  

Note that $P(\mathcal{E_{3,1}})=P(X\geq \frac{1}{2}n^{3/4}-\sqrt{n})\leq P(X-E[X]\geq \sqrt{n})\leq\frac{Var(X)}{n}\leq\frac{\frac{1}{4}n^{3/4}}{n}=\frac{1}{4}n^{-1/4}$. By symmetry  $P(\mathcal{E_{3,2}})\leq \frac{1}{4}n^{-1/4}$. 
Thus by union bound $P(\mathcal{E}_1 \cup \mathcal{E}_2 \cup \mathcal{E}_3)\leq \frac{1}{4}n^{-1/4}+\frac{1}{4}n^{-1/4}+\frac{1}{2}n^{-1/4}=n^{-1/4}$ 


# Chapter 4: Chernoff Bounds
While Markov's inequality and Chebyshev inequality are nice, they decay only linearly with respect to $n$. Instead by using Chernoff Bounds we can get the probability of a rare event to decay exponentially with $n$. Because I have explained Chernoff bounds in my notes I will not explain them here 
## Set Balancing Algorithm
The set balancing algorithm is used whenever you wanna minimize the difference between two allocations of elements in sets. For example given a set of weights you might want to try and create an even split of the weights among two cars. 
Sometimes we might want to balance multiple different attributes at the same time so we encode this problem as a matrix(Additionally we restrict ourselves to a matrix with entries from the set $\{0,1\}$). So for our problem we have a $n\times m$ matrix $A$ with entries $\{0,1\}$ and we trying to find a $n$ dimensional vector $b$ with entries $\{-1,1\}$ that minimizes $||Ab||_{\infty}=\text{max}_{i=1,...,n}|c_i|$.
We will show that the by selecting a random vector $b$ with uniform entries $P(||Ab||_{\infty}\geq \sqrt{4m\,\text{ln}\,n})\leq \frac{2}{n}$ 
We show this by considering the $i$th row $a_i=a_{i,1}+a_{i,2}+...+a_{i,n}$. Let $k$ be the number of $1$'s in the row. If $k\leq \sqrt{4m\,\text{ln}\,n}$, then clearly $|a_i\cdot b|=|c_i|\leq \sqrt{4m\,\text{ln}\,n}$ because $b$ only has entries that are $1$ and $-1$. 
If $k\geq \sqrt{4m\text{ ln }n}$ then we know that $Z_i=\Sigma_{j=1}^m a_{i,j}b_i$ is a random variable that is the sum of $k$ independent random variables with the values $1,-1$ we can use the Chernoff bound defined below. 

Let $X=\Sigma_{i=1}^n X_i$ where $P(X_i=-1)=P(X_i=1)=\frac{1}{2}$. Thus the moment generating function of $X_i$ is $\frac{1}{2}e^t+\frac{1}{2}e^{-t}$. If we do the Taylor expansion of $e^t$ we see that $e^t=1+t+\frac{t^2}{2!}+...+\frac{t^i}{i!}$ and if we do the taylor expansion of $e^{-t}=1-t+\frac{t^2}{2!}+...+(-1)^i\frac{t^i}{i!}$. Thus $\frac{1}{2}e^{-t}+\frac{1}{2}e^{t}=\Sigma \frac{t^{2i}}{(2i)!}\leq \Sigma \frac{(t^2/2)^i}{i!}=e^{t^2/2}$ 
Thus using the Chernoff bound we see that $P(X\geq a)=P(e^{Xt}\geq e^{ta})\leq e^{t^2n/2}-ta$ setting $t=a/n$ we get $P(X\geq a)\leq e^{-a^2/2n}$  and by symmetry $P(X\leq a)\leq e^{-a^2/2n}$ which by union bound means $P(|X|\geq a)\leq 2e^{-a^2/2n}$ 

Now we can show that $P(|Z_i|\leq \sqrt{4m\text{ ln }n})\leq2e^{4m\text{ ln }n/2k}\leq \frac{2}{n^2}$ and by union bound since there are $n$ columns we get the bound failing for $n$ columns to be $\frac{2}{n}$  

I still don't really understand the application or significance of this yet



## Network Routing on a Hypercube Graph
Network routing is where you have a set of processors(Nodes of the graph) which have data packets that they need to send to other nodes. These nodes are connected to each other using directed edges. Each edge can only pass one data packet through it at a given moment(and each packet can only pass through a single edge per time step), and each edge has a stack(it can store packets in a queue but only send one packet). 

One thing you can measure is for a given routing permutation(a situation where every node sends and receives a single packet) how quickly you can generate a route, and how efficient the generated route is. Routing permutations can nicely be represented by scrambling the string "123...n".

One of the specific graphs that we are going to analyze is a hypercube. A $N$-degree hypercube has $2^{N}$ nodes. Each node is numbered $1,...2^N$ and two nodes are considered connected if their binary representation differs by a single bit IE $4$ and $5$ are connected in a hypercube graph because $100$ and $101$ differ by a single bit. Because each node can differ by a single bit and there are $n$ ways that a bit string of length $n$ can differ,  each node has $n$ edges or $2n$ edges if it is a directed graph. Finally the furthest that two nodes can be from each other is $n$ edges apart(every single bit is different)

Because of the nature of our hypercube graph, we can send a packet between two nodes using bit-fixing routing. An example would be sending $000$ to $111$ would follow the following route. $000\rightarrow 100\rightarrow 110 \rightarrow 111$ 

Our actual algorithm works in two phases, phase $1$ where all the packets are routed to a random node, and then phase $2$ where all those packets are finally routed to their destination. We are going to show that the algorithm is $O(\text{Log}\,N)$  with probability $1-O(N^{-1})$. Alternatively since the number of nodes is $2^{N}$ the number of time steps scales linearly with the number of nodes in the network(but you can't pick a specific number of nodes to add because you are restricted to a hyper-cube). Due to the simplicity of the bit-fixing routing, its easy to show that the computation of the route also scales linearly with the number of nodes in the graph. 

In order to analyze phase $1$ we need to calculate the greatest time until some packet $M$ reaches its destination. We denote the random variable that represents the time it takes for a given packet $M$ completes phase $1$ as $T_1(M)$. Note that packet $M$ is either moving through edges or waiting until the edge it needs to use is free. If the path for the packet $M$ is $P=(e_1,e_2,...,e_m)$ and the amount of packets that pass though $e_1$ is denoted as $X_1(e_1)$ then we have the upper bound $T_1(M)\leq \Sigma_{x=1}^m X_1(e_i)$(because worst case the packet has to wait for every single other packet going through every edge on its path). 

The probability that phase $1$ takes longer than $T$ is the probability that there exists some path $P=\Sigma_{x=1}^m X_1(e_i)$ such that $T_1(P)\geq T$. It is incredibly difficult to make assertions about $\Sigma^{m}_{x=1}X_1(e_i)$ because they are not independent. But instead we can make assertions about the number of packets that exist on the nodes that $P$ will utilize that have a possibility of routing through the edges $P$ uses. 

These packets are known as active packets. To specify a packet is active on path $P$ if it reaches node $v_{i-1}$  and $v_{i}$ differ by a single a single bit, which has not been fixed by the bit fixing routing algorithm yet. $v_{i-1}$ and $v_i$ are on path $P$

If we consider a node $v_{i-1}=(b_1,b_2,...,b_{j-1},a_j,a_{j+1},...,a_n)$ and node $v_i=(b_1,b_2,...,b_{j-1},b_j,a_{j+1},...,a_n)$ that differ by the $j\,$th bit 
then only packets originating from $(*,*,...,*,a_j,a_{j+1},...,a_n)$ will get routed to node $v_{i-1}$(This is because if one of the later bits differs, that bit won't change until after the $j$ so it won't route through that). In the same way packets that are being sent have to have an address of $(b_1,b_2,...,b_{j-1},*,...,*)$(because otherwise it will adjust itself to not end up mapping to the node $v_{i-1}$). 
Thus because of the restriction of where they originate there are $2^{j-1}$ possible active packets, and because of the restriction of where they are being sent each one has a $\frac{1}{2^{(j-1)}}$ chance of actually being an active packet. Thus the expected number of packets along a given route is $m$ which is less than $n$. We denote the number of active packets on a path using the random variable $H$

Then we can use a chernoff bound and found earlier in the text to prove that $P(H\geq 6n \geq 6E[H])\leq 2^{-6n}$ 

Now we want to show $P(T_1(P)\geq 30n)\leq P(H\geq 6n)+P(T_1(P)\geq 30n|H< 6n)$. This inequality is from $P(A)\leq P(B)+P(A|\bar{B})$ which is derived from dropping terms from $P(A|B)P(B)+P(A|\bar{B})P(\bar{B})$. We want to do this because we want to show that $P(T_1(P)\geq 30n)$ is less than $2^{-3n}$ because then we can use the union bound of the $2^{2n}$ possible paths 

Since we proved that $P(H\geq 6)\leq 2^{-6n}$ we just need to show that $P(T_1(P)\geq 30n|H< 6n)\leq 2^{-3n-1}$ because then our union bound works  

It is important to note that if a packet leaves the path it can't ever get back on again because it differs by at least a single bit until the end and nothing will change that. Additionally note that the probability of an active packet saying on the path when it transitions to the next node $\frac{1}{2}$ because the bits have to differ. The chance of $6n$ active packets transitioning more then $30n$ times is less than the probability given $36n$ coins getting less than $6n$. This makes sense if you think of each packet having a chance of transitioning as a coin flip, with a success being the packet leaving the path and each failure representing traversing an edge. But once there are more than $6n$ success there will be no more active packets because they have all transitioned off. Thus letting $Z$ be the number of successes in $36n$ coin flips
We see that $P(T_1(P)\geq 30n|H\leq 6n)\leq P(Z\leq 6n)\leq e^{-18(2/3)^2/2}=e^{-4n}\leq2^{-3n-1}$ 

Thus $P(T_1(P)\geq 30n)\leq P(H\geq 6n)+P(T_1(P)\geq 30n|H\leq 6n)\leq 2^{-3n}$ and since there are $2^{2n}$ possible paths, by union bound $P(T\geq 30n)\leq 2^{-n}$ or because $\text{log}_2\,n=N$ it has $O(N^{-1})$ 

The second phase is just running the first phase in reverse, since we are at a random location and now going to a deterministic location. Thus the probability that no packet spends more than $30n$ time steps getting to their location has probability $1-O(N^{-1})$.

Thus our algorithm takes less than $60n$ steps with probability $1-O(N^{-1})$. Note since there is $2nN$ directed edges in the graph and we are routing $N$ packets at most at any given moment only $\frac{1}{2}n$ edges are being used

## Network Routing on a Butterfly Graph
Choosing to ignore for now 


# Chapter 5: Balls, Bins, Random Graphs, Poisson Approximation
## Approximating the birthday paradox
The birthday paradox is not actually a paradox. It is the problem where you have $n$ elements and $m$ categories. The elements are uniformly distributed across all the categories. We are concerned about the probability that two elements share a category. To calculate this we can more easily calculate the probability that no two elements share a category which is the following number
$$
\Pi_{j=1}^{m}(1-\frac{j}{n})
$$
Since the taylor approximation of $e^x=1-x$ we can approximate $1-\frac{j}{n}$ as $e^{\frac{j}{n}}$ so we can approximate this as 
$$
\Pi_{j=1}^{m}e^\frac{j}{n}
$$
which is way way faster to calculate. 
We can get a upper bound on the probability of a collision by considering the event $E_i$ where the $i\text{th}$ person not matching any of the previous people. Thus
$$
P(E_1,E_2,...,E_k)\leq\Sigma_{i=1}^{k}P(E_i)\leq \Sigma_{i=1}^{k}\frac{i-1}{n}=\frac{k(k-1)}{2n}
$$
This is true using a union bound, assumption that no prior people matched, then an application of gauss's sum. From this we can see that if there is less than $\sqrt{n}$ people that then there is at least a $\frac{1}{2}$ probability that all birthdays are distinct. 
If we assume the that the first $\sqrt{n}$ people have distinct birthdays then the probability the next $\sqrt{n}$ people are distinct is 
$$
(1-\frac{1}{\sqrt{n}})^{\sqrt{n}}\leq\frac{1}{e}
$$
Thus the probability of $2\sqrt{n}$ people all having distinct birthdays is at most $\frac{1}{e}$  

## Maximum Load on Balls and Bins  
Often algorithms want to understand based off uniformly distributed items, what is the the behavior once they are placed in bins. This can be used in load balancing for distributed computing, memory allocation and resource management. We can currently prove that the maximum load in balls is less than $3\ln(n)/\ln(\ln(n))$ and more than $\ln(n)/\ln(\ln(n))$ with probability $1-\frac{1}{n}$

### Upper bound on maximum load
In this problem we prove that if we throw $n$ balls into $n$ bins, the chance of any bin having more than $3\ln(n)/\ln(\ln(n))$ is less than $\frac{1}{n}$

We can easily see that the probability of a specific bin having $j$ balls when there are $m$ balls and $n$ bins is at most 
$$
\binom{n}{j}(\frac{1}{n})^j
$$
This is calculated using a union bound and counting the number of ways there can be $j$ balls from $n$ balls. We see that the following inequality is true because $\frac{n!}{(n-j)!n^j}\leq 1$
$$
\binom{n}{j}(\frac{1}{n})^j=\frac{n!}{j!(n-j)!\,n^j}=\frac{1}{j!}\frac{n!}{(n-j)!n^j}\leq \frac{1}{j!}
$$
Further we see since $\frac{k^k}{k!}\leq\Sigma_{i=0}^k\frac{k^i}{i!}=e^{k}$(The inequality is true because $\frac{k^k}{k!}$ is an element of the sum, the equality is true because its the taylor expansion of $e^k$). We can rearrange this to get $\frac{1}{k!}\leq(\frac{e}{k})^k$. Thus we get the statement
$$
\binom{n}{j}(\frac{1}{n})^j\leq \frac{1}{j!} \leq (\frac{e}{k})^k
$$
Using this upper bound and a union bound on the $n$ boxes, for $j\geq 3\ln(n)/\ln(\ln(n))$ that the probability any bin has at least $j$ balls is less than $\frac{1}{n}$ 
$$
n(\frac{e}{j})^{j}\leq (\frac{e\ln(\ln(n))}{3\ln(n)})^{3\ln(n)/\ln(\ln(n))}
$$
Above is true because $j$ is at least $3\ln(n)/\ln(\ln(n))$ by definition we then remove $\frac{e}{3}$ which creates another bound because it is greater than one giving us 
$$
(\frac{e\ln(\ln(n))}{3\ln(n)})^{3\ln(n)/\ln(\ln(n))}\leq\frac{\ln(\ln(n))}{\ln(n)})^{3\ln(n)/\ln(\ln(n))}
$$
which then we rewrite by doing $e^{\ln()}$ which gives us 
$$
e^{-2\ln(n)+3(\ln(n))(\ln(\ln(\ln(n))))/\ln(\ln(n))}
$$
Which is less than $\frac{1}{n}$ so we have proven what is desired
### Lower Bound on maximum load
When we throw $n$ balls independently and uniformly at random into $n$ bins the maximum load is at least $\ln(n)/\ln\ln(n)$ with probability $1-\frac{1}{n}$

We can see that the probability a specific bin has load $M=\ln n/\ln \ln n$ is at least $1/eM!$. In the Poisson case the bins are independent, so the probability that no bin has load $M$ is at most $1-(\frac{1}{eM!})^n$ which is less than $e^{-n/(eM!)}$.
Now we need to prove that $e^{-n/(eM!)}\leq n^{-2}$ because if we prove that we can use a Poisson approximation we can multiply it by $e\sqrt{n}$ and see that $e\sqrt{n}n^{-2}$ is less than $\frac{1}{n}$. 
We can prove this is true by showing $M!\leq n/2e\ln(n)$ or equivalently $\ln(M!)\leq \ln(n)-\ln(2e)-\ln(\ln(n))$. 

We proved below that $M!\leq e\sqrt{M}(\frac{M}{e})^M$ which can be extended to be $M!\leq M(\frac{M}{e})^M$. Thus we have 
$$
\ln(M!)\leq \ln(M)+M\ln(M)-M
$$
which we then replace $M$ with $\ln n/\ln \ln n$ which then a ton of algebra works out to be $\leq \ln(n)-\ln(\ln(n))-\ln(2e)$ proving our conjecture

## Bucket Sort
Bucket sort is a sorting algorithm with expected time complexity of $\Omega(n)$. It works under the assumption that we have $n=2^m$ elements uniformly distributed on the interval $[0,2^k)$ where $m\leq k$.
In the first phase we place the elements into $n$ buckets, we place the each element into the $j$th bin if its first binary digits match with if the first $m$ digits in the binary representation. 
IE if $n=2^{10}$ bucket $3$ contains all of the elements with the starting bits $0000000011$. This means that if a element is in a bucket greater than another elements bucket, then it is greater than it. We can place the elements into the correct buckets with linear time. 

Note that since that since the elements are uniformly distributed, the distribution of the number of elements in a single bucket is $\text{bin}(n,\frac{1}{n})$. We then sort the elements within each bucket with some sorting algorithm(with time complexity less than $n^2$). The expected time of sorting all of these algorithms is $E[\Sigma_{i=1}^{n} c X_i^2]=cE[\Sigma_{i=1}^{n} X_i^2]=cE[\Sigma_{i=1}^{n} X_1^2]=cnE[ X_1^2]$. We can actually calculate $E[ X_1^2]=\frac{n(n-1)}{n^2}+1=2-\frac{1}{n}\leq 2$.  Thus the expected time complexity of this algorithm scales linearly. 

I am pretty sure that you can get this to work with any distribution by using the universality of the uniform. 

## Poisson Approximation 
Because of the difficulty with calculating the values for binomials variables with large number of trial. IE if $X\sim\text{Bin}(4000,p)$ and we want to calculate $P(X=1256)=\binom{4000}{1256}(1-p)^{2744}p^{1256}$ which can be incredibly computationally intensive. But you might notice that for large $n$ and small $p$ that the distribution of $X$ is roughly the Poisson random variable.
To formalize this if we throw $m$ balls into $n$ bins, and denote the number of balls in the $n$th bin as $X_i^{m}$. Additionally let $Y_i^{m}$ be Poisson random variables with $\mu = \frac{m}{n}$. 

First we show that $(Y_1^{m},...,Y_n^{m})|\Sigma_{i=1}^{n}Y_i^{m}=k \sim (X_1^{m},...,X_n^{m})$
We can show that $(Y_1^{m},...,Y_n^{m})|\Sigma_{i=1}^{n}Y_i^{m}=k$ has the same distribution as $(X_1^{m},...,X_n^{m})$
Here is the proof
$P((X_1^{(k)},...,X_n^{(k)})=k_1,k_2,...,k_n)$ where $\Sigma_{i=1}^{k}X_i=k$ equals $\frac{k!}{(k_1!)(k_2!)...(k_n!)}n^k$   just by counting. 
Now we want to find the probability that $P\left((Y_1^{k},...,Y_n^{k})=(k_1,...,k_n)| \Sigma_{i=1}^{k}Y_i=k\right)$ which we can write as $\frac{P((Y_1^{m}=k_1)\cap (Y_2^{m}=k_2)\cap ...\cap (Y_n^{m}=k_n))}{P(\Sigma_{i=1}^{k}Y_i=k)}$ which because the $Y_i$'s are independent(in this case not in generate) and because the sum of Poisson random variables is a poison random variable we can rewrite the previous statement as $\frac{\Pi e^{-m/n}(m/n)^k_i/k_i}{e^{-m}m^k/k!}$ which by properties of exponents simplifies to $\frac{k!}{(k_1!)(k_2!)...(k_n!)}n^k$

Then using that we are able to prove that $E[f(X^{m}_1,...,X^{m}_1)]\leq e\sqrt{m}E[f(Y^{m}_1,...,Y^{m}_n)]$. This initially seemed useless but actually provides a massive amount of utility when you consider indicator functions. If you have a function when that returns one when $X_1^{m}=a$ and returns zero otherwise, we have $[f(X^{m}_1,...,X^{m}_1)]=P(X_1^{m}=a)$. We can do this for all events, thus if we prove this we prove that the Poisson version of the event times $e\sqrt{m}$ is the upper bound on the probability of it in the binomial case

 By the LOTE $E[f(Y^{m}_1,...,Y^{m}_n)]=\Sigma_{k=0}^{\infty} E[f(Y^{m}_1,...,Y^{m}_n)|\Sigma_{i=1}^{k}Y_i=k]P(\Sigma_{i=1}^{k}Y_i=k)$ which we can drop all the other terms in that sum and get $\Sigma_{k=0}^{\infty} E[f(Y^{m}_1,...,Y^{m}_n)|\Sigma_{i=1}^{k}Y_i=k]P(\Sigma_{i=1}^{k}Y_i=k)\leq E[f(Y^{m}_1,...,Y^{m}_n)|\Sigma_{i=1}^{k}Y_i=m]P(\Sigma_{i=1}^{k}Y_i=m)$ Which we know from proving $(Y_1^{m},...,Y_n^{m})|\Sigma_{i=1}^{n}Y_i^{m}=k \sim (X_1^{m},...,X_n^{m})$ that $E[f(Y^{m}_1,...,Y^{m}_n)|\Sigma_{i=1}^{k}Y_i=m]=E[f(X^{m}_1,...,X^{m}_1)]$. 

Thus we know that $E[f(Y^{m}_1,...,Y^{m}_n)]\leq E[f(X^{m}_1,...,X^{m}_1)] P(\Sigma_{i=1}^{k}Y_i=m)$ which since the sum of Poisson random variables is a Poisson random variable we can calculate $P(\Sigma_{i=1}^{k}Y_i=m)=\frac{m^me^{-m}}{m!}$. But we can place a better bound on this using the property that $m!\leq e\sqrt{m}(\frac{n}{e})^m$ which is proved at the bottom of my notes. So now we have proven that $E[f(Y^{m}_1,...,Y^{m}_n)]\leq E[f(X^{m}_1,...,X^{m}_1)]\frac{1}{e\sqrt{m}}$ thus we can now do Poisson approximations!
### Special Case of Poisson Approximation
If you have some function $f$ that is non-negative such that $E(f((X^{m}_1,...,X^{m}_1)))$ is monotonically increasing or decreasing with respect to $m$ then we know that $E(f(X^{m}_1,...,X^{m}_1))\leq 2 E[f(Y^{m}_1,...,Y^{m}_n)]$. 
An example of this would be the number of empty bins. As you increase the number of bins the expected number of empty bins decreases monotonically.
Thus to calculate the probability that given $n$ bins and $m$ balls, we first change the probability of a bin being empty from being the probability $(1-\frac{1}{n})^m$ that is highly dependent on the values of the other bins to $\lambda = ne^{-m/n}$ that is independent. Then we calculate the probability of $k$ bins being empty in the Poisson case as $ne^{-m/n}$ which then we can get an upper bound in the binomial case by calculating $2ne^{-m/n}$

## Bloom Filters
The purpose of a bloom filter is to speed up the time it takes to determine wether an item is in some form of storage data structure. Examples could be linked lists or hash-maps. It can only confirm that an item isn't in the structure, not that an item is in the structure. 

A bloom filter is an array of $n$ bits which we will denote $A[0]$ to $A[n-1]$. We have $k$ independent hash functions which we assume are uniformly distributed denoted as $h_1,...,h_k$ which map to $\{0,...,n-1\}$. Additionally we have some set of elements $S=\{s_1,...,s_m\}$.
Every time we add some element to our structure we hash it with every hash function. And set the bits $A[h_i(s_j)]=1$. Now if we want to determine wether something is stored within the structure we has the element and see if the bits it hashes to have been flipped. If all the bits have been flipped then then actually search the array, but if a single bit hasn't been flipped then we know its not in our structure.

We can calculate the probability that a specific bit is still $0$ after we have appended all of the items as. We using the approximation that $1+x=e^{x}$ 
$$
\left(1-\frac{1}{n}\right)^{km}\approx e^{-km/n}
$$
So the probability of a false positive when we query the array is the probability of no bits are $0$
$$
(1-(1-\frac{1}{n})^{km})^k=(1-e^{-km/n})^{k}=(1-p)
$$
Now given a specific number of bits $n$ and specific number of elements $m$ we want to find the number hash functions $k$ which minimizes the probability of a false positive. To make it easier we are minimizing the natural log of it, meaning the function is $g=k\ln(1-e^{-km/n})$.
$$
\frac{dg}{dk}=\ln(1-e^{-km/n})+\frac{km}{n}(\frac{e^{-km/n}}{1-e^{-km/n}})
$$
which we can find(though a bunch of annoying algebra) has a global minimum at $k=\ln(2)(n/m)$. But we obviously have to have a integer number of hash functions.  

# Useful Approximations and Bounds
These are a few properties which are used repeatedly which are incredibly useful 
### $1+x\approx e^{x}$
This holds when $x$ is small. We can easily see this from the Taylor approximation of $e^x=1+x+\frac{x^2}{2!}+...+\frac{x^n}{n!}$ and when $x$ is small parts $\frac{x^2}{2!}+...+\frac{x^n}{n!}$ become incredibly small
### $H(n)=\Sigma_{i=1}^n \frac{1}{i}=\ln(n)+\Theta(1)$
We prove this by showing that $\ln(n)+c_1 \leq H(n)$ and that $\ln(n)+c_2 \geq H(n)$. We know that $\ln(n)=\int_{x=1}^{\infty}\frac{1}{x}dx$ which since $\ln(n)$ is monotonic $\int_{x=1}^{\infty}\frac{1}{x}dx\leq \Sigma_{i=1}^n \frac{1}{i}$ because $\Sigma_{i=1}^n \frac{1}{i}$ is the left Riemann sum and $\int_{x=1}^{\infty}\frac{1}{x}dx\geq \Sigma_{i=2}^n \frac{1}{i}$ because $\Sigma_{i=2}^n \frac{1}{i}$ is the right Riemann sum. Thus since it is less than $\ln(n)$ by a constant and more than by a constant our error term is $\Theta(1)$
### $n!\leq e\sqrt{n}(\frac{n}{e})^n$ 
The first useful property we have to prove this is $\ln(n!)=\Sigma_{i=1}^n\ln(i)$. Thus just comes from the way multiplication and $\ln()$ interact. 
Next since $\ln()$ is a concave we have the property that $\int^{i}_{i-1}\ln(x)dx\geq \frac{\ln(i-1)-\ln(i)}{2}$. This it easy to see when you imagine drawing a line and then integrating the rectangle in the middle. 
Next we can take $\int_1^{n}\ln(x)dx=\Sigma_{i=1}^{n} \int_{i-1}^{i}\ln(x)dx\geq \Sigma_{i=1}^n \frac{\ln(i-1)-\ln(i)}{2}=\Sigma_{i=1}^n\ln(i)+\frac{\ln(n)}{2}$ 
So we can rewrite $\int_1^{n}\ln(x)dx\geq \Sigma_{i=1}^n\ln(i)+\frac{\ln(n)}{2}$ as $n\ln(n)-n+1\geq \ln(n!)-\frac{\ln(n)}{2}$ using the integral of $\int_1^{n}\ln(x)dx$ and our previously proven property.