---
applied:
---
Signal processing is a field of mathematics that analyzes, modifies and synthesizes signals. 

# What is a signal 
A signals come in two main varieties **discrete** and **Continuous**. A discrete signal $x$ is a sequence(Function whose domain is $\mathbb{Z}$) and we denoted the $n\text{th}$ element of a signal is denoted $x[n]$. A continuous signal is a function from $\mathbb{R}$. There are some interesting differences between **Discrete** and **Continuous** signals, discrete signals frequency is bounded between $[-\pi,\pi)$ and some discrete versions of continuous samples are not periodic 

You can both add signals together and scale them. You can also shift them by defining $y[n]=x[n-k]$
## Notable Signals
- **Impulse:** This is denoted as $\delta[n]$ and $\delta[n]=1$ if $n=n$ and $0$ elsewhere. Every single can be written as a linear combination of impulses 
- **Unit Step:** This is defined as $u[n]=1$ if $n\geq0$ and $0$ elsewhere 
- **Exponential:** This is a signal whose amplitude is $a\alpha^n$. This results in it either exponentially decaying or exponentially growing

# What is a system
A system is a function which takes in a signal and then outputs another signal. It can have the following conditions 
## Types of systems 
- **Linear:** A linear system $T$ is a system such that $T(a[n]+b[n])=T(a[n])+T(b[n])$ and $T(c\cdot a[n])=cT(a[n])$
- **Memoryless:** This is a system which $y[n]$ can be calculated with only $x[n]$ 
- **Time Invariant:** This is a system in which a shifted input results in a equally shifted output
- **Causal:** This is a system which the output $y[n]$ only needs $x[n_i]$ where $i\leq n$ 
- **Stability:** This is a system where for every bounded input $|x[n]|$