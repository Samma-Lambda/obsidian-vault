---
tags:
  - Applied
---
# Mod Power Algorithm
The point of the mod power algorithm is exactly what it sounds like it is for quickly computing $a^n\mod m$ where $\text{GCD}(a,m)=1$ quickly. Note that if $\text{GCD}(a,m)=1$ then $a$ has a multiplicative inverse mod $m$. This means we are working in the group $(\mathbb{Z}/m)^{\times}$ under multiplication. 

We can quickly calculate the order of this group by calculating $\phi(m)$, If you can find the prime divisors of it because $\phi(p_1^{n_1}p_2^{n_2}...p_n^{n_n})=n\Pi_{p|n}(1-\frac{1}{p})$ 

So due to Lagrange's theorem we know that $a^n\mod{m}\equiv a^{n\mod{\phi(m)}}\mod m$. Which by reducing the power allows us to not have to do a ton of multiplication. 


# RSA Encryption
From the previous fast power algorithm we can see that $\phi(pq)=\phi(p)\phi(q)=(p-1)(q-1)$ which is incredibly easy to calculate. But given $m=pq$ finding the prime divisors of this is incredibly hard. So from this problem we have a backdoor for encryption
RSA encryption works by doing the following steps, with Alice as the sender and Bob as the receiver and Eve being the interceptor 
1. The private key $K_{\text{priv}}$ is created by Alice by multiplying two large primes 
2. The Euler Totient function is calculated easily on $K_{\text{priv}}$ which is easily done 
3. Then an exponent $e$ is found that is coprime from $\phi(K_{\text{priv}})$ 
4. Then we find the multiplicative inverse of $e \mod \phi(K_{\text{priv}})$ which can be done using the extended euclidian algorithm 
5. We then publish $K_{\text{Priv}}$ and $e$ and tell anyone who wants to send us messages(in the form of a number) to send us the number to the power of $e$
6. When we receive this number we raise it to the power of $e^{-1}$ and then get the original value back
This whole encryption is based off the hard problem of prime factorization. For someone to intercept the message they would need to do the prime factorization algorithm quickly 