---
tags:
---
#domain 
This is the study of how utilizing probability can lead to computational advantages
# Chapter 1: Introduction to Probability 
In this chapter they introduce basic concepts like the axioms of probability, bayes rule and LOTP. I don't feel the need to go into detail 
## Types of Randomized Algorithms
There are two types of randomized algorithms, Monte Carlo algorithms and Las Vegas algorithms. 
Monte Carlo algorithms have a deterministic time complexity, but a non-deterministic outcome. Examples include Monte-Carlo integration which gives a different result back every time but takes a set amount of time. 
On the other hand there are Las Vegas Algorithms, which have non-deterministic time complexity but deterministic outcomes. They often on average are faster than deterministic algorithms but there is no guarantee that they will be. An example would be randomized quick-sort. 

## O notation
Given a function $g$ and $f$ we would say that $f(x)$ is $O(g(x))$ if $|\frac{f(x)}{g(x)}|\leq M$ for all $x\geq x_0$. Intuitively this means that $f(x)$ grows at either a slower or equal rate to $g(x)$. Consequently this means that $\lim_{x\rightarrow \infty}\frac{f(x)}{g(x)}$ either converges to a finite number(IE $\frac{3x^2+5x}{x^2}$), converges to zero(IE $\frac{100}{x}$) or oscillates under some bound(IE $\frac{3x\sin{x}}{x}$. 
In the case where $\lim_{x\rightarrow \infty}\frac{f(x)}{g(x)}\leq \epsilon$ for all $\epsilon\geq 0$ then we say that $f(x)=o(g(x))$  
## Omega notation
This is kinda the opposite of the big O notation. A function $f(x)$ is considered to have $\Omega(g(x))$ if $\lim_{x\rightarrow\infty}|\frac{f(x)}{g(x)}|$ does not converge. Also a function $f(x)=\omega(g(x))$ if $\lim_{x\rightarrow\infty}|\frac{f(x)}{g(x)}|$ diverges 

## Theta Notation 
A function is considered to be $f(x)=\Theta(g(x))$ if and only if $f(x)=O(g(x))$ and $f(x)=\Omega(g(x))$. This means that $\lim_{x\rightarrow\infty}|\frac{f(x)}{g(x)}|$ is some finite number.  



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
NEED TO FINISH


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
(1-(1-\frac{1}{n})^{km})^k\approx(1-e^{-km/n})^{k}
$$
Now given a specific number of bits $n$ and specific number of elements $m$ we want to find the number hash functions $k$ which minimizes the probability of a false positive. To make it easier we are minimizing the natural log of it, meaning the function is 
$$g=k\ln(1-e^{-km/n})$$
$$
\frac{dg}{dk}=\ln(1-e^{-km/n})+\frac{km}{n}(\frac{e^{-km/n}}{1-e^{-km/n}})
$$
which we can find(though a bunch of annoying algebra) has a global minimum at $k=\ln(2)(n/m)$.But we obviously have to have a integer number of hash functions. 
## Random Graphs
Having the poisson approximation is really nice because it allows us to look at abstract away from a complicated case and look at a simpler case and make statements about that instead. 
It would be useful to have statement like this but for random graphs instead but before that we need to define the two types of random graphs 
We can either define a random graph as between two nodes there is a probability $p$ that there is an edge, or we can define a graph as there are $n$ edges and they are randomly uniformly placed between edges. We denote the first type of random graph as $G(n,p)$ and the second type of random graph as $G(n,N)$. 
You may be able to see the connect between these two similar to way that that balls and bins can be instead approximated with the binomial distribution. 
Some graphs properties are monotonically increasing meaning that if you added an edge to a graph than it would not break the property. An example of this would be a graph containing a degree $n$ cycle, no number of edges you can add will remove this property. There are also monotonically decreasing properties like being cycle free. 
### The relationship between G(n,p) and G(n,N)
We can define a nice relationship between $G(n,p)$ and $G(n,N)$ that is there exists some epsilon $\epsilon$ such that for $p^{+}=(1+\epsilon)N/\binom{N}{2}$ and $p^{-}=(1-\epsilon)N/\binom{N}{2}$ 
$$
P(n,p^-)-e^{-O(n)}\leq P(n,N)\leq P(n,p^{+})+e^{-O(n)}
$$
Where $P$ is the probability of some graph having a monotone increasing trait. This is nice because it allows us to just think about $G(n,p)$ when $n$ gets large.

We can prove this using the following. By the law of total probability $P(n,p^{-})=\Sigma_{k=0}^{\binom{n}{2}}P(n,K)P(X=K)$  where $X$ is a random variable representing the number of edges. Further $P(n,p^{-})=\Sigma_{k\leq N}P(n,K)P(X=K)+\Sigma_{k> N}P(n,K)P(X=K)$
Since we are looking at a monotone increasing function we know that $P(n,K)\leq P(n,N)$ when $K\leq N$ giving us $\Sigma_{k\leq N}P(n,K)P(X=K)\leq P(X\leq N)P(n,N)$. Additionally $\Sigma_{k> N}P(n,K)P(X=K)\leq P(X> N)$. Thus
$$
P(n,p^{-})\leq P(X\leq N)P(n,N)+P(X>N)\leq P(n,N)+P(X>N)
$$ But nicely we can derive a chernoff bound for $P(X>N)\leq e^{-(1+\epsilon)\epsilon^2N/8}$ showing that $P(n,p^{-})-e^{-O(N)}\leq P(n,N)$ we can do a similar argument to show that $P(n,N)\leq P(n,p^{+})+e^{-O(n)}$. 
The significance of this is that with sufficiently large $N$ the graphs $G(n,N)$ behave pretty much like $P(n,p^{-})$ 
### Finding Hamiltonian Cycles
On a graph a hamiltonian cycle is a cycle that includes every single vertex. There are two algorithms included in the text, one which is better but hard to analyze and one which is worse but easier to analyze. 
Both use rotation of a path on a graph which is where you have a path $(v_1,v_2,v_3,...,v_n)$ and some edge $(v_i,v_n)$ we rotate the path with this edge by connecting $v_i$ to $v_n$ in the path and then instead making $v_{i+1}$ the end. So our final path would look like $(v_1,v_2,...,v_i,v_n,v_{n-1},v_{n-2},...v_{i+1})$
#### Algorithm 1
Input: A graph $G=(V,E)$ with $n$ vertices
Output: A hamiltonian cycle or FAIL
1. Pick a random vertex make that the head
2. Repeat steps $3$ through $6$ until you either have a hamiltonian cycle or there are no unused edges in the head node
3. Let $P=v_1,v_2,...,v_k$  be the current path let $(v_k,u)$ be the first edge on the in $v_k$ list
4. Remove $(v_k,u)$ from both $v_k$ and $u$ list
5. If $u\ne v_i$ for $1\leq i\leq k$ AKA meaning that it is not in the path, add $u$ to the path making it $v_{k+1}$ we we rotate we check to see if we have made a full hamiltonian cycle(by counting the number of nodes in the graph) and seeing if it makes a proper cycle 
6. Otherwise rotate along the edge $(v_k,u)$. This sets a new node up as the head so we don't get stuck
#### Algorithm 2
Input: A graph $G=(V,E)$ with $n$ vertices
Output: A hamiltonian cycle or FAIL
1. Start with a random vertex as the head node
2. Keep doing the following with their respective probabilities until you either find a hamiltonian cycle or the list of the edges from the head node is empty NOTE THAT MULTIPLE OF THESE CAN HAPPEN BECAUSE THEY ARE NOT MUTUALLY EXCLUSIVE
With probability $1/n$ reverse the path
With probability $|\text{used edges}(v_k)|/n$ choose a uniformly random used edge from $v_k$ and then rotate the path using it. 
With probability $1-\frac{1}{n}-\frac{|\text{used edges}(v_k)|}{n}$ select the first unused edge from $v_k$ $(v_k,u)$ if $u$ is not in the path make it the head, otherwise rotate using this edge 

#### The property which makes algorithm 2 nice 
Proof that being the head node is uniformly distributed among all nodes, thus $P(v_{t+1}=u)=\frac{1}{n}$ 
The only way the first node $v_1$ can become the head node is by path reversal which happens with probability $\frac{1}{n}$ 
If the node is in the path and the edge between it and the head node has been used. Then the probability that that edge is selected and used is the probability that the second effect happens $|\text{used edges}(v_k)|/n$ times the probability that specific edge is picked which is $\frac{1}{|\text{used edges}(v_k)|}$ which means that $|\text{used edges}(v_k)|/n \frac{1}{|\text{used edges}(v_k)|}=\frac{1}{n}$
If the node is in the path and its edge to the head has not been used then we need the second case to trigger which has probability of $1-\frac{1}{n}-\frac{|\text{used edges}(v_k)|}{n}$ and the probability of this edge being picked is uniform across all not picked nodes making it $\frac{1}{n-|\text{used edges}(v_k)|-1}$ thus the probability of this node becoming the head node is $(1-\frac{1}{n}-\frac{|\text{used edges}(v_k)|}{n})(\frac{1}{n-|\text{used edges}(v_k)|-1})=\frac{1}{n}$
 The same argument can be used if the node is not on the path.

Now because the probability of any node being added to the path is $\frac{1}{n}$ we see that this has the the time complexity of the coupon collector problem meaning it has time complexity of $O(n \text{log}n)$ to make a hamiltonian path and a cycle within $O(n\text{log}n)$

NEED TO FINISH
# Chapter 6: Probabilistic Method
The probabilistic method is a technique where you use the probability axioms to prove the existence of an object with a specific probability. 
## Existence Arguments 
The following are techniques for proving the existence of objects
### Basic Counting Arguments
This is where you define some probability space of objects, and then prove that the probability of a randomly sampled object having a specific property is non-zero. 

#### Complete graphs without monochromatic subgraphs
An example of this is proving a complete graph $k_n$ has no monochromatic complete subgraphs $k_k$ if $\binom{n}{k}2^{-\binom{k}{2}+1}\leq 1$. 

We start by counting the number of $k_k$ subgraphs where are, and for a complete graph with $n$ vertices there is $\binom{n}{k}$, because there are $\binom{n}{k}$ combinations of $k$ vertices. 
We define some arbitrary ordering on these subgraphs and define $A_i$ as the event that the 
$i$th subgraph is monochromatic.
We can easily calculate the probability of that $A_i$ is monochromatic using the fact that all $\binom{k}{2}$edges must be the same color and there are two colors so there is two ways to achieve this. Thus we get $P(A_i)=2^{-\binom{k}{2}+1}$.

Now we want to calculate the probability that all of these subgraphs are monochromatic which we can get an upper bound on using the union bound. $P(\bigcup_{i=1}^{\binom{n}{k}} A_i)\leq \Sigma_{i=1}^{\binom{n}{k}}P(A_i)=\binom{n}{k}2^{-\binom{k}{2}+1}\leq 1$. The last inequality is one of our assumptions. Thus since the probability that all of the subgraphs are monochromatic is less than one, the probability none of them are is greater than zero. 

### Expectation Argument
The expectation argument hinges on the fact that there must be some object greater than or equal to the expected value of a discrete random value(if not then the expected value would be lower), and similarly there must be an object less than or equal to the expected value of a discrete random variable. 
#### Finding a Large Cut
We can prove using this method that every graph with $m$ edges has a cut(a set of edges that will partition the vertices into two disjoint graphs, but all of them need to be removed for it to achieve this) with at least $m/2$ edges
We do this by taking all the vertices in each graph and uniformly assigning them to the sets $A$ and $B$. We define another random variable $X_i$ which equals $1$ if edge $i$ connects a node in $A$ to a node in $B$. 
We can see that $E[X_i]=\frac{1}{2}$ through the simple argument of randomly assign the first node of the edge and the probability it matches is $\frac{1}{2}$. If we let $C(A,B)$ be a random variable representing the value of the cut between $A$ and $B$ we can see that 
$$
E[C(A,B)]=E[\Sigma_i^m X_i]=\Sigma_1^m E[X_i]=m\cdot \frac{1}{2}
$$
Thus we have proven that there is some cut with edges greater than or equal to $m/2$ 

But this just proves the existence of a cut with this property, if we want to create an algorithm from this we need to find the probability $p=P(C(A,B)\geq \frac{m}{2})$.
We know that $\frac{m}{2}=E[C(A,B)]=\Sigma_{i<m/2}iP(C(A,B)=i)+\Sigma_{i\geq m/2}iP(C(A,B)=i)$ 

Note that $\Sigma_{i\geq m/2}iP(C(A,B)=i)\leq pm$ because we know that $i\leq m$ because no cuts can have more than the number of edges, and that the sum of  $\Sigma_{i\geq m/2}P(C(A,B)=i)=p$ by the LOTP. 

Similarly $\Sigma_{i< m/2}iP(C(A,B)=i \leq (1-p)(\frac{m}{2}-1)$ because by LOTP $\Sigma_{i< m/2}P(C(A,B)=(1-p)$ and the max value that $i$ can be without being greater than or equal to $m/2$ is $m/2-1$.

Thus $m/2=\Sigma_{i<m/2}iP(C(A,B)=i)+\Sigma_{i\geq m/2}iP(C(A,B)=i)\leq (1-p)(m/2-1)+pm$ which can be rewritten to be $p\geq \frac{1}{m/2+1}$. 

Finally we can easily test wether a partition of the vertices has value greater than $m/2$ so we have a Las Vegas algorithm with a time complexity of the geometric random variable $\text{Geom}(\frac{1}{m/2+1})$ 

#### Maximum Satisfiability
A satisfiability problem(abbreviated SAT) is a logical expression that is a conjunction of or clauses. An example might be $(x_1 \lor \bar{x_2} \lor x_3)\land(\bar{x_3})\land (x_1 \lor x_2)$. Maximum satisfiability is an algorithm for calculating the maximum number of clauses that can be satisfied in this logical formulation. 
We can prove that at least $m(1-2^{-k})$ clauses can be satisfied where $k$ is the minimum number of variables in a clause and $m$ is the number of clauses in the expression. The probability that a specific clause is satisfied is $1-2^{k_i}$ because its the complement that none of the variables are what they should be. Note that $\Sigma_{i=1}^{m}(1-2^{-k_i})\geq m(1-2^{-k})$ thus we can satisfy at least $\lceil m(1-2^{-k})\rceil$. 
We can turn this into a Las Vegas algorithm using 


### Sample and Modify 
This is where we have some larger structure, and then we create some subset of the structure with a specific property, and then modify that structure to have a specific trait. Often structures are hard to work with but substructures are easy to 
#### Independant Sets
For a graph $(V,E)$ an independent set is a set of vertices which none of them share edges. 

If we have a graph with $m\geq n/2$ edges where $n$ is the number of vertices we can create an algorithm which generates an independent set of size $\frac{n}{2d}$ where $d=2m/n$ meaning it is average degree of an vertex in our graph. 
The algorithm works by letting $d=2m/n$ be the average degree of a vertex in $G$. First you delete each vertex of the graph independently with probability $1-\frac{1}{d}$ and also delete all edges connected to it. Then with all the remaining edges randomly delete one of the vertices attached to it. 

Its really easy to see that what will be returned is a set of independent vertices. Now we are gonna analyze the number of vertices outputted from this algorithm.
Since the probability that a vertex does not get deleted is $\frac{1}{d}$ and there are $n$ edges the expected number of edges that remain is $E[X]=\frac{n}{d}$ 
Now if $Y$ is the number of edges that survive the first step. There are $\frac{nd}{2}$ edges in the graph and an edge survives if only its two adjacent vertices survive. Thus the expected value of the number of edges that survive is $E[Y]=\frac{nd}{2}(\frac{1}{d})^2=\frac{n}{2d}$

Because each edge remaining at the end removes one vertex, our independent set at the end will have expected value $E[X-Y]=\frac{n}{d}-\frac{n}{2d}=\frac{n}{2d}$ 

### Second Moment Method
This is derived pretty much just from chebyshev inequality it states that for any integer valued random variable $P(X=0)\leq \frac{\text{Var}(X)}{E[X]^2}$ 
#### Threshold Behavior on Random Graphs
Threshold behavior is when a slight change in $p$ for a random graph $G(n,p)$ can result in a trait being almost guaranteed or not likely at all. 
An example of this would be the existence of a clique of size $4$ within a random graph. When a random graph has probability $o(n^{-2/3})$ then the probability that there is a clique of size $4$ is almost zero, while if it has probability $\omega(n^{-2/3})$ it is almost guaranteed that the graph has a clique of size $4$

Proof that cliques disappear when the probability is $o(n^{-2/3})$ 
Note that $E[X]=\binom{n}{4}p^6$ where $X$ is the number of cliques of size $4$. Note that $E[X]\propto \binom{n}{4}(n^{-2/3})^6\propto 1$ which we can easily see by approximating the binomial as $n^4$. We can do this because $\binom{n}{4}=\frac{n(n-1)(n-2)(n-3)}{4\cdot3\cdot2\cdot1}$ and the top part works out to have a $n^4$ in it. Thus $E[X]=o(1)$ meaning that $E[X]<\epsilon$ for significantly large $n$. Thus we because $X$ can only take on non-negative integers thus $P(X\geq 1)\leq E[X]<\epsilon$. Thus the probability of a graph having clique of size $4$ is less than epsilon. 

Note that when $p=\omega(n^{-2/3})$ we can easily see that $E[X]\rightarrow \infty$. Thus if we can prove that $P(X=0)=o(1)$ then we have proven our conjecture. Luckily we can use our brand new second moment method to do this. So we just need to prove that $\frac{\text{Var}(X)}{E[X]^2}\leq \epsilon$ which further means that we need to prove that $\text{Var}(X)=o(E[X]^2)$. 
To do this we prove the use the fact that if $\text{Var}[X]\leq E[X]+\Sigma \text{Cov}(X_i,X_j)$ if $X_i$ is a random variable that can take on values between $0$ and $1$. 
Now we can attempt to find the value of $\text{Var}[X]=\text{Var}[\Sigma_{1}^{\binom{n}{4}}X_i]\leq \Sigma E[X_i]+\Sigma_{i\neq j} \text{Cov}(X_i,X_j)$. Finding $\Sigma E[X_i]$ is easy because each clique has $6$ edges and we need them to all be present so it is $\binom{n}{4}p^6$ 
Now to find the covariance we break it up into cases. If two cliques either share $0$ or $1$ vertices then they share no edges are are thus independent. 
If they share $2$ vertices then they have one common edge and we know that $E[X_iE_j]-E[X_i]E[X_j]\leq E[X_iE_j]$ which we can calculate $E[X_iX_j]\leq p^11$ because we need all edges to be present. There are $\binom{n}{6}$ ways to choose $6$ vertices, $\binom{6}{2;2;2}$ ways to split them between the groups. 
If they share $3$ vertices then have have $3$ common edges which similarly we see that $E[X_iE_j]-E[X_i]E[X_j]\leq E[X_iE_j]\leq p^{9}$ and there are $\binom{n}{5}$ ways to choose $5$ vertices and $\binom{5}{3;1;1}$ ways to split them. 
And since there is only $4$ vertices in each clique of size $4$ we have done all the cases. Thus we know that $\text{V}[X]\leq\binom{n}{4}p^6+\binom{n}{6}\binom{6}{2;2;2}p^{11}+\binom{n}{5}\binom{5}{3;1;1}p^{9}=o(n^8p^{12})$. Note that $\binom{n}{4}p^6=o(E[X]^2)$ because $\binom{n}{4}p^6=E[X]^2$ and $\lim_{x\rightarrow\infty}\frac{E[X]}{E[X]^2}=\frac{1}{E[X]}$ which $E[X]$ goes to infinity as we have shown earlier. 
Note that $\binom{n}{6}=\Theta(n^6)$ and that $\binom{6}{2;2;2}$ can thus we have NEED TO FINISH
### Lovasz Local Lemma
Often when we have a set of bad events and want to find the probability that none of these events happen. Without this new lemma we would either have to use a union bound, which would be adding up all of their probabilities. Alternatively we can assume that the events are independent and then multiply their probabilities, but this is a strong assumption. 
The Lovasz Local Lemma provides more nuanced approach to this. We say that an event $E_{n+1}$ is mutually independent of $E_1,...,E_n$ if $P(E_{n+1}|\bigcap_{j\in[1,n]}E_j)=P(E_{n+1})$. We define a dependency graphs as a graph where $V$ the vertices of the graph representing the events $E_i$ and the edges $E$.Each event $E_i$ is mutually independent of the set of events $E_j$ 

It states that if for some events $E_1,...,E_n$ if 
1. $\forall i$ $P(E_i)\leq p$ 
2. The degree of the dependency graph is bounded by $d$ 
3. $4dp\leq 1$ 
Then $P(\bigcap_{i=1}^n \bar{E}_i)\geq 0$ 
#### Edge Disjoint Paths
Consider $i=1,...,n$ pairs each of which can choose from a collection of $m$ paths denoted $F_i$. We want to create edge disjoint paths between them

If any path from collection $F_i$ shares edges with no more than $k$ paths in $F_j$ where $i\neq j$ and $8nk/m\leq 1$, there is a way to choose $n$ edge disjoint paths connecting the $n$ pairs
If we consider the probability space defined by each pair picking a random path independently and uniformly. Let $E_{i,j}$ be the event that the pairs $i$ and $j$ pick paths which share at least one edge.
Since a path in $F_i$ shares no more than $k$ edges with $F_j$ then $p=P(E_{i,j})\leq \frac{k}{m}$. Since $E_{i,j}$ is independant of $E_{k,l}$ if $k\not\in\{i,j\}$ and $l\not\in\{i,j\}$ we have the degree of the dependancy graph $d\leq 2n$ because there are $2n$ combos that don't satisfy this.
Thus through the Lovasz Local Lemma $4dp=\frac{8nk}{m}\leq 1$  


## Turning Existence arguments into algorithms
It might seem like these existence proofs are not that useful within the context of computer science but that can sometimes become useful algorithms. 
If you can efficiently randomly sample a space(for example the space of all coloring of a complete graph) and have probability $p$ of finding an object with the properties you desire, you have a Monte-Carlo algorithm with a probability $p$ of success.
If you have an algorithm that can efficiently determine wether the sampled object has a specific property, you can now construct a Las Vegas algorithm that has time complexity $\text{geom}(p)$ 

# Chapter 7: Markov Chains and Random Walks
This chapter introduces a new tool to solving algorithms probabilistically called Markov Chains. 
## Definition of Markov Chain 
A stochastic process is a collection of random variables $X=\{X(t): t\in T\}$. Often the index $t$ represents time but does not need to. Further if for all $t\in T$, $X(t)$ has a countably infinite support then the stochastic process is a discrete time process. 

If a discrete time stochastic process has the Markov property which is defined as follows$P\left(X(t)=a_t|X(t-1)=a_{t-1},X(t-2)=a_{t-2},...,X(0)=a_0\right)=P\left(X(t)=a_t|X(t-1)=a_{t-1}\right)$
it is a Markov Chain. 

If our Markov Chain is time homogenous(meaning $P\left(X(t)=a_t|X(t-1)=a_{t-1}\right)$ is the same for all values of $t$ we can create a matrix which encodes the transition probabilities where the entries encode $p_{ij}=P(X_{t}=j|X_{t-1}=i)$  
which given some starting state represented by a probability vector $x$ we can calculate the $n$ step distribution by computing $xP^{n}$(to prove this you need to do some math but it all works out).
Additionally you can take a Markov Chain and then represent it as a directed graph $(E,V)$ where the edge weights are the probability of transitioning from one state to another. 

## Properties of Markov Chains
- **Irreducible:** This means $p_{ij}^n>0$ for some $n$ for all $i$'s and $j$'s. This intuitively means that you can get from any state to another state after some period of time. Interestingly if a Markov chain is irreducible then all states have the same period. Finally all Markov Chain is consider irreducible if all the states belong to one communicating class
- **Aperiodic:** A chain is a considered aperiodic if every state has period $1$. Intuitively this means that there is no pattern to when you can be in each state, IE it prevents a random walk from being on a specific node only on even time steps. 
- **Reversible:** A Markov Chain is considered reversible if the following property hold for all sequences $P(X_0=i_0,X_1=i_1,...,X_k=i_k)=P(X_0=i_k,X_1=i_{k-1},...,X_k=i_0)$
- **Time Homogenous:** This means that $P(X_{t}=j|X_{t-1}=i)$ for all $t$ 
- **Symmetric:** If $p_{ij}=p_{ji}$ for all $i$'s and $j$'s then it is symmetric. Symmetric MC their stationary distribution is uniform. This is easily proven using the detailed balance equations
- **Ergodic:** If every state of a Markov chain is aperiodic and positive recurrent(meaning the individual state are all ergodic) then the chain is ergodic 
## Properties of States of Markov Chains

- **Communicating Classes:** Two states are said to communicate with each other if there exists some two way path connecting them. A state is said to be accessible if one state can reach another state. We can make an equivalence relation of the classes which can communicate.
- **Recurrent/Transient:** A recurrent state is a state where the probability of returning to a state given infinite time is $1$, where as a transient state is one where the probability of returning to that state is less than $1$ 
- **Positive/Null Recurrent:** There are some Markov chain state that the probability of returning to them is $1$ but the expected value of the time til returning is unbounded. If the expected return time is unbounded, then the state is known as Null Recurrent. Otherwise it is positive recurrent
- **Periodic:** A state is considered periodic if it can only be accessed on steps divisive by a specific non-zero number 
- **Ergodic:** A state that is aperiodic and positive recurrent is considered ergodic 

## Stationary Distributions 
The stationary distribution of a MC is a probability vector(can be thought of as a probability distribution of starting states) $\pi$ such that $\pi P =\pi$. 
If the MC is **Aperiodic** and **Irreducible** then for any starting distribution $\pi^{(t)}$ we have the property $\text{lim}_{t\rightarrow \infty}\pi^{(0)}P^{(t)}=\pi$, the convergence rate is exponential(We can prove this using TV distance). We also have a unique stationary distribution. 
### Detailed Balance Equation
The detailed balance equation is $\pi_{i}P_{ij}=\pi_{j}P_{ji}$. If a vector $\pi$ satisfies DBE, then it is the stationary distribution(There can be stationary distributions which don't satisfy the DBE though). 
We can use this to test if a proposed distribution is the stationary distribution. 

## Random Walks on Graphs
Often a Markov Chain can be represented by using random walk on a graph. Because of this it can be useful to have some stronger results about simple random walks on the graph. 
### Aperiodicity 
If a random walk is on a non-bipartite undirected graph then the Markov Chain is aperiodic. This is because on an undirected graph there is a cycle of of length $2$(moving to an adjacent node) and a cycle of length $3$ because the graph is non-bipartite. Thus the graph is aperiodic because there are two co-prime cycles
### Stationary Distribution
A random walk converges to a the stationary distribution with each entry in the vector representing a specific node with probability $\pi_i=\frac{d(i)}{2|E|}$.
We can see this by using the handshaking lemma to see that $\Sigma d(v)=2|E|$ thus $\Sigma\pi_i=\Sigma\frac{d(v)}{2|E|}=1$(this is basically saying that the probability of transitioning to a specific node from a random node is the number of edges connected to it over the total number of edges). Thus $\pi_v=\Sigma_{u\in N(v)}\frac{d(u)}{2|E|}\frac{1}{d(u)}=\frac{d(v)}{2|E|}$ is equivalent to the statement $\pi P=\pi$ 
### Cover time
The cover time of a graph, is the maximum expected value of the time it would take to visit every vertex. 
Let $h_{u,v}$ be the expected number of steps to get from node $u$ to node $v$. The commute time of two nodes is $h_{u,v}+h_{v,u}$ and we can show that if $(u,v)\in E$ then $h_{u,v}+h_{v,u}\leq 2|E|$. 

We can prove this by instead of analyzing a Markov chain transversing a undirected graphs nodes, we instead view it as a Markov Chain which the states are the directed edges of the graph. 
This new Markov Chain will have a uniform stationary distribution. And since the expected return time of a state is the reciprocal of its stationary probability, when we leave node $u$ to $v$ the expected time to return is $2|E|$. This is a massive upper bound on the return time but it is worth it for our next theorem

We can now prove that the cover time of a graph $(V,E)$ is bounded by $2|E|(|V|-1)$. 
We can create a spanning tree of the graph, and then create a cycle on it, meaning that every single edge is traversed twice(once in each direction). This can be found using depth first search.
This gives a specfic sequence of vertexes which are visited in order denoted $v_0,v_1,...,v_{2|V|-2}$. Thus we previously proved that the time to get from $v_i$ to $v_{i+1}$ is bounded by $2|E|$ and there are $|V|-1$ pairs thus the commute time is bounded by $2|E|(|V|-1)$ 

But we can push this bound even further with another bound which says the cover time $C_G$ of a graph $G=(V,E)$ with $n$ vertices is bounded by $C_G\leq H(n-1)\text{Max}_{u,v\in V:u\neq v}h_{u,v}$. 
To make the proof more concise we write that $B=\text{Max}_{u,v\in V:u\neq v}h_{u,v}$. We define some random ordering of the vertices of the graph chosen uniformly among all permutations $[Z_1,Z_2,...,Z_n]$. Let $T_j$ be the time step at which each the first $j$ of the vertices have been visited. And let $A_j$ be the last of the first $j$ vertices($[Z_1,Z_2,...,Z_j]$) visited.
Note that the cover time $C_G=T_1+(T_2-T_1)+(T_3-T_2)+...+(T_n-T_{n-1})$ if $Z_1$ happens to be the first node chosen then we have $T_1=0$ which happens with probability $\frac{1}{n}$. Next we have is $Z_1$ is not the first node chosen then $T_1\leq B$ because $B$ is the maximum hitting time. Thus $E[T_1]\leq(1-\frac{1}{n})B$ 
For $(T_{j+1}-T_j)$ we first consider the case where $Z_j$ is not the last element reached in the set $[Z_1,Z_2,...,Z_j]$. If this is the case then $(T_{j+1}-T_j)=0$ and this happens with probability $\frac{j-1}{j}$. The other case is that $Z_j$ is the last element to be seen this happens with probability $\frac{1}{j}$ and $(T_{j+1}-T_j)\leq B$ because it now needs to hit $Z_j$. Thus we can now write the following inequality
$C_G\leq \Sigma_{j=2}^n \frac{1}{j}B+(1-\frac{1}{n})B=(1+\Sigma_{j=2}^{n}\frac{1}{j})B-\frac{1}{n}B=H(n-1)B$ 

## Applications
### SAT-2 Problem
The goal of the SAT-2 problem is to create a set of boolean assignments, which satisfies a bunch of clauses each with two variables in them. An example might be 
![[Screenshot 2026-07-04 at 9.01.56 PM.png]]
The algorithm works by doing the following 
1. Assign an arbitrary truth assignment
2. Repeat up to $2mn^2$ the following, find a clause which is not satisfied and then uniformly alter a variable which is not satisfied 
3. If a valid truth assignment has been found, return it 
4. Otherwise return that the system is unsatisfiable 
The core idea is that all the clauses must be satisfied in order to have a satisfying assignment, so you just go wack a mole-ing until you find something that works
We know that step $2$ takes $O(n^2)$ because there are $n^2$ possible clauses.
To take about the time complexity and accuracy of this algorithm we are going to define a few random variables.
Let $S$ be the satisfying assignment of the system, $A_i$ be the current solution set at the $i$th step and let $X_i$ be the number of boolean assignments in $A_i$ which agree with $S$. 
If $X_0=0$ then we know with $100\%$ probability that $X_1=1$ because changing any clause will increase the number of correct assignments 
Now for time steps $1\leq x\leq n-1$ we know that $A_x$ disagrees at at least one clause. If both of the clauses disagree then we know that $X_{x+1}=X_x+1$. Otherwise then if a clause is unsatisfied then one may be correct and one be incorrect. In this case then the probability of $X_x$ increasing is $\frac{1}{2}$ and the probability of $X_x$ decreasing is $\frac{1}{2}$, this is a massive underestimation of the algorithm but for the purposes of analyzing it we are using it. 
So now to analyze the time complexity and accuracy we need to look at this random walk. Now we want to find $h_j$ which is the expected number of steps to reach $n$(thus completing the algorithm) and $Z_j$ which is a random variable representing the number of steps to reach $n$. 
To start we know that $h_n=0$(because we would have been there) and $h_1=h_0+1$ because we know that $0$ always transitions to $1$. Additionally $E[Z_j]=E[\frac{1}{2}(1+Z_{j-1})+\frac{1}{2}(1+Z_{j+1})]$, but since $E[Z_j]=h_j$ by linearity of expectations $h_j=\frac{h_{j-1}}{2}+\frac{h_{j+1}}{2}+1$. 
Thus we have the following system of equations $h_n=0$, $h_j=\frac{h_{j-1}}{2}+\frac{h_{j+1}}{2}+1$, $h_0=h_1+1$ which we can solve giving us $h_0=\Sigma^{n-1}_{i=0}(2i+1)=n^2$. Thus we have proven that the expected runtime of this algorithm is $n^2$. 
Now to talk about this algorithm accuracy, if there is no satisfying assignment the algorithm is always correct. 
If there is a satisfying assignment we can break up the algorithm into $m$ segments each with $2n^2$ steps in them. Then we get the following probability using Markov's inequality $P(Z>2n^2)\leq \frac{n^2}{2n^2}=\frac{1}{2}$. Since there are $m$ of these steps the probability of all of them failing is $(\frac{1}{2})^m$. Further this means that we can achieve this level of accuracy at an embarrassingly parallel level, by running each $2n^2$ segment separately  
### SAT-3 problem 
We can do almost the exact same algorithm as the SAT-2 problem, but when we solve the new system of equations(noting that the probability of choosing the wrong literal being $\frac{1}{3}$ instead of $\frac{1}{2}$) we end of with a algorithm that runs in $\Theta(2^n)$. 
But since there are only $2^n$ solutions this does not seem much better than just a brute force algorithm. 
But accounting for two more details, we can actually improve on this algorithm. 
First when we pick a solution set randomly, the number of satisfied solutions is distributed as $\text{Bin}(n,\frac{1}{2})$. This means that while getting the solution correct randomly is incredibly rare, getting a good solution set(one that has a lot of variables satisfied) is actually pretty likely. 
Next the Markov Chain actually tends to move down rather than up, meaning its better to reset often than it is to continue with a chain. 

So now we are going to work on an algorithm which using the following steps 
1. Repeat up to $m$ times, terminating this loop if all clauses are satisfied, start with a random truth assignment and take $3n$ steps
2. If a valid truth assignment has been found return it
3. Otherwise return that there is no valid truth assignments
Now we want to find the value $q$ that is the probability that one of these iterations of the loops finds a satisfying assignment given that there is one. Further let $q_j$ represent the probability that a Markov Chain finds the satisfying assignment, given exactly $j$ variables are incorrect.
Now see that the following equation represents the probability that one of these walks moves down $k$ and moves up $j+k$ 
$$
\binom{j+2k}{k}(\frac{2}{3})^k(\frac{1}{3})^{j+k}
$$
So the probability $q_j\geq \text{Max}_{k=0,...,j}\binom{j+2k}{k}(\frac{2}{3})^k(\frac{1}{3})^{j+k}$ because all of these step combinations would lead to a success. We specifically look at the case where $k=j$ meaning that $q_j\geq\binom{3j}{j}(\frac{2}{3})^j(\frac{1}{3})^{2j}$. We then use Stirlings formula(can't find anywhere in the book but it said that they did it)  which states that $m!=\sqrt{2\pi m}(\frac{m}{e})^m(1\pm o(1))$ to approximate $\binom{3j}{j}$. 
We can see that $\binom{3j}{j}=\frac{(3j)!}{j!(2j)!}\geq \frac{\sqrt{2\pi(3j)}}{4\sqrt{2\pi j}\sqrt{2\pi(2j)}}(\frac{3j}{e})^{3j}(\frac{e}{2j})^{2j}(\frac{e}{j})^j$ which equals $\frac{\sqrt{3}}{8\sqrt{\pi j}}(\frac{27}{4})^j=\frac{c}{\sqrt{j}}(\frac{27}{4})^j$ 

Thus from all that we get $q_j\geq \frac{c}{\sqrt{j}}\frac{1}{2^j}$ with $q_0=1$. Now we want to find the probability of sucess $q$. We can see that $q\geq \Sigma_{j=0}^{n}P(\text{a random assigment has j mismatches with S})\cdot q_j$ this is a $\geq$ because we are using a lower bound of $q_j$. But since $P(\text{a random assigment has j mismatches with S})=\binom{n}{j}(\frac{1}{2})^n$ then $\Sigma_{j=0}^{n}P(\text{a random assigment has j mismatches with S})=\Sigma\binom{n}{j}(\frac{1}{2})^{j}$  which we can use the binomial theorem on the rewritten $\Sigma\binom{n}{j}(\frac{1}{2})^{j}=\Sigma\binom{n}{j}(\frac{1}{2})^{j}(1)^{n-j}=(1+\frac{1}{2})^n$.
Thus from all that $$q\geq \frac{1}{2^n}+\Sigma_{j=1}^{n}\binom{n}{j}(\frac{1}{2})^n\frac{c}{\sqrt{j}}\frac{1}{2^j}\geq\frac{c}{\sqrt{n}}(\frac{1}{2})^n \Sigma_{j=0}^{n}\binom{n}{j}(\frac{1}{2})^j(-1)^{n-j}$$
Which can be further be rewritten as 
$$
\frac{c}{\sqrt{n}}(\frac{1}{2})^n \Sigma_{j=0}^{n}\binom{n}{j}(\frac{1}{2})^j(-1)^{n-j}=\frac{c}{\sqrt{n}}(\frac{1}{2})^n(\frac{3}{2})^n=\frac{c}{\sqrt{n}}(\frac{3}{4})^n
$$
Thus $q\geq\frac{c}{\sqrt{n}}(\frac{3}{4})^n$. Thus the expected number of tries is less or equal to $\frac{1}{q}$ meaning the expected number of steps is $(3n)\cdot \frac{c}{\sqrt{n}}(\frac{3}{4})^n$ which dropping constants and gives us a expected time complexity of $O(n^{3/2}(\frac{4}{3})^n)$. 

We then can use Markov's inequality so if we run the algorithm for $2$ times the expected value, the probability of failure is $\frac{1}{2}$ so running it again and again gives us the exponentially decaying probability of failure of $(\frac{1}{2})^{-b}$ 

### The Gamblers Ruin
The gamblers ruin is similar to the coupon collectors problem, meaning that it comes up all the time outside its original context.
Its modeled by two players each starting with dollars $l_1$ and $l_2$ respectively. Each round the they flip a coin and with probability $\frac{1}{2}$ player $1$ gives player $2$ a dollar, otherwise player $2$ gives player $1$ a dollar. 
The game ends when one player runs out of money, what we are interested in the probability that a specific player wins. We can easily model this as a Markov Chain that starts at zero and has an equal probability of either moving up or down $1$ with all states being transient expect the absorbing states $l_1$ and $l_2$. 

If we define $W^t$ as the gain of player $1$ after $t$ steps and $q$ as the probability of the Markov Chain being absorbed by $l_1$. Obviously we see that $E[W^t]=0$. Since all states are transient other than $l_1$ and $-l_2$ we see that $E[W^t]=l_1q-l_2(1-q)=0$ which from this we can rewrite this equation to solve for $q=\frac{l_1}{l_2+l_1}$ 
### Cut property
While this is not a direct application it is such a useful theorem that I am going to include it in the application section.
Also rather than proving it I am going to provide a vibe wise explanation of it. 
Given a set of states $S$ the probability that the set of states is entered, is the probability that it is exited in the stationary distribution. 
The vibes wise explanation is that if this was not the case it would not be the stationary distribution because more would want to flow in or out. 
### Simple Queue
For a simple queue where if there is less then $n$ items in the queue with probability $\lambda$ a new item enters the queue, if there is a non-zero number of items in the queue then with probability $\mu$. With the remaining probability the queue remains unchanged. 

We are curious about the number of customers in the queue $X_t$, so we analyze it as a Markov Chain. Since this Markov Chain is aperiodic and irreducible it has a unique stationary distribution,

We get the system of equations $\pi_0=(1-\lambda)\pi_0+\mu \pi_1$, $\pi_1=\lambda_{pi_{i-1}}+(1-\lambda-\mu)\pi_i+\mu_{\pi_{i+1}}$, and $\pi_n=\lambda \pi_{n-1}+(1-\mu)\pi_n$ 

Which solving gives $\pi_0=\frac{1}{\Sigma_{i=0}^{n}(\frac{\lambda}{\mu})^{i}}$ and $\pi_i=\frac{(\mu/\lambda)^i}{\Sigma_{i=0}^{n}(\frac{\lambda}{\mu})^i}$. Which tells me given a significant time from the beginning of the chain  the probability of there being a specific number of people 


### $s-t$ Connectivity Algorithm 
This algorithm determines wether there exists a path connecting $s$ and $t$ in a given graph $G=(V,E)$, let $n=|V|$ and $m=|E|$. It works very simply by starting the chain at vertex $s$ and then having it run for $2n^3$ steps and if it has visited node $t$ it returns that there is a path, otherwise it returns that there is no path. 
If there is no path than the algorithm always returns the correct answer. If there is a path the time taken to travel from $s$ to $t$ then it is bounded by the cover time $2|E|(|V|-1)$ which is less than $2nm\leq n^3$. Now we can use Markov's inequality to which states that if we run it for $2n^3$ steps then we have a probability of failure of at most $\frac{1}{2}$  
# Chapter 8: Continuous Random Variables
While discrete random variables are incredibly useful. Often in the real world we are faced with scenarios where. The beginning of this chapter mostly talks about the exponential and uniform distribution but I am not taking notes 
## Balls and Bins with feedback
The situation is two bins each one starting with one ball, with bin $1$ gaining a new probability with $\frac{x^p}{x^p+y^p}$ and bin $2$ gaining a new ball with probability $\frac{y^p}{x^p+y^p}$.  If $p>1$ then with probability $1$ there will reach a point where one of the bins gets infinite balls. 

While it seems weird you can actually represent these using exponentials. If bin $1$ obtains its $z$th ball at time $t$ and then obtains its $z+1$th ball at time $t+T_{z}$ with an exponential with parameter $z^p$. At the same time bin $2$ obtains its $z$th ball at time $t$ and then obtains its $z+1$th ball at time $t+U_{z}$ with an exponential with parameter $z^p$. 

If at a given time if bin $1$ has $x$ balls and bin $2$ has $y$ balls then the probability bin $1$ gets the next ball is $\frac{x^p}{x^p+y^p}$. Additionally by the memoryless property the continuous time part does not matter. 

Next we look at something called the saturation time $F_1=\Sigma_{j=1}^{\infty} T_j$ and $F_2=\Sigma_{j=1}^{\infty} U_j$ which has some surprising properties. First the expectation is finite $E[F_1]=E[\Sigma_{j=1}^{\infty} T_j]=\Sigma_{j=1}^\infty\frac{1}{j^p}$ which we can show $\Sigma_{j=1}^\infty\frac{1}{j^p}\leq 1+\int_{u=1}^{\infty}\frac{1}{u^p}=1+\frac{1}{p-1}$ using the idea of stepping on the inside of it. 

Now we just have to find the probability that they are equal, so we assume by way of contradiction they are thus $T_1=\Sigma_{j=2}^{\infty} T_j+\Sigma_{j=1}^{\infty} U_j$ and the probability of $T_1$ equally any specific value is zero thus they do not equal each other. 
The proof is pretty much done now
## Poisson Process
A poisson process is a situation that arises in nature a large amount of the time. Examples include people waiting in a line to be helped, or the amount of alpha particles emitted from radioactive procedures. There are a large number of definitions for it but the more simple one is the following. It is a stochastic counting process 
1. $N(0)=0$
2. The time between increments of $N(t)$ are independent identically distributed exponential random variables with parameter $\lambda$ 
### Facts about Poisson Processes
1. The sum of two independent poisson processes $N(\lambda_1)$ and $N(\lambda_2)$ results in a poisson process with parameter $N(\lambda_1+\lambda_2)$. The chance of an event being from the first poisson process is $\frac{\lambda_1}{\lambda_1+\lambda_2}$. 
2. Conditioning on the number of arrivals that happen over a specific time period, they are uniformly distributed over that interval

## Markov Processes
Before going into queues its useful to learn what a Markov Process is. It is the continuous time version of a Markov Chain with discrete number of states. 
To model this we have a transition matrix which determines the probability of transitioning from one state to another state(like a Classical Markov Chain) as well as a vector of parameters that determine when the state transitions from one to another denoted $(\theta_0,...,\theta_n)$. The Markov chain remains in state $i$ with an exponential with parameter $\theta_i$. 

This brings up the immediate question of what does the stationary distribution look like? Obviously if they all had the same exponential parameter then it would converge to its normal stationary distribution.

To find this we need to do a kinda annoying proof that I am not going to do right now NEED TO FINISH 

## Markovian Queues
Now that we have



# Chapter 10: Entropy, Randomness, and Information
This chapter thats about a statistic of a random variable known as entropy. It measures how random or unpredictable a random variable is.
## Entropy Definition 
Entropy is defined as the following 
$$H(X)=-\Sigma_xP(X=x)\log_{2}(P(X=x))$$
which can be interpreted via LOTUS as $H(X)=E[\log_2(\frac{1}{P(X)})]$. We choose the negative log function because we want independent events to be be additive, and we want it to be positively valued. 
We denote the binary entropy function as $H(p)=-p\log_2 p -(1-p)\log_2(1-p)$ which is the entropy of a coin flip with probability of heads $p$. Note that when you lose log base $2$ entropy is measured in bits. 
Through a long and not necessarily insightful proof you can prove that $H(X)+H(Y)=H(X+Y)$ if $X$ and $Y$ are independent. 
### Entropy decreases through functions 
We can further prove something more useful and profound in the context of machine learning. Given random variable $X$ and another random variable $Y=f(X)$ we can prove that $H(X)\leq H(Y)$ showing that you can't increase entropy. 
Note that $H(X,Y)=H(X)+H(Y|X)=H(Y)+H(X|Y)$. But since $Y$ is a function of $X$ then we know that $H(Y|X)=0$. Thus $H(X)=H(Y)+H(X|Y)$  and since entropy is always positive for discrete random variables we see that $H(X)\geq H(Y)$ 
## Entropy within a combinatorial Context 
The first lemma that shows how entropy shows up in a combinatorial context. Suppose that $nq$ is a integer in the range $[0,n]$ then 
$$
\frac{2^{nH(q)}}{n+1}\leq \binom{n}{nq}\leq2^{nH(q)}
$$
This is immediately apparent if $q=0$ or $q=1$. If $0<q<1$ then we see that
$$\binom{n}{nq}q^{qn}(1-q)^{(1-q)n}\leq\Sigma_{k=0}^{n}\binom{n}{k}q^k(1-q)^{n-k}$$
because the first part only contains one term from the sum. Then we can use the binomial theorem to get $\Sigma_{k=0}^{n}\binom{n}{k}q^k(1-q)^{n-k}=(q+(1-q))^n=1$. Thus we get $\binom{n}{nq}q^{qn}(1-q)^{(1-q)n}\leq 1$ which can be rewritten as $\binom{n}{nq}\leq q^{-qn}(1-q)^{-(1-q)n}$ which using the trick $q^{-qn}=(2^{\log_2 q})^{-qn}$ to see that $q^{-qn}(1-q)^{-(1-q)n}=2^{nH(q)}$ thus we have proven the upper bound $\binom{n}{nq}\leq2^{nH(q)}$. 

Now we just need to prove the lower bound. Similar to the proof above we show that $\binom{n}{nq}q^{qn}(1-q)^{(1-q)n}$ is the largest term in the sum. I am not going to show the algebra, but because it is the largest term in the sum we get $\binom{n}{nq}q^{qn}(1-q)^{(1-q)n}\geq \frac{1}{n+1}$ which is the same as $\binom{n}{nq}\geq \frac{q^{-qn}(1-q)^{-(1-q)n}}{n+1}=\frac{2^{nH(q)}}{n+1}$ proving our conjecture.  

Then further, similar to the proof above we get if $0\leq q \leq \frac{1}{2}$ then $\binom{n}{\lfloor nq \rfloor}\leq 2^{nH(q)}$ and if $\frac{1}{2}\leq q \leq 1$ then $\frac{2^{nH(q)}}{n+1}\leq\binom{n}{\lceil nq \rceil}$.

This is important because we know via chernoff bounds that for large number of coin flips that the number of flips that are heads is going to be around $np$ so it will specific be uniformly distributed as one of the $\binom{n}{np}\approx 2^{nH(p)}$ sequences containing this amount   

## Entropy as Randomness
We have already talked about how entropy is a measure of randomness. But we are going to talk about functions that extract random bits from from a random variable. We call this an extraction function and it is defined as 
$$
P(\text{Ext}(X)=y||y|=k)=\frac{1}{2}^k
$$
Note that it needs to have this probability otherwise the functions bits would not be independent and uniformly random.
Here is a table giving an example of an extraction function
![[Screenshot 2026-07-09 at 1.22.08 PM.png|301]]

### Extracting fair bits
Fair bits are incredibly useful and be be used to generate pretty much all forms of discrete randomness. Here we look at a few ways to generate these random bits from other random variables
#### From Uniform Randomness
Given a uniform random variable $X$ with support $\{0,...,m-1\}$. Note that this random variable would have entropy $H(X)=\log_2m$. We can create an extraction function that on average outputs at least $\lfloor\log_2 m \rfloor-1=\lfloor H(X)\rfloor-1$ independent unbiased bits.

If $m$ is a power of two then we can just use the binary representation of the output. This always outputs $\log_2 m$ bits. 
If $m$ is not a power of two, then we can recursively define a function that outputs fair bits. Let $\alpha = \lfloor \log_2 m \rfloor$. If $X\leq 2^\alpha -1$ then we can just output the binary representation of the output. If $X\geq 2^\alpha$ then $X-2^{\alpha}$ is uniformly distributed. Then recursively do the process on this new random variable again. 
We now create a random variable $Y$ which represents the number of random bits outputted by this function. 
We can see that $E[Y]\geq \frac{2^\alpha}{m}\alpha+\frac{m-2^{\alpha}}{m}(\lfloor \log_2(m-2^{\alpha}) \rfloor-1$ because $\frac{2^{\alpha}}{m}$ percent of the time we get $\alpha$ random bits out. Then because of our inductive hypothesis the rest of the time we get $\lfloor \log_2(m-2^{\alpha}\rfloor-1$ random bits out 
#### From Biased Bits
The idea behind this is if you have a sequence of $n$ bits denoted $\{0,1\}^n$ and you condition on the number of ones within the string, the probability distribution of bit strings of length $n$ with $k$ ones is uniform among all of them. 
Thus we can define a extraction function which takes in the number of heads $k$, and maps the bit string to one value in the set  $\{0,...,\binom{n}{k}\}$ uniquely. From this we can use our extraction function from the uniform distribution on it. 
Now that we have the core idea of our extraction function, we now needs to deal with the fact that it is biased and figure out how many bits on average this extraction function is going to output. 

More formally if $Z$ is the number of heads flipped, and $B$ is the number of bits extracted for a given sequence of flips. We can see via the law of total expectation that $E[B]=\Sigma_{k=0}^{n}P(Z=k)E[B|Z=k]$. We can easily find the value of $E[B|Z=k]$ via our previous extraction function and theorem giving us $E[B|Z=k]\geq\lfloor\log_2\binom{n}{k}\rfloor-1$ 

We can get a lower bound on $E[B]$ by having $\epsilon<\text{min}(p-\frac{1}{2},1-p)$. Now we only consider the $k$ values with $n(p-\epsilon)\leq k\leq n(p+\epsilon)$  
Thus we get $E[B]\geq \Sigma_{k=\lfloor n(p-\epsilon)\rfloor}^{\lceil n(p+\epsilon) \rceil}P(Z=k)E[B|Z=k]$
We know that $E[B]\geq \Sigma_{k=\lfloor n(p-\epsilon)\rfloor}^{\lceil n(p+\epsilon) \rceil}P(Z=k)(\lfloor\log_2\binom{n}{k}\rfloor-1)$  
But from the section entropy and combinatorics we know that $\binom{n}{k}\geq\binom{n}{\lfloor n(p+\epsilon) \rfloor}\geq \frac{2^{nH(p+\epsilon)}}{n+1}$   thus we can replace the $\binom{n}{k}$ with $\frac{2^{nH(p+\epsilon)}}{n+1}$ and to deal with the floor we subtract $1$. Additionally since the second part no longer contains a $k$ we get to move it outside of the summation 
$E[B]\geq(\log_2 \frac{2^{nH(p+\epsilon)}}{n+1}-2)\Sigma_{k=\lfloor n(p-\epsilon)\rfloor}^{\lceil n(p+\epsilon) \rceil }P(Z=k)$ 
Then using the properties of logs we can break up the fraction in the log and the right side is equivalent to the statement that $P(|Z-np|\leq \epsilon n)$. Since we know that $E[Z]=np$ we can place a chernoff bound on $P(|Z-np|>\epsilon n)$ finding that $P(|Z-np|>\epsilon n)\leq 2e^{-n\epsilon^2/3p}$ 
This finally gives us $E[B]\geq (nH(p+\epsilon)-\log_2(n+1)-2)(1-2e^{-n\epsilon^2/3p})$ which as $n$ gets sufficiently will converge to $E[B]\geq (1-\delta)nH(p)$    

### Compression
Another way you can view entropy is information and how effective you can compress that information. For example a random viable with zero entropy would always be the same thus you wouldn't need to encode it. 
Often when compressing a sequence of random variables its useful to write the code as prefix free. This mans that none of the realizations which we encode are prefixes of another one. This allows us to actively read the bits as a data stream rather than waiting until we have all the bits or not having a unique solution. 
Within this we are only considering lossless compression algorithms 

#### Definition of a Compression Function
Within the context of the textbook I am reading a compression function is a function which takes in a sequence of $n$ coin flips aka an element of $\{H,T\}^n$ and outputs a sequence of bits such that every input has a unique output.  

#### Compression Algorithm on Biased Bits
We want to design a compression algorithm on a stream of biased bits. We want to minimize the expected number of bits used for a specific sequence of $n$ bits. Which we will denote $E[B]$. Right off the bat we can see how probability is involved in this situation. If we have two strings $S_1$ and $S_2$ where $S_1$ is more probable than $S_2$ then we want to the length of the compressed string to be less than it(if we don't have this we could swap their representations and then get a lower number of expected bits). 
We can break down our compression algorithm using the law of total expectation.

If there are less than $n(p-\epsilon)$ heads then we use an expensive "compression" algorithm where we set the first bit to $1$ and then the rest of the bits to just the exact sequence. This means that we use $n+1$ bits. We can place a chernoff bound on the probability that $P(X<n(p-\epsilon))<e^{-n\epsilon^2/2p}$

Now we need to consider the case where there are more than $n(p-\epsilon)$ $1$'s in our bit string. 





 

# Markov Chain Mixing times
## Mixing Times 
It would be useful to be able to see how far the $n$ step distribution of a Markov Chain is from the stationary distribution. But before that we need to be able to measure the distance between distributions. 
### Total Variation Distance
We can define a distance metric between two distributions defined as the three equivalent definitions
- $||\mu - \nu||_{TV}=\text{Max}_{A\subset S}|\mu(A)-\nu(A)|$
- $||\mu - \nu||_{TV}=\frac{1}{2}\Sigma_{x\in S}|\mu(x)-\nu(x)|$
- $||\mu - \nu||_{TV}=\text{inf}\{P(X\neq Y): (X,Y)\text{is a coupling of }\mu\text{ and }\nu\}$

Its nice having all of these definitions because we can just pick the one that is most convenient for our use-case. 
The third definition of TV distance is nice because any coupling you create will be an upper bound on the TV distance. Thus if we can be clever about our couplings we can bound the total variation and the mixing time. A coupling of two random variables $X$ and $Y$ is a joint random variable such that the marginal of $X$ is $\mu$ and the marginal of $Y$ is $\nu$. 
We always have the independent coupling but we can get clever and make better ones that are not independent. 


The maximal distance to stationary is defined as $d(t) = \text{Max}_{j\in S}||\pi_{x_0=j}^{(t)}-\pi||_{TV}$. The mixing time of a Markov Chain is defined as $t_{\text{mix}}(\epsilon)=\text{min}\{t|d(t)\leq \epsilon\}$

### Coupling Methods for mixing times
A coupling of Markov Chains is defined as pair of stochastic processes $(X_{t},Y_{t})$ where both processes follow the same transition matrix $P$ but can start at different initial conditions.

We know that $||\pi_{x}^{(t)}-\pi_{y}^{(t)}||_{\text{TV}}\leq P(X_{t}\neq Y_{t})$ because every step of the stochastic process is a valid coupling of $\pi_{x}^{(t)}$ and $\pi_{y}^{(t)}$. 

We can always do the independent coupling, but in the case of a lazy random walk(a random walk with a $50\%$ of staying in the same location) we can define a better coupling. We can flip a coin and randomly pick who advances, with the one who doesn't advance staying in the same state. 
Additionally we add the condition that once they equal each other, they always equal each other transitioning together. This massively decreases $P(X_{t}\neq Y_{t})$ as overtime it becomes smaller and smaller.


The coupling time denoted $\tau_{t}=\text{min}\{t\geq 0:X_{t}=Y_{t}|X_{0}=i,Y_{0}=j\}$ 
We get another bound of $||X_{i}^{(t)}-X_{j}^{(t)}||_{\text{TV}}\leq P(\tau_t>t)$. 

Also know that $d(t)\leq\text{Max}_{i,j\in S}||\pi_{X_0=i}^{(t)}-X_{Y_{0}=j}^{(t)}||_{\text{TV}}$ 



### Spectral Methods for mixing times
We know the following facts about the transition matrix $P$ of a Markov Chain 
- If $\lambda$ is an eigenvalue of $P$ then $|\lambda|\leq 1$ 
- If $P$ is irreducible then $\lambda=1$ has an eigenspace of $\vec{1}$
- If $P$ is irreducible and aperiodic then it does not have $-1$ as an eigenvalue 

We can define a new inner product space $(\mathbb{R}^n,<.,.>_{\pi})$. Where $<f,g>_{\pi}=\Sigma_{x\in S}f_x g_x \pi_x$

If our Markov Chain is reversible with respect to $\pi$ then then the following is true
- $(\mathbb{R}^n,<.,.>_{\pi})$ has an orthonormal basis of eigenvectors $f^{k}$ with associated real eigenvalues $\lambda_k$
- $P$ can be decomposed into $\frac{p_{ij}^{(t)}}{\pi_{j}}=\Sigma_{k=1}^{n}f_{i}^{k}f_{j}^{k}\lambda_{k}^{t}$

We have something called the separation distance $s(t)=\text{Max}_{j}[1-\frac{p_{ij}^{(t)}}{\pi_{j}}]$ 

We have another bound $||\pi^{(t)}_{X_0=i}-\pi||_{\text{TV}}\leq s(t)$ 

$\lambda_{*}=\text{Max}\{|\lambda_k|:\lambda_{k}\text{ is an eigenvalue and }\lambda_{k}\neq 1\}$ we define the absolute spectral gap as $\gamma_{*}=1-\lambda_{*}$

The relaxation time is defined as $\frac{1}{\gamma_{*}}$
We get another bound of $t_{\text{mix}}(\epsilon)\leq t_{\text{rel}}\log(\frac{1}{\epsilon \pi_{\text{min}}})$ 

GOOD PROOFS TO DO
- $d(t+1)\leq d(t)$
- DBE implies stationary 
- Proof TV is a distance metric 
- Prove equivalent definitions of TV distance 



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
