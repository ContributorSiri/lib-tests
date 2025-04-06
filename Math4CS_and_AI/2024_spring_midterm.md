# 2023-2024 Math For CS & AI Midterm
## General Information
- **Date**: 2024-04-16
- **Time**: 10:00-12:40
- Open book, open notes
- May answer in Chinese

## Problem 1 (30 pts)
Consider a graph $G$ with 8 vertices $\{1,2,\cdots,8\}$ and 12 edges 
$$E=\{\{1,2\},\{2,3\},\{3,4\},\{4,1\}\}\cup \{\{5,6\},\{6,7\},\{7,8\},\{8,5\}\}\\
\cup \{\{1,5\},\{2,6\},\{3,7\},\{4,8\}\}$$

1. [10 pts] Find the number of spanning tree of $G$ using the matrix tree theorem. You should write your answer in the format of determinant, without calculating the value.
2. [10 pts] Give a Pfaffian orientation for $G$.
3. [10 pts] Use the results in (b) and the Kastelyen theorem discussed in the class to find the number of perfect matchings of $G$. You should write your answer in the format of determinant, without calculating the value.

**Remarks.** In 3, only giving a numerical value of the perfect matching using other methods will not be awarded any points.

## Problem 2 (30 pts)
Consider a game of $n$ soldiers $P_1,P_2,\cdots,P_n$. In the first round, $P_1$ will fight with $P_2$. Let $P_{i_1}$ be the winner. In the second round, $P_{i_1}$ will fight with $P_3$. Let $P_{i_2}$ be the winner. In the $k$-th round, $P_{i_{k-1}}$ will fight with $P_{k+1}$. Let $P_{i_k}$ be the winner. The game will end when there is only one soldier $P_{i_{n-1}}$ left.

We assume that the "ability" of the soldiers are *transitive*, i.e., if $P_i$ is stronger than $P_j$ and $P_j$ is stronger than $P_k$, then $P_i$ is stronger than $P_k$.

Define that the round $j$ is **upset**, if $P_{j+1}$ wins the previous winner $P_{i_{j-1}}$. Let $X_n$ be the random variable corresponding to the number of upsets in the game.

1. [5 pts] Find the expectation of $X_n$.
2. [5 pts] Find the variance of $X_n$.
3. [5 pts] Prove that
$$\Pr\{X_n>10\log _2 n+20\}<\frac{1}{n}.$$
4. [5 pts] Define $Z_n=2^{X_n}$. Find the expectation of $Z_n$.
5. [5 pts] Find the variance of $Z_n$.
6. [5 pts] Suppose that someone comes late and can only see the last $\frac{n}{2}$ rounds. Let the number of upsets he can see be $u_n$. Find 
$$
\lim_{n\to \infty}u_n.
$$

## Problem 3 (40 pts)

Let  $n \geq m>0$ be integers. A binary string  $u=u_{1} u_{2} \cdots u_{n}$ is said to contain  $v=v_{1} v_{2} \cdots v_{m}$ as a substring if there exists an integer  $i$ (where $0 < i \le n-m+1$ ) such that  $u_{i}=v_{1}, u_{i+1}=v_{2}, \cdots, u_{i+m-1}=v_{m}$ . For example, 110100 contains 101 as a substring (with  $i=2$  ), while the string 001100 does not contain 101 as a substring.

Let $a_{n}$ denote the number of binary strings of length $n$ that do not contain 101 as a substring. Clearly,  $a_{1}=2, a_{2}=4$. Let  $A(x)=\sum_{n \geq 1} a_{n} x^{n}$ .
1. [10 pts] Determine the value of $a_{5}, a_{6}$ .
2. [15 pts] Derive an explicit closed-form formula for $A(x)$.
3. [15 pts] Let  $1<\lambda<2$ be the unique value satisfying  $\lambda^{3 / 2}=1+\sqrt{\lambda}$ . Derive an explicit rational function  $f(\lambda)$ such that
$$\lim_{n \rightarrow \infty} \frac{a_{n}}{\lambda^{n} f(\lambda)}=1.$$

**Remarks** For  $n=3$ , there is only one binary string of length  $n$ that contains 101 as a substring (ie, 101). For $n=4$ , there are exactly four binary strings of length  $n$  that contain 101 as a substring (ie,  0101,1010,1011,1101) . Thus,  $a_{3}=2^{3}-1=7, a_{4}=2^{4}-4=12$.
