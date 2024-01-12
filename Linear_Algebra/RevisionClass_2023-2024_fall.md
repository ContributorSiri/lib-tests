## 2023-2024 线性代数期末复习会题目
1. 考虑线性空间 $V=M_{n\times n}(\mathbb{C})$. 在 $V$ 上定义内积 $\langle A,B\rangle=\text{tr}(A^T\overline{B})$. 对任意 $M\in V$, 定义线性变换 $T_M$ 满足 $T_M(X)=MX$；线性变换 $U_M$ 满足 $U_M(X)=$M^TXM$.     
(1) 证明：$M$ 是酉矩阵等价于 $T_M$ 是酉变换；    
(2) 设 $M$ 可逆，证明：$M$ 可对角化等价于 $U_M$ 可对角化.

2. 已知分块矩阵 $O = \begin{bmatrix} A & B\\ C & D\\ \end{bmatrix}$ 是正交实矩阵，其中 $A,D$ 是方阵. 若 $\text{det}(O)=1$，证明：$\text{det}(A)=\text{det}(D)$.

3. 证明：对任意满足 $\text{tr}(A)=\text{tr}(B)$ 的正定厄米矩阵 $A,B$，均有
$$\text{tr}(A\log A-A\log B)\ge 0.$$

4. 设 $P$ 是 $n\times n$ 的正定矩阵，$A$ 是 $p\times n$ 矩阵. 证明：若分块矩阵 $M = \begin{bmatrix} P & A^T\\ A & O\\ \end{bmatrix}$ 可逆，则其特征值一定 $n$ 正 $p$ 负.    
**提示.** 考虑 $M\to Q^{-1}MQ, Q^{T}MQ$ 对 $M$ 特征值的影响.