# Algorithm 2025 Fall Midterm
## General Information
- **Date**: 2025.11.10
- **Time**: 9:50 - 12:20
- A single A4 cheatsheet is accepted.
- **Total points**: $30$.

##  Problem 1 (3 pts)
Compare the magnitudes of the following asymptotic bounds: 
$\sqrt{n}^{\log(n)}$, $2^{2^{\log^{*}(n)}}$, $\binom{n}{\log\log(n)}$, $n^{\log\log(n)}$, $2^{(\log\log(n))^2}$
where **log\* n** denotes the number of times the logarithm function must be applied to **n** to reduce it to a constant.

##  Problem 2 (4 pts)
(1)(2pts) Use a priority queue to provide the pseudocode of the Dijkstra's algorithm. You may assume that the priority queue has already been implemented for you, but you need to specify the exact names of the operations used on the priority queue.

(2)(2pts) Give a counterexample showing that Dijkstra's algorithm cannot correctly compute the shortest paths in a graph that has negative edge weights but no negative-weight cycles.

##  Problem 3 (3 pts) 
Consider the Supplier Problem: Given a graph $G=(V,E)$, with a weight on each edge and the weight satisfies the triangular inequality (which makes the weight a metric space). where $V$ is partitioned into two parts $C$(Customers) and $S$(Suppliers). The goal is to find $k$(fixed) points in $S$, called $s_1,\dots,s_k$ ,to minimize $T=\max_{c\in C} \min_{1\le i \le k} dis(s_i,c)$.
Show that it is NP-Complete to give a $(3-\epsilon)$-approximation algorithm.

##  Problem 4 (3 pts)
There are $n$ empty bins. An **operation** means randomly put a ball to a bin, and if this bin already has at least one ball, we take the ball out and throw again. (We throw at most 2 times, not recursively do that). Calculate the expectation number of operations needed to make all bins non-empty. Give your answer in simplest form, or give the asymptotic order of it.

##  Problem 5 (3 pts)
There are 10 sorted arrays and their length are all $n$, give a algorithm that runs in time $O(\log(n))$ to find the $k$th largest number in these arrays.

##  Problem 6 (4 pts)
Consider a complete binary tree \(T\) with \(n\) leaves.  
We define a tree metric on these \(n\) leaves as follows:  
For every node \(v\) in \(T\), associate a value \(L(v) \ge 0\).  
Furthermore, whenever node \(u\) is the parent of node \(v\), we require \(L(v) \ge L(u)\).

For any two leaves \(x, y\), define the tree metric: $d_T(x, y) = L(\mathrm{LCA}(x, y))$,where \(\mathrm{LCA}(x,y)\) denotes the lowest common ancestor of \(x\) and \(y\).

(1)(1pts) Prove that \(d_T\) is indeed a metric.

(2)(3pts) A tree metric \(d_T\) is called good if for all \(x, y\),

   \[
   d_T(x, y) \le d(x, y).
   \]

   A tree metric is **maximal** if for every other tree metric \(d_T'\),

   \[
   d_T(x, y) \ge d_T'(x, y).
   \]
Give a polynomial-time algorithm to compute such a tree metric  
   (distance-preserving construction).  

All symbols refer to complete binary tree structures and all tree metrics \(L\) defined on this structure that satisfy the maximal property.

##  Problem 7 (5 pts)
(1)(2pts) 
Given $L$ a set of strings. Define the **concatenation** of $L$ be $s_1\dots s_n(s_i\in L)$(allow $s_i=s_j$). For each two letter $u,v$, there's a $dist(u,v) \ge0 $, and equality holds iff $u=v$. Also, "space" is considered to be a special letter. Define the distance of two strings $U,V$ to be $\sum dist(U_i,V_i)$.
Given two strings \(s\) and \(t\), give a polynomial-time algorithm to compute the shortest distance between \(s\) and \(t\), as well as their corresponding optimal alignment.  (Optimal cost and optimal alignment)
(2)(3pts)
Given a string $S$, find a poly-time algorithm to minimize the distance of $S^0$ and $L^0$, where $S^0$ is $S$ adding some spaces in arbitrary position, and $L^0$ be a concatenation of $L$.

##  Problem 8 (3 pts) 
Prove that the following decision version is NP-Complete:

\[
\text{Given } \min_{x_1, x_2, \dots, x_n \in \{0,1\}} P(x_1, x_2, \dots, x_n),
\]

where \(P\) is a multivariate polynomial in \(x_1, x_2, \dots, x_n\).

##  Problem 9 (2 pts)
Let a \(d\)-dimensional vector \((x_1, x_2, \dots, x_d)\) represent a point \(X\).  
We say that \(X\) contains \(Y = (y_1, \dots, y_d)\) if there exists a permutation \(\pi\) of \([d]\) such that  

\[
x_{\pi(i)} \le y_i \quad \text{for all } 1 \le i \le d.
\]

(1).(1pts) Give a polynomial-time algorithm to determine whether \(X\) contains \(Y\).

(2).(1pts) Given \(n\) \(d\)-dimensional vectors \(X_1, X_2, \dots, X_n\),  
   give a polynomial-time algorithm to determine whether there exist  
   distinct indices \(i_1, \dots, i_t \in [n]\) such that for every \(1 \le j \le t-1\),  
   \(X_{i_j}\) contains \(X_{i_{j+1}}\).  
   Please express the time complexity of your algorithm using Big-O notation.





