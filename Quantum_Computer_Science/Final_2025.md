# Quantum Computer Science, Spring 2025 - Final

- **Date and Time**: 2025.6.5, 9:50 - 12:20.
- **Open book**. Calculators are not allowed.
- **Total points**: $100$.

**Please explicitly write down the derivation process of each problem, otherwise you may lose some marks.**

## Problem 1 Concepts ($27$ pts)

1. What is a cluster state? Can we correct error happened on the cluster state? Can we use cluster state to achieve universal quantum computing? ($3+3+3=9$ pts)
2. Please explain the derivation of CHSH inequality using the local hidden variable theory. How does quantum mechanical prediction violate this inequality? ($3+3=6$ pts)
3. For a nondegenerate code, what is the minimum number of physical qubit needed to correct arbitrary single-qubit error? Is $[[5,1,3]]$ code degenerate? Explain your reasons. ($3+3=6$ pts)
4. Please explain why ions cannot be trapped using a electrostatic field. ($6$ pts)

## Problem 2 Bell State and Quantum Teleportation ($10$ pts)

1. Consider the following quantum circuit. For inputs $|00\rangle,|10\rangle,|01\rangle,|11\rangle$, the outputs of the circuit are $|\Phi_+\rangle,|\Phi_-\rangle,|\Psi_+\rangle,|\Psi_-\rangle$, respectively. Please write down the four states w.r.t. the computational basis. ($4$ pts)
![](/Images/Quantum_Computer_Science/2025_final/p2-1.png)
2. The idea of quantum teleportation is as follows: for an arbitrary single-qubit state $|\psi\rangle$ hold by Alice, it needs to be teleported to Bob. Suppose Alice and Bob share a Bell state $|\Phi_+\rangle$. First, Alice can measure two qubits hold by her w.r.t. Bell basis, and send the result to Bob (using $2$-bit classical communication). Then, according to the measurement results, Bob can apply some gates to recover $|\psi\rangle$. Please fill in the blanks. ($6$ pts)

| Alice’s measurement result | Bob’s operation |
|----------------------------|-----------------|
| $\Phi_+$                       | ? |
| $\Phi_-$                         | ? |
| $\Psi_+$                        | ? |
| $\Psi_-$                         | ? |

## Problem 3 Quantum Fourier Transform ($11$ pts)

Define the $m$-qubit Fourier transform operation
$$F_m=\dfrac{1}{\sqrt m}\sum_{j,k=0}^{m-1} \omega^{jk}|j\rangle\langle k|,$$
where $\omega$ is the $n$-th primitive unit root $e^{2\pi i/m}$.

1. How does $F_m^2$ act on the computational basis $|0\rangle,|1\rangle,\cdots,|m-1\rangle$? ($5$ pts)
2. Please list **all** eigenstates of $F_m^2$ and their corresponding eigenvalues. ($6$ pts)

## Problem 4 Contiguous Quantum Search ($16$ pts)

In this problem, we will explore quantum search algorithm through a contiguous perspective. In the following questions, we are considering a $n$-qubit system, and the measurement should be done in the computational basis. We further assume the Planck constant is $1$. Let $N=2^n$.

1. Define $|\psi\rangle=\dfrac{1}{\sqrt N}\sum_{x\in \{0,1\}^n}|x\rangle$. For any normalized vector in the computational basis, $|s\rangle$, find a linear combination $|\phi\rangle$ of $|s\rangle$ and $|\psi\rangle$, such that $\{|s\rangle,|\phi\rangle\}$ is an orthonormal basis. ($3$ pts)
2. Suppose we can create an environment with Hamiltonian $H=|s\rangle\langle s|+|\psi\rangle\langle \psi|$. Write $H$ in the outer product form w.r.t. the orthonormal basis in question 1. ($3$ pts)
3. For a time $t>0$, calculate $U(t)=e^{-iHt}$. ($5$ pts)
4. Suppose we first prepare the state $|\psi\rangle$, and let it evolve under the Hamiltonian $H=|s\rangle\langle s|+|\psi\rangle\langle \psi|$ for time $t=T$. After evolution, we measure the result state. What is the probability of "the outcome is $|s\rangle$"? Find $T$ such that this probability is maximized. ($5$ pts)

## Problem 5 $7$-Qubit Steane Code ($16$ pts)

In class, we have discussed the $5$-qubit code to encode $1$-qubit, such that it can correct arbitrary single-qubit error. Now, let us consider a $7$-qubit code. The code space is stabilized by $6$ elements in Pauli group:
$$M_1=X_1X_2X_3X_4,\ M_2=X_2X_3X_5X_6,\ M_3=X_3X_4X_6X_7,\\
M_4=Z_1Z_2Z_3Z_4,\ M_5=Z_2Z_3Z_5Z_6,\ M_6=Z_3Z_4Z_6Z_7.$$
1. Prove that the following two states are stabilized by $\{M_i\}_{1\le i\le 6}$ ($3$ pts):
    $$|0\rangle_L:=\dfrac{1}{2\sqrt 2}(I+M_1)(I+M_2)(I+M_3)|0\rangle^{\otimes 7},$$
    $$|1\rangle_L:=\dfrac{1}{2\sqrt 2}(I+M_1)(I+M_2)(I+M_3)|1\rangle^{\otimes 7}.$$
2. Suppose we have a $Z_i$ error, where $i\in \{1,2,\cdots,7\}$ is unknown. It is known that we can use the error syndrome of $M_1,M_2,M_3$ to recover this error. Fill in the blanks. ($3$ pts)

| $M_1$ | $M_2$ | $M_3$ | Error |
|----------|--------|----------|-----------------|
| + | + | + | No Error |
| + | + | - | $Z_?$ |
| + | - | + | $Z_?$ |
| - | + | + | $Z_?$ |
| + | - | - | $Z_?$ |
| - | + | - | $Z_?$ |
| - | - | + | $Z_?$ |
| - | - | - | $Z_?$ |

3. The logic operators can be defined as
    $$X_L=X_1X_2X_3X_4X_5X_6X_7,$$
    $$Z_L=Z_1Z_2Z_3Z_4Z_5Z_6Z_7.$$
    However, there are other possible definitions of $X_L$ and $Z_L$. What is **the smallest possible weight** for $X_L$ and $Z_L$, respectively? Note that the _weight_ of an element in the Pauli group is the number of qubits it is operated on. ($5$ pts)
4. If the system suffers from a $2$-qubit error $E=Z_2Z_3$. If we detect the error syndrome and correct it using $M_1,M_2,M_3$, what will the final state be? What about $E'=Z_2X_3$? ($5$ pts)

## Problem 6 Clifford Group ($20$ pts)

The $k$-qubit Pauli group $\mathcal P_k$ is defined as
$$\{i^aA_1\otimes A_2\otimes \cdots\otimes A_k:a\in \mathbb Z;A_i\in \{I,X,Y,Z\},1\le i\le k\}.$$
The Clifford group $\mathcal C_k$ is defined as the normalizer of $\mathcal P_k$:
$$\mathcal C_k=\{U:UU^\dagger =I;U\mathcal P_kU^\dagger=\mathcal P_k\}.$$
1. Prove that the Hadamard gate $H$ and $S=\begin{pmatrix}1 & \\ & i\end{pmatrix}$ are both in $\mathcal C_1$; but $T=\begin{pmatrix}1 & \\ & e^{\pi i/4}\end{pmatrix}$ does not. ($6$ pts)
2. Prove that the control-NOT gate is in $\mathcal C_2$. ($4$ pts)
3. Does the Toffoli gate belong to $\mathcal C_3$? ($5$ pts)
4. Does the $2$-qubit Fourier transform $F_4\in \mathcal C_2$? ($5$ pts)
