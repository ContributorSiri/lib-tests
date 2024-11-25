# Machine Learning 2024 Midterm Exam

- **Date**: 2024.11.8
- **Time**: $90$ minutes.
- **Score**: $120$, $80$ points for basic questions and $40$ points for advanced questions. **The score will be clipped to $100$** if exceeding $100$.
- **Cheatsheet is not allowed.**

## 1 Question-Answering ($56$ pts)

1. ($2$) What is the difference between classification and regression?
2. ($3$) When a function is smooth, we know it has both an upper bound function and a lower bound function. What are these two functions?
3. ($3$) What is the difference between compressed sensing and linear regression?
4. ($4$) SAG algorithm is defined as
$$w^{k+1}=w^k-\eta\left[\dfrac{f_j'(w^k)-f_j'(\phi_j^k)}{n}+\dfrac{1}{n}\sum\limits_{i=1}^n f_i'(\phi_i^k)\right],$$
where:

- $w^k$ is the current weight vector at step $k$;
- $\eta$ is the step size (learning rate);
- $f_j'(w^k)$ is the gradient of loss function $f$ with data point $j$ at the weight $w^k$;
$f_j'(\phi_j^k)$ is the stored gradient of loss function $f$ with data point $j$ at the last calculated point $\phi_j^k$;
- $n$ is the number of data points.

SAG updates the gradient for only one randomly selected data point $j$ at each step, reducing computational cost. If at step $k$, it picks $j$ as the data point, then the update rule for $\phi_i^k$ is defined as follows:
$$\phi_i^{k+1}=\begin{cases}w^k,&i=j;\\\phi_i^k,&i\neq j.\end{cases}$$
Is SAG one kind of SGD method that we defined in class? If yes, prove it; if no, explain why.

5. ($4$) In the proof of SGD convergence analysis, assume we already know that
$$\mathbb{E}f(w_{i+1})\le f(w^\star)+\dfrac{1}{2\eta} \mathbb{E}(||w_i-w^\star||^2-||w_{i+1}-w^\star||^2)+\eta\sigma^2.$$
Please derive the upper bound for $\mathbb{E}f(\bar w_t)$.

6. ($4$) State the SVRG algorithm with pseudo-code.

7. ($4$) Recall that in linear coupling, after telescoping for $T$ steps of the algorithm, we can set
$$\bar x:=\dfrac{1}{T}\sum\limits_{k=0}^{T-1} x_k$$
and get
$$\alpha T(f(\bar x)-f(x^\star))\le \alpha^2L(f(y_0)-f(y_T))+V_{x_0}(x^\star)-V_{x_T}(x^\star),$$
where $\alpha$ is the learning rate in the MD step, and $V_x(y)$ is the Bregman divergence bounded by a constant $\Theta$. Please continue to show linear coupling gives $1/T^2$ convergence rate.

8. ($4$) What is the non-convex objective of matrix completion that we learned in class? Why is it non-convex?

9. ($4$) What is strict saddle point? What is a flat saddle point? What are their differences?

10. ($4$) State the no-free-lunch theorem.

11. ($4$) If a hypothesis class $H$ contains $100$ hypothesis, is this class guaranteed to be agnostic PAC learnable? If yes, provide brief explanation. If no, provide one counter example.

12. ($4$) Provide one hypothesis class that is not PAC learnable and explain why.

13. ($3$) Why do we say cross entropy is equivalent to KL divergence in terms of loss function design?

14. ($3$) Ignoring all the constants. Please write down, in our main theorem of compressed sensing, how many measurements do we need to recover the unknown signal $x\in \mathbb{R}^d$? You should write it in terms of sparsity of the signal $s$, dimension $d$, failure probability $\delta$, error $\epsilon$.

15. ($6$) Let $f:\mathbb{R}^n\to \mathbb{R}$ be a differentiable convex function. This means that for any $x,x'\in \mathbb{R}^n$ and $\lambda\in [0,1]$, the following holds:
$$f(\lambda x'+(1-\lambda)x)\le \lambda f(x')+(1-\lambda)f(x).$$
Please prove that, for any $x,x'\in \mathbb{R}^n$, the following inequality also holds:
$$f(x')\ge f(x)+\nabla f(x)^T(x'-x).$$

## 2 Intuition of Sticks ($8$)

In the proof of compressed sensing main theorem, we defined the partitions $T_0,T_1,\cdots$, where $x$ is the unknown signal, $x^\star$ is our solution. $T_0$ contains the largest elements in absolute value in $x$, and $T_1,T_2,\cdots$ are sorted in $h=x^\star-x$. $s$ is a constant denoting the sparsity, and $x_s$ is the best $s$-sparse vector that approximates $x$. Now, please prove formally that
$$||h_{T_0^c}||_1\le ||h_{T_0}||_1+2||x-x_s||_1.$$

## 3 Perceptron Analysis ($8$)

For the Perceptron algorithm, assume that there exists $w^\star$ such that $||w^\star||_2=1$, and there exists $\gamma>0$ such that for any data point $i$, $y_i\langle w^\star, x_i\rangle\ge \gamma$. Moreover, assume that $||x_i||_2\le R$ for all $i$. Please prove that, the Perceptron algorithm makes at most $\dfrac{R^2}{\gamma^2}$ mistakes, when starting from $w_0=\mathbf{0}$.

## 4 Mirror Descent Guarantee ($8$)

Recall that, in Mirror descent, we apply the following updating rule
$$x_{k+1}=\text{Mirr}_{x_k}(\alpha \nabla f(x_k)),$$
where
$$\text{Mirr}_x(\xi)=\arg\min_{y} (V_x(y)+\langle\xi,y-x\rangle).$$
Assume now $V_x(y)$ is the Bregman divergence that is strongly convex w.r.t. $||\cdot||_p$ ($p>1$). Please prove that
$$\alpha(f(x_k)-f(u))\le \dfrac{\alpha^2}{2}||\nabla f(x_k)||_q^2+V_{x_k}(u)-V_{x_{k+1}}(u)$$
for every $u$. Here, $1/p+1/q=1$.

## Advanced 1: Smoothness and Convexity ($10$)

Let $f$ be $\mu$-strongly convex and have Lipschitz continuous gradients with constant $L$. Prove that for all $x,y$, 
$$f(x)\ge f(y)+\langle f'(y),x-y\rangle+\dfrac{1}{2(L-\mu)} ||f'(x)-f'(y)||^2+\dfrac{L\mu}{2(L-\mu)} ||y-x||^2+\dfrac{\mu}{L-\mu} \langle f'(x)-f'(y),y-x\rangle.$$
**Hint**: You may first prove that for $L$-smooth and convex function $f$,
$$f(x)\ge f(y)+\langle f'(y),x-y\rangle+\dfrac{1}{2L}||f'(x)-f'(y)||^2.$$

## Advanced 2: Newton's Method

Given a quadratic objective function to optimize:
$$f(\mathbf{x})=\dfrac{1}{2}\mathbf{x}^T\mathbf{H}\mathbf{x}+\mathbf{c}^T\mathbf{x}+b,$$
where $\mathbf{H}\in \mathbb{R}^{n\times n}$ is a positive definite Hessian matrix.

Newton's method is an iterative optimization algorithm used for finding the roots or critical points of a function. For minimizing a given function $f(\mathbf{x})$, the method updates the variable $\mathbf{x}$ using the following update rule:
$$\mathbf{x}_{\text{new}}=\mathbf{x}-\mathbf{H}^{-1}\nabla f(\mathbf{x}),$$
where $\mathbf{H}=\nabla^2 f(\mathbf{x})$ is the Hessian matrix.

Please give **tight** convergence analysis of Newton's method for $f(\mathbf{x})$. 

_NOTE._ The answer of this question is: only $1$ step to converge. Quite strange.

## Advanced 3: Union of VC Dimension ($10$)

Given two hypothesis classes $H_1,H_2$ over a fixed domain $X$. Let $d=\max\{\text{VCDim}(H_1),\text{VCDim}(H_2)\}$. Prove that
$$\text{VCDim}(H_1\cup H_2)\le 2d+1.$$
Is this bound tight? Prove your claim.

## Advanced 4: Implicit Regularization ($10$)

Let $S=\{(x_i,y_i)\}_{i=1}^n$ be the training set, where $X=[x_1,\cdots,x_n]^T\in \mathbb{R}^{n\times d}$, $y=(y_1,\cdots,y_n)^T\in \mathbb{R}^n$, and $n<d$. This setting is overparameterized, and $X$ is assumed to be full rank, implying an infinite number of solutions. Each row of $X$ is a data point.

The loss function is defined as
$$L(w)=\dfrac{1}{2n}||Xw-y||^2.$$
Given the convex nature of the square loss function, GD can be applied to find a global minimum. We initialize our $w_0=\mathbf{0}$, and use GD update rule:
$$w_{t+1}=w_t-\eta_t \nabla L(w_t),$$
where $\eta_t$ is the learning rate. Please prove the following claims.

_NOTE._ The question part is missing.