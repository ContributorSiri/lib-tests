## Theory of Computation Midterm

**Acknowledgement:** This file is written by 陈宇轩.

### General Information
- **Date:** 2025/04/08, totally closed book, 13:30-15:30.
- **Choose 6 problems to answer. Rice's Theorem cannot be used directly.**

### Problem 1
Give a DFA, NFA, or regular expression for the following language, and explain your idea.
$$L=\{w \in \{0,1\}^* \mid w \text{ contains at least two } 0 \\
\text{ symbols in every consecutive four symbols}\}$$

### Problem 2
1. Prove that $L=\{a^nb^na^n \mid n \ge 0\}$ is not context-free.
2. Provide a CFG or PDA for $\overline{L}$ (the complement of $L$), and explain your idea.

### Problem 3
Determine whether the following languages are decidable: 
1. $L=\{M \mid M \text{ is a Turing machine that runs more than } 2^{|w|} \text{ steps on some input } w\}$
2. $L=\{M \mid M \text{ is a Turing machine that runs more than } 2^n \text{ steps on some input}\}$, where $n$ is the number of states of $M$.

### Problem 4
For arbitrary languages $A$ and $B$, prove that there exists a language $L$ such that $A \le_T L$ and $B \le_T L$.

### Problem 5
Let all prime numbers be ordered increasingly as $p_1, p_2, p_3, \cdots$. Prove that there exists a constant $c$ such that $p_i \le c \cdot i \cdot (\log i)^2$. *(Hint: Recall that there exist incompressible strings for every length.)*

### Problem 6
Show that there does not exist a recursive function $f$ such that for every Turing machine $M$ that always halts and whose language is finite, $f(\langle M \rangle)$ is an upper bound on the size of $L(M)$. *(Hint: Use Kleene's Theorem.)*

### Problem 7
In class, we discussed a randomized approach to establish a lower bound for the partial sum problem by constructing difficult queries on average. For a permutation $\pi$ of $[n]$, the queries are $\text{Update}(\pi(k), \Delta_k)$ and $\text{Sum}(\pi(k))$ for $i$ from $1$ to $n$.

1. Recall the definition of $\text{IL}(t_0, t_1, t_2)$ for $t_0 < t_1 < t_2$ such that $t_1 - t_0 = t_2 - t_1$: When we sort $\pi(t_0), \cdots, \pi(t_2)$ in increasing order, $\text{IL}(t_0, t_1, t_2)$ represents the number of consecutive pairs $\pi(j_1), \pi(j_2)$ where $j_1 < t_1$ and $j_2 > t_1$. Prove that $\mathbb{E}_\pi[\text{IL}(t_0, t_1, t_2)] = \Omega(t_2 - t_0)$.
2. Now, we derandomize the queries. For a permutation $\pi'$ of $1, 2, \cdots, k$, we construct a new permutation $\pi$ of $1, 2, \cdots, 2k$ as follows:
   $$\langle 2\pi(1) - 1, 2\pi(2) - 1, \cdots, 2\pi(k) - 1, 2\pi(1), 2\pi(2), \cdots, 2\pi(k) \rangle.$$
   Prove that $\text{IL}(0, k, 2k) = \Omega(k)$.
3. Using the above method, generate a permutation $\pi$ for $1, 2, \cdots, 2^i = n$. Prove that
   $$\sum_v \text{IL}(v) = \Omega(n \log n).$$
