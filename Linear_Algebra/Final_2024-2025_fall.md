# Final 2024-2025 Fall

### 1. 
Let \( V \) be an inner product space over \( \mathbb{R} \), and let \( T \) be a function (not necessarily linear) such that \( T(0) = 0 \) and \( \|T(v) - T(w)\| = \|v - w\| \) for all \( v, w \in V \). Let \( \dim(V) = n \).

1. (a) Show that \( \|T(v)\| = \|v\| \) for all \( v \in V \). (5 pts)  
   (b) Show that \( \langle T(v), T(w) \rangle = \langle v, w \rangle \) for all \( v, w \in V \). (5 pts)  
   (c) If \( \{e_1, \dots, e_n\} \) is an orthonormal basis for \( V \), show that \( \{T(e_1), \dots, T(e_n)\} \) is an orthonormal basis as well. (5 pts)  
   (d) Show that \( T \) is linear. (5 pts)  


### 2. 
Perform the Gram-Schmidt process on the following basis for \( \mathbb{R}^3 \):  
\[
\{(1, 1, 1)^t, (0, 1, 1)^t, (1, 3, 0)^t\}
\]  
(8 pts)  



### 3. 
Consider the matrix  
\[
A = 
\begin{pmatrix}
3 & 0 & 8 & 0 \\
3 & -1 & 6 & 0 \\
-1 & 0 & -5 & 0 \\
0 & 0 & 0 & 2
\end{pmatrix} \in M_{4 \times 4}(\mathbb{R}).
\]

- Determine whether the matrix is diagonalizable. (6 pts)  
- If it is not diagonalizable, find its Jordan canonical form. Specifically, find an invertible matrix \( Q \) and a Jordan matrix $B$ such that \( Q^{-1} A Q =B\). (10 pts)  


### 4. 
Let \( B \in M_{n \times n}(\mathbb{C}) \) be a matrix where the \( i \)-th row is \( e_k \) for some integers \( 1 < i \leq n \) and \( 1 \leq k \leq n \). Prove that  
\[
\det(B) = (-1)^{i+k} \det(\tilde{B}_{ik}),
\]  
You are only allowed to use the definition of the determinant that applies expansion along the first row. (16 pts)  

### 5.
 Consider the matrix  
\[
A = 
\begin{pmatrix}
a & 0 & 0 & -c \\
0 & -d & b & 0 \\
0 & c & a & 0 \\
-b & 0 & 0 & -d
\end{pmatrix}.
\]  
Find an invertible matrix \( S \in M_{4 \times 4}(\mathbb{R}) \) and matrices \( H_1, H_2 \in M_{2 \times 2}(\mathbb{R}) \) such that  
\[
S A S^{-1} = H_1 \oplus H_2.
\]  
(12 pts)  



### 6. 
Apply an orthogonal transformation to transform the quadratic form  
\[
xy + yz + zx = 1
\]  
into a standard form. (8 pts)  



### 7. 
Let \( A \in M_{m \times n}(\mathbb{C}) \) and \( B \in M_{n \times m}(\mathbb{C}) \). Prove that \( I_m - AB \) is invertible if and only if \( I_n - BA \) is invertible. (8 pts)  



### 8. 
For a matrix \( A \in M_{n \times n}(\mathbb{C}) \) with distinct eigenvalues \( \lambda_1, \dots, \lambda_n \), consider the linear operator \( T_A \) on \( M_{n \times n}(\mathbb{C}) \) defined by  
\[
T_A(B) = AB - BA.
\]  
Prove that \( \lambda_i - \lambda_j \) is an eigenvalue of \( T_A \) for \( 1 \leq i < j \leq n \). (12 pts)  
