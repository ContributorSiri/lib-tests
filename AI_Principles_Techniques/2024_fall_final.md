# AI Principles and Techniques 2024 Fall Midterm

## General Information

- **Date**: 2024.12.23
- **Time**: 19:20 - 21:20
- You are allowed (and also recommended) to use **a calculator** and an **A4 page of cheatsheet**.
- **Total points**: $100$.

## 1 Search

## 2 Reinforcement Learning

## 3 Deep Learning: GNN

### 3.1 (27 pts) Bob's Graph Neural Networks
#### 3.1.1 Background

Bob is a biology student who was deeply shocked upon learning that this year's Nobel Prize in Biology was awarded to Al rescarchers. As a result, he decided to switch to the field of Al. Recently, he has been fascinated by a particular type of neural network: Graph Neural Networks (GNNs). Here is a brief introduction of GNN's:

Graphs provide a powerful way to represent arbitrary relational structures between entities, More importantly, many natural objects, such as protein structures, biomolecules, and chemical compounds, are inherently graph-structured. Therefore, graphs are particularly suited for representing biological and chemical elements. To design a ncural network that can process such structures, we need to develop specialized frameworks, collectively known as Graph Neural Networks (GNNs).

#### 3.1.2 Introduction

The core component of GNNs is Message Passing, which will perform $K$ iterations. To start,
let's define some notations. A graph $G = (V, E)$ is the combination of a node set $V$ and a edge set $E$. $V$ contains $||V||$ nodes, while $E$ contains $||B||$ edges $(u, v)$, each edge links two node from $||V||$. For each node, it contains a feature $X_u\in R^d$, where $d$ is the feature dimension. During each message passing iteration in a GNN, a hidden feature $h_u^{(k)}$ is generated, representing the updated feature of node $u\in V$ in the $k$ iteration, based on the information aggregated from $u$'s graph neighborhood $N(u)$ (the set of nodes connected with $u$). In its most general form, a message passing update can be expressed as

$$
h_u^{(k)} = \Phi^{(k)}\left(h_u^{(k-1)}, \oplus_{v\in N(u)}\Psi^{(k)}(h_u^{(k-1)}, h_v^{(k-1)})\right)\\
= \Phi^{(k)}\left(h_u^{(k-1)}, \oplus_{v\in N(u)}\left(m_{u\to v}^{(k)}\right)\right)\\
= \Phi^{(k)}\left(h_u^{(k-1)}, m_u^{(k)}\right)
$$

where $\Phi^{(k)}$ (update function), $\Psi^{(k)}$ (message function) are arbitrary differentiable functions (e.g. neural network), $\oplus$ is an (aggregation operator), typically a nonparametric function e.g. summation or maximum. For notational simplicity, we use $m_{u\to v}^{(k)}=\Psi^{(k)}(h_u^{(k-1)}, h_v^{(k-1)})$ to denote the message from a sender node $v$ to receive node $u$, and $m_u^{(k)}$ to denote aggregated messages from all of $u$'s neighbors. The superscript $(k)$ on functions and $(k-1)$ is used to distinguish between different rounds of message passing. A single GNN layer may include $K$ rounds of message passing. 

Message construction, aggregation and update can be considered the three main building blocks of a message passing layer. The initial embeddings at $k=0$ are set to the input feature of each node: $h_u^{(0)}=X_u\in R^d,\forall u\in V$. After $K$ iterations of message passsing, the feature $h_u^{(K)}$ of each node $u$ might node $u$ might encode all information relevant for the training objective, which may be used downstream application e.g. classification, regression or unsupervised learning.

#### 3.1.3 Perceptron GNNs

The general formulation above is quite abstract. Let's instantiate it concretely by considering a basic GNN message passing block, Perceptron, as below:

$$
h_u^{(k)} = \sigma\left(W_{self}^{(k)}h_u^{(k-1)} + W_{neigh}^{(k)}\sum_{v\in N(u)}h_v^{(k-1)}+b^{(k)}\right)
$$

where $W_{self}^{(k)}, W_{neigh}^{(k)}\in R^{d^{(k)}\times d^{(k-1)}}$ are trainable parameter matrices, $\sigma$ is an activate function (e.g. ReLU) and $b^{(k)}\in R^{d^{(k)}}$ is the trainable bias parameters.

Question (a) (6 pts): Please identify the function that instantiate the message function $\Psi^{(k)}$, the aggregation operator $\oplus$, and the update function $\Phi^{(k)}$.

#### 3.1.4 CNNs are GNNs

Actually, mcssage passing is a fairly general formalism. Let's now consider the convolutional flavor of massage passing. We may define that:

$$
h_u^{(k)} = \phi\left(h_u^{(k-1)}, \oplus_{v\in N(u)}\left(\left\{W^{(k)}h_v^{(k-1)}\right\}\right)\right)
$$

We can express our familiar 2D convolution layer as convolutional message passing on a graph. Consider an input $I\in R^{H\times W\times d^{(k-1)}}$, where $H\times W$ is the image size and $d^{(k-1)}$ is the input channels of the $k$-th layers of CNNs.

Question (b) (3 pts): Suppose the kernel size of CNNs is $h = 3,w = 3$, and the windows
stride step is 1. There is no padding. If we use Equation 6 to reformulate CNNs as GNNs.
what is the graph $G = (E,V)$ of CNNs ?

Question (c) (6 pts): If we use sigmoid as the activation function, based on your answer in Question (b), write down the definition of $\phi^{(k)}$, $\oplus$.

#### 3.1.5 Attention is All You Need
One of the main design methods for modern neural network is the attention mechanism, which has become the cornerstone of the popular Large Language Models (LLMs). Given feature sets $\{q_i\}_{i=1}^N,\{k_i\}_{i=1}^N,\{v_i\}_{i=1}^N$, where $q_i\in R^{D},k_i\in R^{D},v_i\in R^{D}$, the attention mechanism output:

$$
o_i=\sum_{j=1}^N\frac{sim(q_i,k_j)}{Z_i}v_j\quad s.t. \quad Z_i=\sum_{j=1}^Nsim(q_i,k_j)
$$

where sim is a measurement of the similarity betwcen two elements. Usually, people set $sim(x,y)=x^Ty$. The attention mechanism in Equation is called so because it uses the "query" feature $q_i$ of element $i$ to compare with a set of "key" features $\{k_j\}_{j=1}^N$. The similarity $sim(q_i, k_j)$ serves as the weight (attention) for the corresponding "value" $v_j$, which is then used to combine the values based on their relevance.

Question (d) (5 pts): Design a method to merge the attention mechanism above to GNNs to create a new type of GNNs called "Graph Attention Networks (GAT)".

Hint: You may refer to the general formulation of GNNs in Equation 2, 3, 4. There may be multiple solutions. You shouldn't hesitate for too long. Just write down one reasonable solution you think.

#### 3.1.6 Graph Anything Model

Through your analysis, Bob sees the power of GNNs. It seems that GNNs are a general network architecture that can encompass perceptrons, convolutional networks, attention-based networks, and more. However, he wonder when he should use GNNs.

Question (e) (7 pts): Do you think we should use GNNs all the time? Use a comparison with CNN's as an example and provide at least two reasons for your conclusion.

## 4 Probabilistic Models and Inference

### 4.1 (24 pts) Alice's Old Robot

#### 4.1.1 Basics
Alice's grandpa recently gave her an (really) old robot he used to build and maintain. He tells her that it worked fine back in the day, but he's not sure about its current condition. Now Alice want to monitor the robot over the next few weeks to determine if it's still functioning ($F$) properly. She is particularly concerned about whether the robot is still capable of performing its tasks without observing errors ($E$) and delays ($S$) (two observations which reflect the robot functionality). Alice's grandpa makes the following conclusion:
- The prior probability of the robot functioning properly (in day 1) ($F = 1$), with no observations, is 0.7.
- The probability of the robot functioning on day t is 0.8 given that it was functioning on the previous day, and 0.3 if not.
- The probability of the robot displaying error messages ($E = 1$) is 0.2 if the robot is functioning properly, and 0.7 if not.
- The probability of the robot responding slowly ($S = 1$) is 0.1 if the robot is functioning properly, and 0.3 if not.
  
Since Alice knows you've taken professor's Artificial Intelligence Principles and Techniques course, she asks for your help in figuring out the robot's functionality. Let's explore it together.

#### 4.1.2 Mathematical Modeling
Let's first convert the information into a mathematical model.

Question (a) (3 pts): Formulate the conclusion from Alice's grandpa using conditional probability, with the binary variables $F_t, E_t$, and $S_t$

Question (b) (4 pts): If we want to reformulate this problem as a hidden Markov model (HMM) instead (that has only a single observation variable), how would you do so? Provide a brief description of your design, and then write down the probability tables for the HMM.

#### 4.1.3 Estimate the Future

Now, you and Alice are ready to record the robot's performance. But before that, you decide to calculate the probabilities of what might happen in the next T days.
Question (c) (4 pts): We first consider $T = 2$. One of the worst-case scenarios is that robot displays both error messages and slow responses on both days. What is the probability the of that ?

Question (d) (5 pts): Now let's consider $T$ to be very large. Alice find that it is impossible for her to calculate it manually. Luckily, she find a algorithm called $\alpha$-update algorithm. Given the observation $(e_t,s_t),t=1\dots T$, it defines:
$$\alpha_t(x)=P(F_t=x,e_{1:t},s_{1:t})$$
where $e_{1:t}$ and $s_{1:t}$ means the joint observation from day 1 to day $t$. The $\alpha$-update algorithm is an $O(T)$ algorithm which calculates $\alpha_t(x)$ with recursion. Please first derive the relationship between $\alpha_t(x)$ and $\alpha_{t-1}(x)$, and then describe how to describe $P(e_{1:t},s_{1:t})$ using $\alpha$-update algorithm.

#### 4.1.4 Infer the Functionality

Now you and Alice start observing the robot's behavior. You have recorded the observations for $T$ days, $e_{1:T},s_{1:T}$. The problem now is to find the most likely sequence of $F_{1:t}$ that generated the observed data

Question (e) (8 pts): Design an algorithm to find the most likely $F_{1:t}$ sequence from $e_{1:T},s_{1:T}$, making it as efficient as possible.
Hint: Describe it with formulations and language. Pseudo-code is not necessary, but you may use it if you want.
Hint: One potential direction is to consider the equation:
$$\max_{X_{1:T}}f(X_{1:T})=\max_{X_T}\max_{X_{1:T-1}}f(X_{1:T})$$
Hint: You should consider $T$ to be very large. There may be multiple solutions. Please write down the most efficient one you can think of