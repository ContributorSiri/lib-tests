## Final Exam(40pts,3hrs)
- You can use all the NPC problems whether discussed in class or in HW to do NP-reduction.
- You may need Chernoff bound: Suppose $x_1,\dots,x_n$ are independent random variables in $\{0,1,\}$and $X=x_1+\dots+x_n$.
  Let $\mu=\frac{E[X]}{n}$, then $$Prob(|X-\mu|>\epsilon)\leq 2e^{n\epsilon^2}$$ Other versions us also available, but you may find them
  equivalant in the problems.
- The total points is 40pts and each problem is 5pts. You should do **all the problems in P1~P5** and choose **3 problems from
  P6~P10**. If you choose more than 3, we will consider the three for which you get the highest scores.
- You need to prove the correctness of the algorithm you designed.

**Problem 1**  
A man wants to travel to a town $L$ miles away, and there are n rest stations $x_1,\dots,x_n$ miles from him. He can travel 
at most $d$ miles a day, and must rest at a rest station at night.

(1) Give a poly-time algorithm to find the minimum days he needed to get to the town. You can assume solution exists. (2pts)

(2) Suppose he has $k$ energy bars, and eating one of them can travel one more mile a day. Give a poly-time algorithm (on n) to find the minimum days he needed to get to the town. You can assume solution exists. (2pts)

**Problem 2**  
$A=\{a_1,\dots,a_n\}$ is a set, with each element associated a popsitive weight. $F$ is a family of subsets of $A$, and a subset $H$ of $A$
is called a Hitting Set if and only if for all $X\in F,|X \cap H|>0$. The goal is to find a hitting set with the minimum total weight.

(1) Show the problem is NP-hard. (2 pts)

(2) Give a poly-time b-approximation algorithm.($b=\max_{X \in F}|X|$)(3 pts,partial points for worse solutions, approximation solutions with expect time is allowed).

**Problem 3**  
In a directed graph $G=(V,E)$, the in-deg and out-deg are the same for any specific vertices.(Different vertices can have different deg). Proof or give a counterexample that if $x$ has $k$ pairwise edge-disjoint paths to $y$, then so do $y$ to $x$. (5 pts)

**Problem 4**  
We consider a randomized algo for vertex cover: randomly select an uncovered edge and a vertice incident to it, until all edges are covered.

(1) Prove it is not a c-approximation for some constant c in the weighted vertex cover. (1 pt)

(2) Is it a c-approximation for some constant c in the unweighted(cardinality) vertex cover? (4 pts)
    (Hint: Let $p_e$ be the probability that $e$ has been chosen. For a vertex $v$, estimate $\sum p_e$($e$ incident to $v$).)
    
**Problem 5**  
Given a convex n-gon $P$, a **chord** is an edge connecting two non-adjacent vertices of $P$, and a **triangulation** is using n-3 chords to partition $P$ to n-2 triangles.

(1) Calculate the number of different triangulations. (2.5pts)

(2) Give a poly-time algorithm to find a triangulation of minimum total chord length. (2.5pts).

**Problem 6**  
There is a coin with a bias $\delta > 0$, that is, it has prob $0.5+\delta$ to be one side than another. You need to guess this side
is tail/head.

(1) If you know $\delta$, prove you can guess with success probability >0.99 in $O(\delta^{-2})$ tosses. (2pts)

(2) If you don't know $\delta$, prove you can guess with success probability >0.99 in $O(\delta^{-2} \log \log \delta^{-1})$ tosses.(Hint:Guess $\delta$) (3pts)

**Problem 7** 
Given a directed graph $G=(V,E)$, you can delete at most $k$ edges of it. Give a poly-time algorithm to minimize $$\max_v |d^{+}(v)-d^{-}(v)|$$

**Problem 8**  
**Problem 9**  
**Problem 10**  
