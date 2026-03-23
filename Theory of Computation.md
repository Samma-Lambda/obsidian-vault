---
tags:
  - Computer
---
# Languages

Every language is build from an alphabet(A finite set of symbols) $\Sigma$ , Strings(finite sequences of elements from the alphabet) including the empty string $\epsilon$.

- Any string has a length $|001|=3$, $|\epsilon|=0$
- You can concatenate strings $101+00=10100$

A language is any set of strings from an alphabet. Every alphabet has the empty language $\emptyset$ and the Kleene closure(all possible finite strings) $\Sigma ^{*}$


# Types of Automata 
## Deterministic Finite Automaton(DFA)

This is an abstract machine which accepts or reject strings. It has finitely many states and transitions between them to do this, it always reads the text one letter at a time

- An example would be a DFA to accept even strings and reject all others on the alphabet $\{a\}$

Its usually represented using a state diagram

![[Pasted image 20251227123407.png|300]]

- There are things that a DFA can’t do like check if something is prime due to its finite memory
- It also can’t recognize the string $\{a^nb^n|n\in \mathbb{N}\}$

Formally in mathematical terms a DFA is a tuple $(Q,\Sigma,\delta,q_0, F)$ where

- $Q$ is a finite set (the states)
- $\Sigma$ is a finite set (the alphabet)
- $\delta$ is a function $Q\times \Sigma \rightarrow Q$(the transition between states)
- $q_0\in Q$(the starting state)
- $F\subseteq Q$(set of accepting states )

Additionally $L(M)$ is the language of all accepted strings from a DFA. Finally often its more convenient for to use $\delta ^*:Q\times \Sigma \rightarrow Q$ as a function that takes in an string rather than individual letters


## NFA(Non-deterministic Finite Automata)

These are DFA’s with more capacities. They can do the following as well

- Have states without arrows for a specific letter leading to the state “falling off”
- epsilon transitions, these transitions are instantly done
- Splitting by having two different paths from the same state
![[Pasted image 20251227123926.png]]

To formally define a NFA it has the same five ingredients but some are modified

- $Q$ the set of states
- $\Sigma$ the alphabet
- $\delta$ the transition function $\delta :Q\cup\{\epsilon\}\rightarrow P(Q)$
- $q_0$ is the starting state
- $F\subseteq Q$ is the set of accepting states

It accepts if any of the accept states are active at the end.
To formally define a NFA it has the same five ingredients but some are modified

- $Q$ the set of states
- $\Sigma$ the alphabet
- $\delta$ the transition function $\delta :Q\cup\{\epsilon\}\rightarrow P(Q)$
- $q_0$ is the starting state
- $F\subseteq Q$ is the set of accepting states

It accepts if any of the accept states are active at the end.

Every NFA can be written as a DFA using the subset construction
![[Pasted image 20251227125504.png|500]]
![[Pasted image 20251227125527.png|650]]


# Language Derivatives and the Pumping Lemma
For a language L we denote its derivative $\frac{d}{da}L$, this takes the language and finds only the elements that start with a. IE $L=\{ab^{3n}|n\in\mathbb{N}\}$ would imply $\frac{d}{da}L=\{b^{3n}|n\in \mathbb{N}\}$.
The pumping lemma is a way to prove that something can't be done with a NFA(and thus a DFA) it states that if a language has infinite distinct derivatives than it can't be classified using a NFA . 