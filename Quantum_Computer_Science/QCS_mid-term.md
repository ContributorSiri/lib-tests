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

(4) Define a Hamiltonian on $n$ qubits
$$
H' = \chi \sum_{i} X_i.
$$
$H'$ maps states in $\mathcal{H}_{sym}$ into $\mathcal{H}_{sym}$. Write down the action of $H'$ in the symmetry subspace, in terms of $H' = \sum_{i,j} H'_{ij} |\psi_i\rangle \langle \psi_j|$.

(5) Suppose the initial state of the two-oscillator system is $|\bar 0\rangle = |n,0\rangle$. Compare the results in (2) and (4) and use your result to compute $\langle \bar k | \exp(-iHt)|\bar 0\rangle$.

## IV Schmidt decomposition (15 pts)

Suppose a two particle pure state is of the form
$$
|\psi_{AB}\rangle = \frac{1}{\sqrt{2}}|0\rangle(\frac{1}{\sqrt{3}}|0\rangle + \frac{\sqrt{2}}{\sqrt{3}}|1\rangle) + \frac{1}{\sqrt{2}}|1\rangle(\frac{\sqrt{2}}{\sqrt{3}}|0\rangle + \frac{1}{\sqrt{3}}|1\rangle).
$$
(1) Calculate the reduced density matrices $\rho_A$ and $\rho_B$.  
(2) Do Schmidt decomposition.  
(3) Is there a Schmidt decomposition for an arbitrary tripartite pure state? That is, if $|\Psi_{ABC}\rangle$ is an arbitrary vector in $H_A \otimes H_B \otimes H_C$, can we find orthonormal bases $\{|i\rangle_A\}, \{|j\rangle_B\}$ and $\{|k\rangle_C\}$ such that
$$
\Psi_{ABC} = \sum_{i} C_i |i\rangle_A \otimes |i\rangle_B \otimes |i\rangle_C?
$$
Explain your answer.

## V Density Matrix

Consider a qubit with density matrix $\rho = a(I+|+\rangle\langle +| - b |0\rangle\langle 0|)$, where $I$ is the identity matrix, and $|+\rangle = \frac{1}{\sqrt{2}}(|0\rangle + |1\rangle)$.  
(1) For a given $b$, what is the value of $a$ that makes $\rho$ a valid density matrix? And what are the possible values of $b$?  
(2) For $b=0$, give a way of creating this state by mixing pure states with different classical probabilities.  
(3) For $b=0$, find $2$ different purifications that give this density matrix as its reduced density matrix.  
(4) For $b=1$, consider a set of POVM $\{E_0, E_1, E_2, E_3\}$ on the state $\rho$, where
$$
E_0 = u|0\rangle\langle 0|, E_1 = u|1\rangle\langle 1|, E_2 = u|+\rangle\langle +|, E_3 = u|-\rangle\langle -|
$$
where $|-\rangle=\frac{1}{\sqrt{2}}(|0\rangle - |1\rangle)$. Determine the value $u$ and give the measurement probabilities of each of the four outcomes.

## VI Spin echo (15 pts)

Realist qubits are often subject to qubit frequency noise, which can in part be mitigated by a method called Spin Echo. In a spin echo sequence, the qubit is first allowed to evolve for a time $t_0$, then a instantaneous bit flip with evolution operator $U=\mathrm{e}^{-i\pi \sigma_y/2}$ is applied to the qubit, and the qubit is allowed to evolve for another $t_0$. Now consider a qubit with initial pure state $|\psi\rangle = |+\rangle$.

(1) The qubit could have a constant but unknown frequency offset $\delta$, which makes its Hamiltonian
$$
H=\frac{1}{2} \hbar \delta \sigma_z.
$$
Show that after a spin echo sequence, the final state is independent of $\delta$.

(2) Now, if the qubit has no frequency offset($\delta=0$), but is subject to a phase damping channel described by jump operator $L=\sqrt{\gamma} \sigma_z$. Show that after a spin echo sequence, the final state is no longer a pure state

(3) From the above calculation, what type of nois eis spin echo more effective at suppressing? Slow-varying frequency drift or white-noise frequency noise? Give your reasons.
