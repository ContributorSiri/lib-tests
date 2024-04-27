# Quantum Computer Science, Spring 2024 - Midterm

2024.04.25 9:50 - 12:35, 6A117

Please explicitly write down the derivation process of each problem, otherwise you might lose some marks. You are allowed to use results from homework without proving them, as long as you CLEARLY state what results you used.

## I Coherent state (20 pts)

In a quantum harmonic oscillator, a coherent state $|\alpha\rangle$ is defined the eigenstate of the annihilation operator $\hat a$ with eigenvalue $\alpha\in \mathbb C$,
$$
\hat a|\alpha\rangle = \alpha|\alpha\rangle.
$$
(1) Expand the coherent state $|\alpha\rangle$ in the Fock basis $\{|n\rangle\}$, the eigenstates of $\hat n = \hat a^\dagger \hat a$.  
(2) Show that $|\alpha\rangle$ is a minimal uncertainty state.  
(3) Suppose at time $t=0$ the harmonic oscillator is in state $|\alpha\rangle$. Prove that under the evolution of Hamiltonian
$$
\hat H = \frac{{\hat p}^2}{2m} + \frac{1}{2}m\omega^2{\hat x}^2 = \hbar\omega(\hat a^\dagger \hat a + \frac{1}{2}),
$$
the state at time $t$, $|\alpha(t)\rangle = \exp(-i\hat Ht/\hbar)|\alpha\rangle$ is also a coherent state, and find the corresponding eigenvalue $\alpha(t)$.

## II Heisenberg equations (10 pts)

A particle with mass $m$ and charge $q$ moves along the $x$-axis in a uniform electric field $\boldsymbol E = E \boldsymbol e_x$. We know that initially ($t=0$), $\langle \hat x(0) \rangle = 0, \langle\hat p_x (0)\rangle = p(0)$. Please calculate $\langle \hat x(t) \rangle, \langle \hat p_x(t) \rangle$ with Heisenberg equation.

## III Amplitude damping of harmonic oscillator (20 pts)

Suppose our principal system (a harmonic oscillator) interacts with the environment, which is another oscillator, with the Hamiltonian
$$
H = \chi (\hat a^\dagger \hat b + \hat a \hat b^\dagger),
$$
with $\hat{a} , \hat{a^\dagger} (\hat{b} , \hat{b^\dagger})$ being the annihilation/creation operators of the principal system (the environment). The non-trivial commutaion relations are $[\hat a, \hat a^\dagger] = [\hat b, \hat b^\dagger] = 1$, and others are zero.

(1) We use $|n_a, n_b\rangle = |n_a\rangle |n_b\rangle$ to denote the eigenstates of $\hat a^\dagger \hat a$ and $\hat b^\dagger \hat b$, with eigenvalue $n_a$ and $n_b$ respectively. Show that $H$ commutes with $\hat a^\dagger \hat a + \hat b^\dagger \hat b$.

(2) Suppose the initial state of the system is $|n,0\rangle$. From the conclusion of question(1), the state after the evolution is in the subspace spanned by $|n-k,k\rangle$, which we denote by $|\bar k\rangle$. Write down $H$ in terms of $\sum_{i,j} H_{ij} |\bar i\rangle \langle \bar j|$.

(3) Consider a system consist of $n$ qubits. Define the symmetry subspace $\mathcal{H}_{sym}$ where permutes any of the qubits does not change the state (and will not introduce a global phase). For example, $\frac{1}{\sqrt{2}} (|00\rangle+|11\rangle)$ is in the symmetric subspace, but $|10\rangle$ is not, since exchanging the two qubits gives $|01\rangle$. Let $\psi_k\in \mathcal{H}_{sym}$ being the *normalized* eigenstates of $\sum \frac{1}{2} (I-Z_i) with eigenvalue $k$. Write down $\psi_k$ in terms of the sum of computational basis.
