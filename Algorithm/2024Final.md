## Final Exam(50pts,3hrs)
You can use any NPC problem that we mentioned in class or in the homework for your reductions.

We provide the following probablity inequalities, which may be useful later.

**Lemma1** (Markov's Inequality) If $X \ge 0$, then $Pr[X \ge t\mathbb{E}[X]] \le 1/t$.

**Lemma2** (Chebyshev's Inequality) $Pr[|X-\mathbb{E}[X]| \ge t\sqrt{Var[X]}] \le 1/t^2$.

**Lemma3** (Chernoff Bound) Let $X_i (1\le i \le n)$ be independent random variables with values in $[0,1]$. Let $X := \sum_{i=1}^{n} X_i$, and $\mu = \mathbb{E}[X]$. The following statement hold: For every $\epsilon \in (0,1)$, we have
$$Pr[|X-\mu| \ge \epsilon \mu] \le 2\exp(-\epsilon^2\mu/3).$$

If we do not mention specifically that you need to design a deterministic algorithm, you can also design a randomized algorithm. If we require a poly-time algorithm, your randomized algorithm can either run in poly-time with high probability, or run in expected polynomial time. If we require an approximation algorithm with approximation factor $\alpha$, your randomized algorithm can either return a solution that is an $\alpha$-approximation with high probability, or return a (random) solution with expected cost at most $\alpha$ times the optimum.  
In all of the following problems, you need to prove the correctness of the algorithm you design.

**Problem 1. (10 points)**
Consider the $k$-Center problem in the Euclidean plane. We are given $n$ sites $S = \{s_1, s_2, \ldots, s_n\}$ in the plane and a positive integer $k \le n$, and we want to choose a set of $k$ centers $C = \{c_1, c_2, \ldots, c_k\}$ such that the maximal distance between a site and its nearest center is as small as possible. Note that a center does not neccessarily need to be located at a site.

**(1) (5 points)** Design a polynomial-time algorithm to solve the above problem if all $n$ sites are lies on a straight line.

Now, we do not assume that the sites lie on a straight line any more. Consider the following simple local search approach. We start by arbitrarily choosing $k$ sites in the plane to be the centers $c_1, c_2, \ldots, c_k$. We now alternate the following two steps.
- Given the set of $k$ centers $\{c_1, c_2, \ldots, c_k\}$, we devide $S$ into $k$ sets: For $i = 1, 2, \ldots, k$, we define $S_i$ to be the set of all sites for which $c_i$ is closest center (ties are broken arbitrarily).
- Given the division of $S$ into $k$ sets, construct new centers as follows. For each set $S_i$, we find the smallest circle in the plane that contains all points in $S_i$, and define center $c_i$ to be the center of this circle. If $S_i$ is empty in this step, the position of $c_i$ does not change.

If the above steps cause the covering radius to strictly decrease, then we perform another iteration; otherwise the algorithm stops.

**(2) (2 points)** Prove that this local search algorithm eventually terminates.

**(3) (3 points)** Consider the following statement. There is an absolute constant $b > 1$ (independent of the particular input instance), so when the local search algorithm terminates, the covering radius of its solution is at most $b$ times the optimal covering radius. Decide whether you think this statement is true or false, and give a proof of either the statement or its negation.

**Problem 2. (5 points)**
Consider a set of mobile computing clients in a certain town that each need to be connected to one of several possible base stations. The position of each of these clients and base stations is specified by its $(x, y)$ coordinates in the plane.  
For each client, we wish to connect it to exactly one of the base stations. Our choice of connections is constrained by the following ways:
- There is a range parameter $r$: a client can only be connected to a base station that is within distance $r$;
- There is also a load parameter $L$: no more than $L$ clients can be connected to any single base station.

Design a polynomial-time algorithm to decide whether every client can be connected simultaneously to a base station, subject to the range and load conditions above.

**Problem 3. (5 points)**
We are given a tree with $n$ nodes, where each node has a positive integer value and each edge has a positive length. The score for a path between two nodes $u$ and $v$ is defined as the sum of the values of all nodes along the simple path from $u$ to $v$, minus the total length of the edges on this path. Design an $O(n)$-time algorithm to find two distinct nodes $u$ and $v$ such that the score of the path between them is maximized.

**Problem 4. (5 points)**
We are given a simple undirected graph $G = (V, E)$. We wish to find a permutation $(v_1, v_2, \ldots, v_n)$ of all vertices in $V$ such that
$$|E\cap\{v_1v_2, v_2v_3, \ldots, v_{n-1}v_n, v_nv_1\}|$$
is as large as possible.

**(1) (2 points)** Formulate the decision version of this problem and prove that it is NP-Complete.

**(2) (3 points)** Design a polynomial-time approximation algorithm for this problem with constant approximation ratio.

**Problem 5. (5 points)**
We are given a simple undirected graph $G = (V, E)$, where $|V| = n$. Bob wishes to approximate $|E|$ without reading the whole input. In particular, Bob designs the following algorithm to approximate $|E|$: first, Bob samples $k$ ($k \ge 2$) i.i.d. vertices $u_1, u_2, \ldots, u_k$ uniformly from $V$. Then, Bob computes
$$S := \# \{(i, j): 1 \le i < j \le k, u_iu_j \in E\}.$$

**(1) (2.5 points)** Find the formula for $\mathbb{E}[S]$. (For a fixed $G$.) The answer should be in the form of $c_{n,k} \cdot |E|$, where $c_{n,k}$ depends only on $n, k$.

**(2) (2.5 points)** Show that $S/c_{n,k}$ gives a good approximation of $|E|$. Specifically, prove that for $\epsilon \in (0, 1)$,
$$Pr[|S/c_{n,k} - |E|| \le \epsilon\cdot|E|] \ge 1 - O(k)\cdot\exp\left(-\Omega\left(\epsilon^2\cdot\frac{k|E|}{n^2}\right)\right).$$

**Please answer 4 problems from the following 5 problems. If you answer more than 4 problems, we will give you scores according to the 4 problems for which you get the highest scores.**

**Problem 6. (5 points)**
We are given $n$ lines in the Euclidean plane. We assume no lines are vertical and no three lines pass the same point. We say a line is uppermost at some $x$-coordinate $x_0$ if its $y$-coordinate at $x_0$ is larger than the $y$-coordinates of all other lines at $x_0$. We say a line is visible if it is uppermost at some $x$-coordinate — intuitively, some portion of the line can be seen if you look down from $y = \infty$. Give an algorithm that returns all visible lines in $O(n\log n)$ time.

**Problem 7. (5 points)**
Design a polynomial-time algorithm for the following version of subset sum: we are given a positive integer $n$ and $n$ integers $a_1, a_2, \ldots, a_n$, where each $a_i$ is given in the form of $q_i \cdot 2^{b_i}$. Here $q_i \in \{-n, -n + 1, \ldots, n\}$ and $b_i \in \{0,1,\ldots,n\}$. Our goal is to decide whether there is a non-empty subset $I \subseteq [n]$ such that $\sum_{i \in I} a_i = 0$.

**Problem 8. (5 points)**
Given a permutation $P$ of $\{1,2,\ldots,n\}$. We say $P_i$ is a right-to-left maxima iff $P_i > P_j$ for all $j > i$. Now, suppose $P$ is a random permutation (chosen from all $n!$ permutation uniformly at random). Try to figure out the expectation of the number of right-to-left maxima of $P$. (It is enough to find out the right asymptotic order, i.e., in $\Theta()$ notation).  
Here is an example. If $n = 9$ and $P = \{591826473\}$, the number of right-to-left maxima is 4. (They are $\{9873\}$.)

**Problem 9. (5 points)**
Consider the vertex cover problem: we are given an undirected graph $G(V, E)$. A vertex cover is a subset $S$ of vertices such that all edges are covered by $S$ (i.e., for every $(u, v) \in E$, either $u \in S$ or $v \in S$). We would like to find a vertex cover of size as small as possible.  
Now, we suppose the graph $G$ is $k$-colorable (i.e., each vertex can be colored by a color from $[k]$ such that any two adjacent vertices are colored differently). Suppose such a $k$-coloring of the graph $G$ is provided to you as well. Design a polynomial-time approximation algorithm that can achieve an approximation factor of $2 - 2/k$.  
Note that for bipartite graphs, we have $k = 2$, and the algorithm can find the optimal answer.  
(Hint: use the LP approach. First write down the LP relaxation for vertex cover, and show that the optimal fractional solution $\{x_i\}$ for the LP relaxation is half-integral, i.e., $x_i \in \{0, 1/2, 1\}$ for each $i$. Then, use the half-integrality to derive an approximation algorithm for vertex cover. If you do not know how to prove half-integrality, you can use it directly and you may get partial credit if other steps are correct).

**Problem 10. (5 points)**
We are given $n$ points $A_1, A_2, \ldots, A_n \in \mathbb{R}^2$. Our goal is to find a set of pairwise disjoint unit disks, where each disk should be centered at some point $A_i$, that cover as many points as possible. Design a polynomial-time approximation algorithm for the problem. You will get full credit if you can get a PTAS (polynomial-time approximation scheme), and partial credit for a constant approximation factor.