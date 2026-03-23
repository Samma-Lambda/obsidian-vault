---
tags:
  - Computer
---
Time complexity is abstractly the study of how long an algorithm will take to run for a given input size. Here are an example below 

Often the constants in all notation are dropped, so if you have something with a time complexity of $5n^2$ it just becomes $n^2$ 
# Big $\mathcal{O}$ notation 
This is often described as the worst case time complexity of an algorithm based off the size of an input. An example might be searching an unsorted array, if there are $n$ elements in the array then the worst case you would search $n$ elements. This would be denoted as $\mathcal{O}(n)=n$

# Big $\Omega$ notation
While $\mathcal{O}(n)$ is the worst case time complexity, $\Omega(n)$ is the best case time complexity. For example searching an unsorted array you can get the correct element the very first element making $\Omega(n)=1$. 

# Big $\Theta$ Notation
This is the exact time complexity of an algorithm serving as both an upper bound and lower bound. This is possible because time complexity can be a constant. So we say $f(n)=\Theta(g(n))$ if $c_1\cdot f(n)\leq g(n) \leq c_1 \cdot f(n)$. This serves as the most precise time complexity analysis 