# 2023-2024 Spring Final

## General Information
- **Date**: 2024-06-11
- **Time**: 10:00-12:40
- Open notes, but can't bring books
- May answer in Chinese

## Problem 1 (20 pts) Linear Algebra

1. Give a $2\times 2$ matrix whose singular values are different from its eigenvalues.
2. For a $n\times n$ matrix $M$, is its left eigenvalues also equal to its right eigenvalues? Prove or give a counterexample. (The left eigenvalues are defined as the eigenvalues of the left eigenvectors.)

## Problem 2 (15 pts) TV bound

There is two distributions $\mu,\nu$ on a finite state space $\Omega$. There is a function $f$ from $\Omega$ to another $\Lambda$, which is another finite state space.

Now, assume that there is some distribution $\mu',\nu'$ on $\Lambda$, such that for any $B\subseteq \Lambda$,

$$
\mu(f^{-1}(B))=\mu'(B),\quad \nu(f^{-1}(B))=\nu'(B).
$$

Prove that

$$
||\mu-\nu||_{TV}\geq ||\mu'-\nu'||_{TV}.
$$

## Problem 3 (25 pts) Sketching

**NOTE. This problem description is not the one given on the exam. It is a simplified version.**

**This is an algorithm design problem.** Please design an algorithm to solve the following problem. Given positive integers $T,n$.

- **INPUT:** at time $1\le t\le T$, receive a vector $\mathbf{x}_t\in \{0,1\}^n$ (cannot be overwritten). Define $\bar{\mathbf{x}}_t = \sum\limits_{i=1}^t \mathbf{x}_i$.
- **QUERY**: at any time $t$, receive an integer $1\le i\le n$, and the algorithm outputs a number $y$. You must ensure that
$$|y-\bar{\mathbf{x}}_t^i|\le \dfrac{1}{10}\cdot ||\bar{\mathbf{x}}_t||_1$$
with probability at least $0.9$. Here, $\bar{\mathbf{x}}_t^i$ denotes the $i$-th element of $\bar{\mathbf{x}}_t$, and $||\cdot||_1$ denotes the $L_1$ norm.

Additionally, the algorithm should only use no more than $O((\log nT)^2)$ space.

**Hint**: 1. The problem actually asks you to compress the $O(n)$ information of $\bar{\mathbf{x}}_t$ without losing too much information. What can JL lemma help?\
2. The memory of storing random vectors can be ignored, since we can just store the random seed and generate the same random vectors when needed.


## Problem 4 (40 pts) Lower Bound of Mixing Time

Consider a Markov chain on a one-dimensional lattice with $n$ vertices. The transition probability is defined as follows:

$$
P(x\to y)=\begin{cases}\frac{1}{2}&,x=y\\\frac{1}{4}&,|x-y|=1(\text{mod } n)\\ 0&,\text{otherwise}\end{cases}
$$

1. Suppose that now there is a constant $\alpha$, such that for any $t= O(n^\alpha)$, we have

$$
P^t\left(1\to \frac{n}{2}+1\right) \le \frac{1}{2n}.
$$

You may assume that $n$ is an odd number.

2. Show that the mixing time of this Markov chain is at least $\Omega(n^2)$.