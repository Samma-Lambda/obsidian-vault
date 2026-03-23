---
tags:
  - Applied
---
The Chinese Remainder Theorem(CRT) is a wave of solving a system of simple congruences. An example of something that could be solved using the Chinese remainder theorem is 
$$
x\equiv 3 \mod{5},
x\equiv0 \mod{2},x\equiv2 \mod{3}
$$
its works by doing the following. You answer will but put mod the product of all the numbers(because $\mathbb{Z}/30\cong \mathbb{Z}/5 \oplus \mathbb{Z}/2 \oplus \mathbb{Z}/3$). We then compute a partial modulus for each part of the system so for this case($6,15,10$) and then find the modular inverse of these. This makes the solution look like 
$$
x\equiv[3][6][6]^{-1}_5+[0][15][15]^{-1}_{2}+[2][10][10]^{-1}_{3}\mod{30}
$$
We can see how this works by looking at each individual congruence. Since $[15]$ and $[10]$ are the same thing as zero it zeros out those sections. Then the part that zeros the section for the other section is inverted mod five resulting in just the three being left. 
Beyond just being useful for the integers any single field can use this, so for example you can find conguences of polynomials but I am not sure where that would be useful