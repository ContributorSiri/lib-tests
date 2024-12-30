# AI Principles and Techniques 2024 Fall Midterm

## General Information

- **Date**: 2024.12.23
- **Time**: 19:20 - 21:20
- One A4 cheat sheet is allowed. Electronic devices are not acceptable, including, but not limited to phones, laptops, digital cameras, etc.
- **Total points**: $100$.
- Answer those that you believe you can solve easily first!

## 1 Search

### 1.1 Alpha-Beta Search (8 pts)

Consider alpha-beta search on the adversarial game tree shown below. The max player moves
first. If the node value variable $x=11$, then what is the minmax value of the root node? When
will the branch $l$ be pruned? Directly write down your answers.

### 1.2 $A^\star$ Tree Search (12 pts)

Consider the $A^\star$ tree search algorithm with limited fringe (priority queue) size $M$. In all cases, $g(n)$ is the cost of the path from the start node to $n$, $h(n)$ is an admissible heuristic, $h^\star(n)$ is the true cost from $n$ to the nearest goal. Assume all costs are positive. The priority is still maintained by $g+h$, but the fringe only maintains the smallest $M$ nodes and discards larger nodes. (You can choose how to break ties by yourself)

**Question (a)** (4 pts) If $h(n)=h^\star (n)$, what is the least fringe size $M$ required to find an optimal path?

**Question (b)** (8 pts) Assume we have $\min_{u\neq v} |(g(u)+h(u))-(g(v)+h(v))|=\varepsilon>0$. The starting node is $s$. Do the followings preserve optimality? If not, give a counterexample; if yes, prove your answer.

1. $M=\left\lceil \dfrac{h(s)}{\varepsilon}\right\rceil$;

2. $M=\left\lceil \dfrac{h^\star(s)}{\varepsilon}\right\rceil$;

3. $h(n)\ge h^\star(n)-d$ where $d\ge 0$; $M=\left[\dfrac{d}{\varepsilon}\right]+1$.

## 2 MDP and Reinforcement Learning

### 2.1 Conceptual Short Questions (14 pts)

**Question (a)** (5 pts) We had made several assumptions in MDPs, including first-order Markovian dynamics, state-dependent reward, stationary dynamics and full observability. Explain the definition of first-order Markovian dynamics assumption and full observability assumption.
**Question (b)** (5 pts) Consider the grid world, where the agent can move north, south, east, west to adjacent grid, and stays still when hitting a wall. The transitions are deterministic. The figure shows the original reward function. Discounting factor $\gamma=0.8$. Perform value iteration of $2$ iterations on the grid world shown in the figure. Directly write down the values after each iteration.

$$
\begin{array}{|c|c|c|}
\hline
\text{wall} & -1 &\text{wall} \\
\hline
 0& 0 & 0 \\
\hline
\text{wall} & 100 & \text{wall} \\
\hline
\end{array}
$$

**Question (c)** (4 pts) What is the benefit of using a frozen target Q-Net when training a DQN? Answer in less than $2$ sentences.

### 2.2 Preference based Reinforcement Learning (15 pts)

Sometimes it is difficult to directly get reward for each state-action transition, but preference can be applied to reconstruct the reward. Dataset $\mathcal{D}=\{(\tau_1,\tau_2),\cdots,(\tau_{2n-1},\tau_{2n})\}$ is a collection of trajectory pairs. Trajectory $\tau=(s_0,a_0)\to (s_1,a_1)\to \cdots \to (s_n,a_n)$ is a sequence of state-action pairs. Preference is denoted as $\tau_1\succ \tau_2$, meaning $\tau_1$ is preferred over $\tau_2$.

#### 2.2.1 Reward Reconstruction
Using the Bradley-Terry model, we can associate preferences with rewards. The probability of $\tau_1$ is preferred over $\tau_2$ is defined as

$$P(\tau_1\succ \tau_2)=\dfrac{e^{R(\tau_1)}}{e^{R(\tau_1)}+e^{R(\tau_2)}},$$
where $R(\tau)=\sum_{(s_t,a_t)\sim \tau} \gamma^t r(s_t,a_t)$ is the cumulative reward of the trajectory. The reward function is non-negative, i.e. $r(s,a)\ge 0$ for each pair $(s,a)$. Write $\tau_1\succ \tau_2$, if $P(\tau_1\succ \tau_2)>0.5$.

**Question (a)** (4 pts) Prove the properties:

- If $P(\tau_1\succ \tau_2)>0.5$, $P(\tau_2\succ \tau_3)>0.5$, then $P(\tau_1\succ \tau_3)>0.5$.
- $P(\tau_1\succ \tau_3)\le P(\tau_1\succ \tau_2)+P(\tau_2\succ \tau_3)$.

**Question (b)** (3 pts) Suppose $\tau_1=(s_{1,0},a_{1,0})\to (s_{1,1},a_{1,1})\to \cdots \to (s_{1,n},a_{1,n})$ and $\tau_2=(s_{2,0},a_{2,0})\to (s_{2,1},a_{2,1})\to \cdots \to (s_{2,n},a_{2,n})$. Define $\tau_1\circ\tau_2=(s_{1,0},a_{1,0})\to (s_{1,1},a_{1,1})\to \cdots \to (s_{1,n},a_{1,n})\to (s_{2,0},a_{2,0})\to (s_{2,1},a_{2,1})\to \cdots \to (s_{2,n},a_{2,n})$. If $\tau_1\succ \tau_2\succ \tau_3$, compare $\tau_1\circ \tau_2$ with $\tau_1,\tau_2,\tau_3$.

#### 2.2.2 Grid World Instance

Consider a grid world instance, where the agent can move north, south, west, east to adjacent grids. The transitions are deterministic. In the dataset $\mathcal{D}$, trajectories belong to the same trajectory pair start at the same grid, all trajectories end at different grid. That is, $\forall (\tau_1,\tau_2)\in \mathcal{D}$, $s_{1,0}=s_{2,0}$; $\forall i\neq j$, $s_{i,|\tau_i|}\neq s_{j,|\tau_j|}$.

Li Hua thinks training a reward model is too troublesome, so he comes up with a new strategy: for each trajectory $(s_0,a_0)\to \cdots\to (s_n,a_n)$, assign a terminal reward $r(s_n,a_n)$ and set non-terminal rewards to $0$, so that $\forall (\tau_1,\tau_2)\in \mathcal{D}$, if $\tau_1\succ \tau_2$, $R(\tau_1)>R(\tau_2)$ and vice versa. Then, perform Q-learning with TD-update to get Q-functions. The policy should always follow $\arg\max_{a} Q(s,a)$. 

**Question (c)** (4 pts) Consider the single trajectory $\tau=(s_0,a_0)\to (s_1,a_1)\to (s_2,a_2)\to (s_3,a_3)$ shown in the figure. The terminal reward is $r$, and the discounting factor is $\gamma$. What are the convergence values of $Q(s_k,a_k)$ for $k=0,1,2,3$ after Q-learning?

$$
\begin{array}{|c|c|c|c|}
\hline
\ \ \ \ & & & \downarrow \\
\hline
 & \leftarrow & \leftarrow & \leftarrow \\
\hline
\end{array}
$$

**Question (d)** (4 pts) Does the strategy of Li Hua always follow the preferred trajectory starting from a given grid? Prove your opinion.

**Hint**: Could $Q(s_0,a_0)>R(\tau)$?

## 3 Deep Learning: GNN

## 4 Probability