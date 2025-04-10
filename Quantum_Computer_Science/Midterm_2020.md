# Quantum Computer Science, Spring 2020 - Midterm

## Problem 1: The Bloch sphere picture for mixed states ($15$ pts)

1. Show that, an arbitrary density matrix of a mixed state qubit can be written as
    $$\rho=\dfrac{I+\vec r\cdot \hat{\vec \sigma}}{2},$$
    where $\vec r$ is a real 3-dimensional vector satisfying $|\vec r|\le 1$. This vector is known as the **Bloch vector** for the state $\rho$. ($7$ pts)
2. What is the Bloch vector representation for the state $\rho=I/2$? ($3$ pts)
3. Show that a state $\rho$ is pure if and only if $|\vec r|=1$. ($5$ pts)

## Problem 2: Harmonic Oscillator ($20$ pts)

Let $|\alpha\rangle$ denote the eigenstate of the annihilation operator $a$, with eigenvalue $\alpha\in \mathbb C$.

1. Expand the coherent state in Fock basis $|n\rangle$. ($10$ pts)
2. Prove that, the probability distribution of the photons in a coherent state, i.e., the probability of detecting $n$ photons in a coherent state, is a Poissonian distribution. ($5$ pts)
3. Prove that, coherent state satisfies the minimum uncertainty relation in terms of $\hat x$ and $\hat p$. ($5$ pts)

**Hint.** You can use the following relations: $a|n\rangle=\sqrt{n}|n-1\rangle$, $a^\dagger |n\rangle=\sqrt{n+1}|n+1\rangle$,
$$\hat x=\sqrt{\dfrac{\hbar}{2m\omega}}(a+a^\dagger),\quad \hat p=i\sqrt{\dfrac{m\omega\hbar}{2}}(a^\dagger-a).$$

## Problem 3: Evolution of a 2-Level System ($20$ pts)

The evolution of a 2-level system is described by the master equation
$$\dot \rho=\gamma_1\left(\sigma_-\rho\sigma_+-\dfrac{1}{2}\{\sigma_+\sigma_-,\rho\}\right)+\gamma_2\left(\sigma_z\rho\sigma_z-\rho\right),$$
where $\sigma_{\pm}=\dfrac{1}{2}(\sigma_x\pm i\sigma_y)$.
1. If the density operator is expanded with Pauli matrices $\rho=\dfrac{1}{2}(I+u\sigma_x+v\sigma_y+w\sigma_z)$, find the evolution equation for the expansion parameters $u,v,w$. ($10$ pts)
2. Let the lifetime of the excited state be $T_1$, and the de-coherence time of equal superposition of two levels is called $T_2$ (Both fit by an exponential curve). Express $T_1$ and $T_2$ for this 2-level system in terms of parameters $\gamma_1$ and $\gamma_2$. ($10$ pts)

## Problem 4: Density Matrix ($20$ pts)

For the 3-particle $W$ state
$$|\Psi_1\rangle_{ABC}=\dfrac{1}{\sqrt 3}(|001\rangle+|010\rangle+|100\rangle)$$
and the GHZ state
$$|\Psi_1\rangle_{ABC}=\dfrac{1}{\sqrt 2}(|000\rangle+|111\rangle),$$
find the two-particle reduced density operators $\rho_{1AB}$ and $\rho_{2AB}$. ($10$ pts) What is the amount of entanglement between $AB$ and $C$ (in terms of von-Neumann entropy) for these two states? ($10$ pts)

## Problem 5: Basis Operators for Qubit Systems ($15$ pts)

For qubit with basis vectors $|j\rangle =|0\rangle, |1\rangle,\cdots,|d-1\rangle$, define the operators $X_d$ and $Z_d$ as follows:
$$Z_d|j\rangle =\omega^j|j\rangle,\quad \omega=e^{2\pi i/d},$$
$$\begin{cases}X_d|j\rangle =|j+1\rangle\ (0\le j\le d-1),\text{ and}\\ X_d|d-1\rangle =|0\rangle.\end{cases}$$
1. Prove that $X_d^d=Z_d^d=I$. ($5$ pts)
2. Prove that $X_dZ_d=\omega^{-1}Z_dX_d$. ($5$ pts)
3. On a 1-dimensional lattice of $n$-qubits, define the $d$-dimensional cluster state. ($5$ pts)

## Problem 6 : Schmidt Decomposition ($10$ pts)

Find the Schmidt decompositions of the following two states
$$|\phi_1\rangle=\dfrac{|00\rangle +|01\rangle +|10\rangle -|11\rangle}{2},$$
$$|\phi_2\rangle=\dfrac{|00\rangle+|01\rangle+|11\rangle}{\sqrt 3}.$$