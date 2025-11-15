# Midterm(150min,30pts)
- The total time of this test is 150min, and total score is 30 pts.
- Some of the questions are incomplete(can't remember well).
- Some of the problems may have ambiguity(e.g. in P7,it doesn't say whether $t \ge 0$, or whether there is a path from $s$ to $t$ in P5), if this doesn't significantly
  affect the difficulty of the problem, either will be given full score.
- If not stated, we assume that real number addition/multiplication/division can be done in $O(1)$ time.
- The average score is 24 and the median score is 25. Highest score: 30 (17 students), Lowest score: 14. (Before score re-checking).

1.(3pts)

Sort some functions in asymptotic order.

2.(3pts)

Given $L$ a set of strings. Define the **concatenation** of $L$ be $s_1\dots s_n(s_i\in L)$(allow $s_i=s_j$). For each two letter $u,v$, there's a $dist(u,v) \ge0 $, and equality holds iff $u=v$. Also, "space" is considered to be a special letter. Define the distance of two strings $U,V$ to be $\sum dist(U_i,V_i)$(If they are not of the same length, add spaces to the shorter one).

Given a string $S$, find a poly-time algorithm to minimize the distance of $S^0$ and $L^0$, where $S^0$ is $S$ adding some spaces in arbitrary position, and $L^0$ be a concatenation of $L$.

3.(4pts) 

We are given n intervals $I_i=[a_i,b_i]$, and positive real numbers $\delta, U$. Give an
algorithm to determine whether we can shift those intervals by at most $\delta$( we can shift different length for
different intervals), to make the union of them covers $[0,U]$.

**Note**: Actually, the purpose of this problem is to ask for a poly-time algorithm. However, because
of some special reason, expo-time algorithms was also given full mark.
 
4.(3pts)

5.(3pts)
Given a directed graph $G=(V,E)$, with a weight on each edge. Assume all cycles are of positive length. Give a poly-time algorithm to calculate
the number of shortest paths from $s$ to $t$.

6.(4pts)

7.(3pts)

Consider the generalized version of minimum spanning tree problem:Given a graph $G=(V,E)$, and the weight of each edge $e$ is a quadratic function $w_e(t)=a_et^2+b_et+c_e(a_e>0)$.  
Give an poly-time algorithm to find a minimum spanning tree among all time, that is, $\min_{t,T} \sum_{e\in T} w_e(t)$, where $T$ is a spanning tree of $G$.

8.(3pts)

There are n empty bins. An **operation** means randomly put a ball to a bin, and if this bin already has at least one ball, we take the ball out and throw again. (We throw at most 2 times, not recursively do that). Calculate the expectation number of operations needed to make all bins non-empty. Give your answer in simplest form, or give the asymptotic order of it.

9.(4pts)

Consider the Supplier Problem: Given a graph $G=(V,E)$, with a weight on each edge. where $V$ is partitioned into two parts $C$(Customers) and $S$(Suppliers). The goal is to find $k$(fixed) points in $S$, called $s_1,\dots,s_k$ ,to minimize $T=\max_{c\in C} \min_{1\le i \le k} \text{dist}(s_i,c)$.

(1) Give a poly-time 3-approximation algorithm to calculate $T_{min}$.

(2) Show that it is NP-Complete to give a $(3-\epsilon)$-approximation algorithm.


