# 2023-2024 Math For CS & AI Midterm
## General Information
- **Date**: 2025-04-08

## Problem 1

1. Suppose there are $n$ different types of stamps. A collector wants to collect **all the types**. He can get a random stamps at each time. Find the expectation of the number of times he needed to achieve his goal. 
2. Suppose there is a coin, w.p. $0.8$ to get a head, and $0.2$ to get a tail. Please provide an encoding strategy for the outcome such that, when $n$ is sufficiently large, the expected number of bits to encode the result of $n$ coin flips is strictly less than $n$.
3. Define a complex function $f(z)=\dfrac{z^2+1}{z(z^3+8)}$. Find all of its singularities, and calculate
    $$\int_{|z|=1}f(z)dz.$$

## Problem 2

Let $G=(V,E)$ be a simple graph, each vertex having color of green, red, or blue (uniformly and independently). Suppose $|V|=n$, $|E|=m$. Prove the following statements:

1. The probability for the number of red vertices $\ge \dfrac{n}{2}$ is $e^{-\Omega(n)}$.
2. The probability for the number of monochrome edges $\ge \dfrac{m}{2}$ is $O(m^{-1})$.
3. If $G$ is a complete graph, then the probability in question 2 is $e^{-\Omega(\sqrt m)}$.

> **Note**. $\mathbb P\left[\#\text{monochrome edges }\ge \dfrac{m}{3-\varepsilon}\right]=e^{-\Omega(\sqrt m)}$ always hold (regardless of the structure of $G$).

## Problem 3

For a random variable $X$ taking value of non-negative integers, define its **generating function**
$$G_X(x)=\sum_{n=0}^{+\infty} \mathbb P[X=n]\cdot x^n.$$

1. If $X,Y$ are independent random variables, prove that
    $$G_{X+Y}(x)=G_X(x)G_Y(x).$$
2. If $N$ is a Poisson distribution, i.e., $\mathbb P(N=n)=\dfrac{\lambda^n}{n!}e^{-\lambda}$, prove that
    $$G_N(x)=e^{\lambda(x-1)}.$$
3. If $S=\sum_{i=1}^N X_i$, where $N,X_1,X_2,\cdots$ are pairwise independent, and all marginals of $X_i$ are as same as $X$, prove that
    $$G_S(x)=G_N(G_X(x)).$$
4. Long time ago, there is a single chicken. The number of eggs laid by each chicken after its birth follows a Poisson distribution $\mathcal P_\lambda$ ($\lambda>0$); each egg has a probability of $p$ to hatch another chicken and a probability of $1-p$ to die directly, where $0<p<1$ is a constant. We do not consider double-yolk eggs, assume that the chicken will never die after birth, and also suppose that each chicken has the ability to produce eggs. Under these assumptions, the final number of chickens is a well-defined random variable $T$. Find the generating function of $T$, $G_T(x)$, and its expectation $\mathbb E[T]$.