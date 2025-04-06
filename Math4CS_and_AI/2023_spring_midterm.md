# 2022 - 2023 Math For CS & AI Midterm

## Problem 1

Suppose we toss a coin $n$ times, and the probability of getting _heads_ each time is $p$. Let $X$ represent the number of _heads_. Now, we do this process again, and get the number of _heads_ $Y$ (from the definition, $0\le X,Y\le n$). Define $V=X-Y$, $W=XY$.

1. Find $\mathbb E(V)$ and $\text{Var}(V)$.
2. Find $\mathbb E(W)$ and $\text{Var}(W)$.
3. Prove that $\mathbb P(V>\delta np)\le 2e^{-\delta^2np/12}$.

## Problem 2

Let $G_n$ be the graph whose vertices are all binary strings of length $n$, i.e., $\{0,1\}^n$. Two vertices are adjacent if and only if their strings differ in **exactly one bit**.

1. Does $G_n$ have an Eulerian circuit?  
2. Does $G_n$ have a Hamiltonian circuit?

Define a new graph $H_n$, which has the same vertices as $G_n$, but the edges are different: two vertices in $H_n$ are adjacent if and only if their strings differ in **exactly two bits**.

3. Does $H_n$ have an Eulerian circuit?  
4. Does $H_n$ have a Hamiltonian circuit?

## Problem 3

Same as 2023-2024 midterm Problem 3.