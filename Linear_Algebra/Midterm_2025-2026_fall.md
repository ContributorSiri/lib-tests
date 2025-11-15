# Linear Algebra 2025 Fall Midterm
## General Information
- **Date**: 2025.11.14
- **Time**: 13:30 - 16:00
- **Total points**: $100$.
- Cheatsheets and calculators are not allowed.

*Side note:* All *Side notes* did not appear on the exam paper, but the **Hints** did. Moreover, some problems may not be described very clearly, but it is similar to the descriptions in the exam. Problem 6 was a numerical calculation problem and the numbers cannot be recalled, but they are actually trivial and can be filled in arbitrarily.

## Problem 01
Consider a system of linear equations:

$$
\begin{aligned}
(a_1+b)x_1+a_2x_2+\cdots+a_nx_n&=0\\
a_1x_1+(a_2+b)x_2+\cdots+a_nx_n&=0\\
&\vdots\\
a_1x_1+a_2x_2+\cdots+(a_n+b)x_n&=0
\end{aligned}
$$

where $\sum_{i=1}^na_1\ne0$.

**(1)** Find the conditions for $a_1,\cdots,a_n,b$ such that the system has only zero solution.

**(2)** Find the conditions for $a_1,\cdots,a_n,b$ such that the system has non-zero solutions. In this case, find the solution sets.

## Problem 02
Let $T:V\to W$ be a linear transformation. Prove that $\text{nullity}\,T+\text{rank}\,T=\dim V$.

## Problem 03
Suppose $V$ is an $n$-dimensional vector space. Let $T:V\to V$ be a linear transformation, and $W$ is an $r$-dimensional subspace of  that is invariant under $T$. Prove that there exists a basis $\beta$ of $V$ such that $[T]_\beta$ takes the form

$$
\begin{pmatrix}
A&B\\
O&C
\end{pmatrix}
$$

where $A$ is a $r\times r$ square matrix, and $O$ is the $(n-r)\times r$ zero matrix.

**Hint**: $W$ is an invariant subspace means that $T(W)\subseteq W$.

## Problem 04

**(1)** Define the Cartesian product of vector spaces:

$$
V_1\times\cdots\times V_m:=\{(v_1,\cdots,v_m):v_1\in V_1,\cdots,v_m\in V_m\}
$$

It can be verified that $V_1\times\cdots\times V_m$ is a vector space (*Side Note: Verification was given in the exam, but omitted here for simplicity*). Find the dimension of $V_1\times\cdots\times V_m$.

**(2)** Prove that $\mathcal L(V_1,W)\times\cdots\times\mathcal L(V_m,W)$ is isomorphic to $\mathcal L(V_1\times\cdots\times V_m,W)$.

## Problem 05
Suppose $A$, $B$, and $A+B$ are all $n\times n$ invertible matrices. Prove that $A^{-1}+B^{-1}$ is also invertible and find its inverse matrix.

## Problem 06
*Side Note: Numerical calculation problem, but the numbers are irretrievable : (*

**(1)** Suppose $T:\mathbb R^4\to\mathbb R^4$ is a linear transformation with

$$
T(e_1)=\cdots,T(e_2)=\cdots,T(e_3)=\cdots,T(e_4)=\cdots
$$

*Side Note: You can fill in four linearly independent vectors by yourself! (There are about six zeroes in the four vectors)*

Calculate the rank of $T$ and determine if it is invertible.

**(2)** Find the dimension and a basis of $R(T)$ and $N(T)$, respectively.

**(3)** Suppose there is a new basis $\beta$:

$$
\{\cdots,\cdots,\cdots,\cdots\}
$$

*Side Note: Again, any four linearly independent vectors are okay. (There are about eight zeroes in the four vectors)*

Calculate $[T]_\beta$.
## Problem 07
Let $T:V\to W$ be a linear transformation and $T^t:W^*\to V^*$ be its transpose. Suppose there exists $\phi\in W^*$ such that $N(T^t)=\text{span}(\phi)$. Prove that $R(T)=N(\phi)$.

**Hint**: The definition of $T^t$ was given in class.

## Problem 08
Suppose $A$ is a $n\times n$ matrix with rank $r$ ($1\le r\le \frac n2$), and $A^2=0$. Prove that there exists invertible matrix $P$ such that

$$
A=P\begin{pmatrix}
O&I_r&O\\
O&O&O
\end{pmatrix}
P^{-1}
$$

where $I_r$ is the $r\times r$ identity matrix, and $O$ are zero matrices.