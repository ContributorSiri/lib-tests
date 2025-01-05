# ML final 2024

## Short Answer

2/3/4 for each question

1. given $x_0$, let $f$ be a smooth function, write the lower bound and upper bound of $f(x)$ at any point $x$
2. Suppose $f$ is a smooth function, how should we choose the learning rate $\eta$ to ensure the $f$ value decreases in each GD step
3. Compare the classical view and modern view of overfitting
4. NFL
5. Assume $f(x)=\dfrac{1}{n}\sum_{i=1}^n l_i(x)$. Let $\tilde u=\nabla f(\tilde w)$ and $w^\star$ is the global optimum. Prove one of the inequality that introduced in SVRG analysis:

   $$
   \mathbb{E}\|\nabla l_i(w_{t-1})-\nabla l_i(\tilde w)+\tilde u\|_2^2\le 2\mathbb{E}\|\nabla l_i(w_{t-1})-\nabla l_i(w^\star)\|_2^2 + 2\mathbb E \| \nabla l_i(\tilde w) - \nabla l_i(w^\star)\|_2^2.
   $$

   $$


   $$
6. What is shattering and VC dimension
7. What is the difference between lasso and ridge-regression
8. What is a RIP-condition
9. RIP Thm1
10. State the soft version of SVM
11. State the Adaboost
12. Decision tree qieyiduan Thm
13. State the minimal PCA reconstruction error( You only need to write down the formula )
14. What is Cross Entropy Loss
15. Consider the a kind of technique called backward pass differentiable approximation. Suppose we use JPEG compression to defend. How to attack this model using this technique
16. Give a scenario that we can use a zero-order optimization, but a first-order optimization or higher-dimension optimization can not work.
17. How do we define prior distribution in Gaussian process of Bayesian Optimization
18. Consider the back-propogation framework that we introduce in the lecture of hyperparameter tuning, think about the process of back-propogation with decay $\gamma$. Write down the $w_{t+1}$ and $v_{t+1}$ using  $w_t$, $v_t$. How can we recover $w_t$ and $v_t$ using $w_{t+1}$ and $v_{t+1}$
19. In Successive Halving Algorithm, total budget is $B$, in round $r$, how much budget is do each arm received
20. State IntegratedGradient and show this method satisfies completness axiom
21. Write down rewireing process of rectified flow
22. State the Mercer Theorem
23. What is the graph Laplacian?
24. Recall the Linear Coupling Mentioned in Class

    $$
    \text{Starting:}  x_0=y_0=z_0\\
    Set: x_{k+1}=\tau z_k+(1-\tau)y_k\\
    y_{k+1}=x_{k+1}-\eta\nabla f(x_{k+1})\\
    z_{k+1}=Mirr_{z_k}(\alpha\nabla f(x_{k+1}))
    $$

    Proof that if we can choose $\alpha$ and $\eta$ properly, we can have the following statement:

    $$
    \alpha\left<\nabla f(x_{k+1}),x_{k+1}-u\right>\le\alpha^2 L(f(y_k)-f(y_{k+1}))+V_{z_k}(u)-V_{z_{k+1}}(u)
    $$

## Require Thinking

1. Gini
2. Gradient boosing, L2 -> L1
3. SHAP, efficiency, n! -> 2^n, still?
4. Escape saddle point ...
5. k=2 is NP hard, why can we do?
6. 10000 larger?
7. LSH family of L2


## Long Proofs

1. each round probability
2. e xi xj Wxi Wxj
3. SIMCLR : InfoNCE

## Advanced

1. 2D RoPE
2. NFL extend to k
