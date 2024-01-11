**Problem.** ($12$ pts) For an $n\times n$ self-adjoint matrix $H\in M_{n\times n}(\mathbb{C})$, prove that:     
(a)  $I_n-iH$ and $I_n+iH$ are both invertible;($6$ pts)     
(b)  $A=(I_n-iH)(I_n+iH)^{-1}$ is a unitary matrix, and $-1$ is not its eigenvalue.($6$ pts)

**Problem.** ($12$ pts) Let $T$ be a linear operator on a finite-dimensional inner product space $V$. Suppose that the characteristic polynomial of $T$ splits. Then there exists an orthonormal basis $\beta$ of $V$ such that the matrix $[T]_{\beta}$ is upper triangular.

**Problem.** ($12$ pts) The quadratic form $f:\mathbb{R}^3\to \mathbb{R}$ defined by
$$f((x_1,x_2,x_3)^{T}) = (1-a)x_1^2+(1-a)x_2^2+2x_3^2+2(1+a)x_1x_2$$
has rank $2$ (the rank of a quadratic form is defined as the rank of a matrix representation of its corresponding bilinear form $H$).     
(a)  Find the value of $a$. ($4$ pts)     
(b)  Find an orthonormal basis $\beta$ for $\mathbb{R}^3$, such that $\psi_{\beta}(H)$ is a diagonal matrix. ($8$ pts)

**Problem.** ($12$ pts) In the vector space $V=\text{span}(S)$ with the inner product
$$\langle f,g\rangle=\int_{0}^{\pi} f(t)g(t)\text{d} t,$$
$S=\{\sin t,\cos t+1,1,t+t^2\}$ with $t\in [0,\pi]$, and $h(t)=2t+1$.    
(a)  Use the Gram-Schmidt process to transform the ordered basis $S$ into an orthonormal basis $\gamma$ for $V$. ($6$ pts)    
(b)  Calculate the coordinate vector of $h(t)$ relative to $\gamma$. ($6$ pts)

**Problem.** ($12$ pts) Let $A$ be an $n\times n$ matrix taking a Jordan block form,    
$$
A = \begin{bmatrix}
    \alpha & 1 & 0 & 0 & \ldots & 0 & 0\\
    0 & \alpha & 1 & 0 & \ldots & 0 & 0\\
    \vdots & \vdots & \vdots & \vdots & \ddots & \vdots & \vdots\\
    0 & 0 & 0 & 0 & \ldots & \alpha & 1\\
    0 & 0 & 0 & 0 & \ldots & 0 & \alpha\\
\end{bmatrix}.
$$
Calculate $A^k$ with $k$ being a nonzero positive integer.

**Problem.** ($15$ pts) Let $A,B$ be $m\times n$ real matrices satisfying $A^{T}B+B^{T}A=O$. Prove that
$$\text{rank}(A+B)\ge \max\{\text{rank}(A),\text{rank}(B)\},$$
and prove that the equality holds if and only if there exists an $m\times m$ matrix $P$ such that either $B=PA$ or $A=PB$.

**Problem.** ($15$ pts) Let $A,B\in M_{n\times n}(\mathbb{C})$, and $A^T=A,B^T=B$. that is, $A$ and $B$ are complex symmetric matrices. Suppose that $A$ is similar to $B$, that is, there exists an invertible matrix $P\in M_{n\times n}(\mathbb{C})$ such that $B=P^{-1}AP$. Prove that there exists an invertible matrix $O\in M_{n\times n}(\mathbb{C})$ satisfying    
(a)  $O^TO=OO^T=I_n$;    
(b)  $B=O^TAO$.    
You can use the following theorem directly. For an invertible matrix $X\in M_{n\times n}(\mathbb{C})$, there exists a polynomial $g(t)$ such that $g(X)^2=X$.