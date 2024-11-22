# Midterm Exam 2024

- **Time**: 2024.11.21, 19:20 - 21:50, $150$ min.
- **Total Score**: $120$, but clip to $100$ when exceeding $100$.
- You can only bring a double-face A4 cheatsheet.

_NOTE._ This midterm exam worth $0\%$ to the final grade. This exam only serves for the mock test of the final exam.

**For every algorithm you write, you need to prove its correctness. Providing a correct algorithm without proof will only gives you partial score.**

## Problem 1 ($10$ pts)

Write down the **full pseudo-code** to solve the following problem:
> Given a set of $n$ intervals. Find a subset $S$, such that the intervals in $S$ do not intersect and, $|S|$ is maximized.

The algorithm **must** run in $O(n\log n)$ time.

## Problem 2 ($15$ pts)

Design an algorithm to solve the following problem:
> Given a tree $T$ having $n$ nodes. Find a vertex $v\in T$ such that, if we delete $v$ and all the edges adjacent to $v$ from $T$, every connected component of the resulting forest has size $\le \dfrac{n}{2}$.

Your algorithm **must** run in $O(n)$ time. You also need to show why such $v$ exists.

## Problem 3 ($15$ pts)

Design an algorithm to solve the following problem:
> Given a sorted array of positive integers $(a_1\le a_2\le \cdots\le a_n)$ (they are already in the memory, so we don't need to read them), such that $a_n\le m$. Find $b_1,b_2,\cdots,b_m$ such that, for each $1\le j\le m$, $j$ appears $b_j$ times in array $a$.

Your algorithm **must** run in $O(m\log n)$ time.

## Problem 4 ($15$ pts)

The description of the $\mathsf{Max2Lin}$ problem is as follows:
> $n,m,k$ are positive integers. There $n$ variables $x_1,x_2,\cdots,x_n\in \mathbb{F}_2$, and $m$ equations in $\mathbb{F}_2$. Each equation is either in form $x_i=\alpha$ or $x_{i_1}+x_{i_2}=\beta$, where $i,i_1,i_2\in \{1,2,\cdots,n\}$ and $\alpha,\beta\in \mathbb{F}_2$. Determine whether there is a $(x_1,x_2,\cdots,x_n)\in \mathbb{F}_2^n$ such that **at least** $k$ equations are satisfied.

Prove that $\mathsf{Max2Lin}\in \mathsf{NP}$-$\mathsf{complete}$.

## Problem 5 ($15$ pts)

Design a poly-time **constant-ratio** approximation algorithm for the following problem:
> Given a undirected graph $G$, each vertex $v$ having degree $\le 10$ and a weight $w_v\ge 0$. Find an **independent set** $I\subseteq V(G)$ such that $\sum\limits_{v\in I} w_v$ is maximized.

In other words, your algorithm must deterministically find an independent set $I'$, such that
$$\sum\limits_{v\in I'} w_v\ge C\cdot \sum\limits_{v\in I^\star} w_v,$$
where $I^\star$ is the optimal solution.

## Problem 6 ($15$ pts)

Alice and Bob play a game on a pyramid of integers: the pyramid has $n$ levels, level $i$ ($1\le i\le n$) having $i$ integers. Alice and Bob both start from the only number at level $1$; in each step, they need to travel to the next level by going to an adjacent number (can be the left or the right one). Finally, after $n-1$ steps, they need to reach the same number at level $n$. They count their score by adding every number they had visited (if both Alice and Bob visited a number, only count for once!). They want to design a strategy to maximize their score.

For instance, the following graph represents a case when $n=4$. In fact, their best strategy is: $1\to 2\to 5\to 9$ for Alice, $1\to 3\to 6\to 9$ for Bob. Then, their score will be
$$1+2+3+5+6+9=26.$$

$$
1\\
2\ \ 3\\
4\ \ 5\ \ 6\\
7\ \ 8\ \ 9\ \ 10
$$

Design a poly-time algorithm to solve this problem.

## Problem 7 ($15$ pts)

Suppose $b$ is a fixed positive integer. Find a poly-time **$b$-approximation** algorithm for the following problem:
> $A$ is a set of size $n$, each element $x\in A$ has a weight $w_x\ge 0$. Given $m$ subsets $B_1,\cdots,B_m\subseteq A$, such that for each $1\le i\le m$, $|B_i|\le b$. Call $H\subseteq A$ a **hitting set**, if for each $1\le i\le m$, $B_i\cap H\neq \emptyset$. Find a hitting set $H^\star$ such that $\sum\limits_{x\in H^\star} w_x$ is minimized.

## Problem 8 ($20$ pts)

Suppose you want to trade a kind of stock in $n$ days. In day $i$ ($1\le i\le n$), the price of this stock is $p_i>0$. In each day, you can either choose to buy some stocks, sell some stocks you have already bought in previous days, or do nothing. However, every stock you buy will cost you another $c_b>0$ money; every stock you sell will cost you another $c_s>0$ money. You need to maximize your profit after $n$ days.

**(1, $10$ pts)** Suppose now you have **infinite** amount of money, and you can only buy / sell **at most one** stock in each day. Design an algorithm that runs in $O(n)$ time.

**(2, $10$ pts)** You have $M$ money initially, and you **cannot borrow money** (that means, you can only buy a stock if you have enough money). And the amount of stocks you buy in each day is **unlimited**. Design an algorithm that runs in $O(n)$ time.