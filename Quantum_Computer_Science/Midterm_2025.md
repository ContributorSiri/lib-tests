# Quantum Computer Science, Spring 2025 - Midterm

- **Date and Time**: 2025.04.10, 9:50 - 12:20.
- **Open book**. Calculators are not allowed.
- **Total points**: $100+5$.

**Please explicitly write down the derivation process of each problem, otherwise you may lose some marks.**

## Problem 1: Spin Precession ($10$ pts)

Consider a spin-$\dfrac{1}{2}$ particle in magnetic field $\vec B$. The Hamiltonian of the system is given by
$$\hat H=-\gamma \hat{\vec S}\cdot \vec B,$$
where $\gamma$ is the gyromagnetic (回旋磁的) ratio, $\hat{\vec S}=\dfrac{\hbar}{2}\hat{\vec \sigma}$ is the spin operator, $\hat{\vec \sigma}=\hat\sigma_x \vec{e_x}+\hat\sigma_y \vec{e_y}+\hat\sigma_z \vec{e_z}$ is the Pauli operator, and $\vec B$ is the external magnetic field. In this problem, the magnetic field $\vec B$ is along the $z$-axis with magnitude $B_0$, i.e., $\vec B=B_0\vec e_z$. Now, using the Heisenberg equation, find the time revolution of the spin operators $\hat{S_x}(t)$ and $\hat{S_y}(t)$.

## Problem 2: Bloch Sphere ($15$ pts)

For a 2-dimensional qubit system, the density matrix can be written as $\rho=\dfrac{1}{2}(I+\vec r\cdot \hat{\vec \sigma})$, where $\vec r$ is a vector starting from the origin of the coordinates, and $\hat{\vec \sigma}=\hat\sigma_x \vec{e_x}+\hat\sigma_y \vec{e_y}+\hat\sigma_z \vec{e_z}$.

1. Prove that $|\vec r|\le 1$, which means that the ending point of $\vec r$ is within a sphere with radius $1$. ($5$ pts)
2. For a pure state $|\psi\rangle=\cos\dfrac{\theta}{2}|0\rangle+\sin\dfrac{\theta}{2}e^{i\phi}|1\rangle$, derive its $\vec r$ in its density matrix $\rho=\dfrac{1}{2}(I+\vec r\cdot \hat{\vec \sigma})$, and calculate the magnitude $|\vec r|$. ($5$ pts)
3. In the Schrodinger's picture, assume that the Hamiltonian is $\hat H=\hbar(\alpha I+\dfrac{\omega}{2}\vec n\cdot \hat{\vec \sigma})$. Prove that
    $$\dfrac{\text{d}\vec r}{\text{d}t}=\omega \vec n\times \vec r,$$
    which means that $\vec r$ rotates around axis $\vec n$.

## Problem 3: Thermal State in Harmonic Oscillator ($15$ pts)

In a harmonic oscillator, the density matrix of the thermal state can be written as
$$\rho_{\text{th}}=\sum_{n=0}^{+\infty} \dfrac{\alpha^n}{(\alpha+1)^{n+1}}|n\rangle\langle n|,$$
where $|n\rangle$ is the eigenstate of the number operator $\hat n=\hat a^\dagger \hat a$ with eigenvalue $n$.

1. Calculate the average value of the number operator $\bar n=\langle \hat a^\dagger \hat a\rangle$. ($5$ pts)
2. Calculate the entropy of the thermal state $S(\rho_{\text{th}})$. ($10$ pts)

## Problem 4: Schmidt Decomposition ($20$ pts)

Same as Problem 4 in **2024 Midterm**.

## Problem 5: Density Matrix ($20$ pts)

Same as Problem 5 in **2024 Midterm**.

## Problem 6 ($20+5$ pts)