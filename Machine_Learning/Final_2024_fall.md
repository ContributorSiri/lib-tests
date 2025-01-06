# Machine Learning Final 2024

- **Time**: 2025.1.3, 19:00 - 22:00
- **Score**: $100+10=110$ ($10$ points for advanced problems), clip to $100$ when exceeding $100$.

## Short Answer Problems I

There are $25$ short answer problems in this section. You only need to write a few sentences for each of the problems below.

1. Let $f$ be a smooth function. Write down the lower bound and the upper bound of $f(x)$ at any point $x$, if $f(x_0)$ and $\nabla f(x_0)$ is given.
2. Let $f$ be a smooth function. How should we choose the learning rate $\eta$ to ensure the $f$ value decreases in each GD step?
3. What is the difference between the classical view and modern view of overfitting?
4. Prove the following inequality, which is crucial in the proof of No Free Lunch Theorem. Let $S=\{x_1,x_2,\cdots,x_m\}$ be the training set, and $\{v_1,v_2,\cdots,v_p\}$ are the examples in the dataset $\mathcal C$ that do not appear in $S$, such that $p\ge m$. Suppose there are $T$ datasets $\mathcal D_{i}$ ($1\le i\le T$), each one corresponding to a ground-truth function $f_i:\mathcal C\to \{0,1\}$. Prove that, for every algorithm $A$, we have
    $$
    \dfrac{1}{T}\sum_{i=1}^T \mathcal L_{\mathcal D_i}(A(S^i))\ge \dfrac{1}{2}\min_{r\in [p]} \dfrac{1}{T} \sum_{i=1}^T \mathbf 1_{A(S^i)(v_r)\neq f_i(v_r)}.
    $$
5. Assume $f(x)=\dfrac{1}{n}\sum_{i=1}^n l_i(x)$. Let $\tilde u=\nabla f(\tilde w)$, and $w^\star$ is the global optimum. Prove one of the inequality that is introduced in SVRG analysis:

   $$
   \mathbb{E}\|\nabla l_i(w_{t-1})-\nabla l_i(\tilde w)+\tilde u\|_2^2\le 2\mathbb{E}\|\nabla l_i(w_{t-1})-\nabla l_i(w^\star)\|_2^2 + 2\mathbb E \| \nabla l_i(\tilde w) - \nabla l_i(w^\star)\|_2^2.
   $$

   $$


   $$
6. What is shattering? What is the definition of the VC dimension?
7. Compare the difference between LASSO and Ridge regression.
8. What is RIP-condition?
9. Let $\varepsilon<1$, and $W$ is a $(\varepsilon,2s)$-RIP matrix. Let $x$ be a $s$-sparse vector, and $y=Wx$. Prove that
$$\{x\}=\arg\min_{v:Wv=y} \|v\|_0.$$
10. State the soft-margin SVM.
11. State the Adaboost algorithm.
12. Prove the following theorem, which is used to prove the main theorem in polynomial approximation of decision trees. Suppose $h(x_1,x_2,\cdots,x_n)\in \{-1,1\}^n$ is a polynomial with degree $\le \log (s/\varepsilon)$ and $\|h\|_1\le s$. Prove that there is a polynomial $f$, with degree $\le \log(s/\varepsilon)$ and $\|f\|_0\le s^2/\varepsilon$, such that $\|h-f\|_2\le \varepsilon$.
13. State the minimizing reconstruction error objective of PCA.
14. What is the cross entropy?
15. Consider a kind of attacking technique called backward pass differentiable approximation. Suppose we use JPEG compression for a model. Briefly explain how to attack this model using this technique.
16. Give a scenario that we should use zero-th order optimization methods, while the first order methods or higher order methods are not applicable.
17. How do we define prior distribution in Gaussian process of Bayesian optimization?
18. We have introduced the back-propogation framework in the lecture of hyperparameter tuning. Think about the process of back-propogation with decay $\gamma$. Express $w_{t+1}$ and $v_{t+1}$ using $w_t$, $v_t$. How can we recover $w_t$ and $v_t$ using $w_{t+1}$ and $v_{t+1}$?
19. In Successive Halving (SH) algorithm, suppose the total budget is $B$. Then, how much budget does each (survived) arm received in round $r$?
20. State Integrated Gradient algorithm and show this method satisfies the completeness axiom.
21. Write down the rewiring process of rectified flow.
22. State the Mercer's Theorem.
23. What is the definition of Laplacian $L$ of a graph?
24. Recall the Linear Coupling algorithm:

    $$
    \text{Starting: }x_0=y_0=z_0\\
    x_{k+1}=\tau z_k+(1-\tau)y_k\\
    y_{k+1}=x_{k+1}-\eta\nabla f(x_{k+1})\\
    z_{k+1}=Mirr_{z_k}(\alpha\nabla f(x_{k+1}))
    $$

    Proof that if we choose $\alpha$ and $\eta$ properly, we have the following inequality holds:
    $$
    \alpha\left<\nabla f(x_{k+1}),x_{k+1}-u\right>\le\alpha^2 L(f(y_k)-f(y_{k+1}))+V_{z_k}(u)-V_{z_{k+1}}(u).
    $$

25. What is the main improvement of t-SNE compared with traditional SNE? What problem does this improvement solve?

> _NOTE_. Question 25 does not actually appear in the test. Instead, it is made by us since we believe t-SNE should be on the test paper.

## Short Answer Problems II

There are $7$ problems in this section. Some of them requires thinking and a longer proof or calculation.

1. Compute the Gini index for weather and humidity, respectively. Which one has a larger Gini index? Which one will be preferred to be the first layer of the decision tree?

| Weather | Humidity | Decision |
|----------|----------|----------|
|    Sunny     |    High     |    Yes     |
|    Overcast     |    Low     |    Yes     |
|    Rain     |    Low     |    Yes     |
|    Sunny     |    High     |    No     |
|    Rain     |    Low     |    No     |
|    Rain     |    High     |    No     |
|    Overcast     |    High     |    Yes     |
|    Overcast     |    High     |    Yes    |
|    Sunny     |    Low     |    Yes     |
|    Overcast     |    Low     |    Yes     |
|    Sunny     |    High     |    No     |
|    Rain     |    High     |    No    |
|    Sunny    |    Low     |    Yes     |
|    Rain     |    Low     |    Yes     |

2. Gradient boosting algorithm is essentially learning the gradient of a loss function with respect to the current weak learner $F$. Classical gradient boosting uses the square loss function. If we use the absolute difference (i.e. $\ell_1$ loss) as the loss function, write down the new gradient boosting algorithm.
3. Prove that SHAP algorithm satisfies efficiency. Note that SHAP needs to consider all permutations, so the denominator of the attribution is $n!$. Can we change this denominator into $2^n$, i.e. consider all subsets? If yes, prove the efficiency for the new formula; if no, identify which stage breaks.
4. Consider the escaping saddle point scenario. If the point is initialized at a local maximum, can we guarantee that the algorithm can escape from this point? Use the assumption made in the class to prove your opinion.
5. Ratiocut problem is proved to be NP-hard. However, we claimed in class that solving the optimal $v^A$ that minimizes $(v^A)^TLv^A$ is sufficient. It seems like a simple linear algebra problem! How is it possible? What else did we do to transfer Ratiocut into this quadratic programming problem?
6. In RoPE, we set $\theta_i=10000^{-2(i-1)/d}$. What will happen if we change $10000$ into a larger integer, say $50000$?
7. Prove the local sensitive property for the following hash function in $\ell_2$ measure. Let $r\sim \mathcal N(0,I)$, $b\sim \mathcal U(0,w)$, the hash function is
$$h(x)=\left\lfloor \dfrac{\langle r,x\rangle+b}{w}\right\rfloor.$$


## Long Proofs

In this section, you need to provide a rigorous proof for each question.

1. Consider the SH algorithm for multi-arm bandit problem. Suppose we have $B$ budgets, and arm 1 is the best arm (i.e. $v_1>\max\{v_2,v_3,\cdots\}$). Let $\Delta_i=v_1-v_i$ and 
    $$H_2=\max_{i\ge 2} \dfrac{i}{\Delta_i^2}.$$
    Prove that, in each round, the probability of eliminating arm 1 is at most
    $$3\exp\left\{-\dfrac{B}{8\log_2 nH_2}\right\}.$$
2. Suppose $W$ is $(\varepsilon,2s)$-RIP. $I,J$ are two disjoint sets of size $s$. Prove that, for each vector $\mu$,
    $$\langle W\mu_I,W\mu_J\rangle\le \varepsilon \|\mu_I\|\cdot\|\mu_J\|.$$
3. Prove that InfoNCE loss in SimCLR is equivalent to minimizing the cross entropy loss of adjacency matrices generated by Markov Random Fields (MRFs). Recall that the cross entropy loss
    $$H_\pi^k(Z)=-\mathbb{E}_{W_X\sim P(\cdot;\pi)} \log P(W_Z=W_X;K_Z),$$
    and the InfoNCE loss
    $$\text{InfoNCE}=-\sum_i \log \dfrac{\exp\{-\|f(X_i)-f(X_{i'})\|^2/2\tau\}}{\sum_j \exp\{-\|f(X_i)-f(X_{j})\|^2/2\tau\}},$$
    where $i'$ is the random generated data augmentation pair using $\pi$. Note that you should first state how to do data augmentation, and how to define $\Omega$ for each MRF, so that these two losses are equivalent.

## Advanced Problems

1. Design a 2-dimension RoPE matrix $R_{x,y}$ for each $(x,y)\in \mathbb{N}_+^2$. Note that $\{R\}$ should satisfy two properties: by multiplying $R$, the dot product of two vectors in position $(x_1,y_1),(x_2,y_2)$ should carry the information of their position difference $(x_1-x_2,y_1-y_2)$; $(x,y)$ can be recovered using $R_{x,y}$.
2. Prove the following extension of No Free Lunch Theorem. Let $A$ be any learning algorithm for the task of binary classification with respect to the $0$-$1$ loss over a domain $X$. Let $m$ be any number smaller than $|X|/k$ ($k\ge 2$ is a fixed integer) representing a training set size. Then, there exists a distribution $\mathcal D$ over $X\times \{0,1\}$ such that:
    
    - There exists a function $f:X\to \{0,1\}$ with $\mathcal L_{\mathcal D}(f)=0$;
    - $$\mathbb E_{S\sim \mathcal D^m} \mathcal L_\mathcal D(A(S))> \dfrac{1}{2}-\dfrac{1}{2k}.$$ 
