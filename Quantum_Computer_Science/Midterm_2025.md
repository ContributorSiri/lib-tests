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

## Problem 6 Transformation Between Pictures ($20+5$ pts)

The Schrodinger picture of a quantum system describes the evolution as
$$i\hbar \frac{\partial}{\partial t}|\phi(t)\rangle_S=\hat{H}|\phi(t)\rangle_S,$$
while the Heisenberg picture models it as
$$\frac{d}{dt}A(t)_H=\frac{i}{\hbar}[A(t)_H,\hat{H}].$$
Now, we consider the **interaction picture**, which is different from the two pictures.

1. for a potential $V(\hat{x}(t))$ which only depend on the particle's position $x$, the Hamiltonian for the particle can be written as
    $$H=\frac{\hat{p}^2}{2m}+V(\hat{x}(t)).$$
    Prove the Ehrenfest theorem ($10$ pts):
    $$\langle m\frac{d^2}{dt^2}\hat{x}(t)\rangle=-\langle\nabla V(\hat{x}(t)) \rangle.$$
2. Consider a system with the Hamiltonian $H=H_0+H_1$, where $H_1$ is relatively small compare to $H_0$ and $H_0$ is independent of time. Here, $H_1$ can be interpreted as a "preturbation". Consider the following interaction picture:
    $$|\phi(t)\rangle_{I}=e^{\frac{i\hat{H}_0t}{\hbar}}|\phi(t)\rangle_S,$$
    $$A(t)_I=e^{\frac{i\hat{H}_0t}{\hbar}}A(t)_Se^{-\frac{i\hat{H}_0t}{\hbar}}.$$
    Derive the equation of $|\phi(t)\rangle_I$ and $A(t)_I$ under the time evolution.
3. Consider the following system: an atom of three energy level $(a,b,c)$ is in a cavity and coupling with a photon which is in possibly two modes, with frequency $\nu_1,\nu_2$, and the total state of the system in general has the following form:
    $$|\phi\rangle=c_1(t)|a\rangle|0\rangle|0\rangle+c_2(t)|b\rangle|1\rangle|0\rangle+c_3(t)|c\rangle|0\rangle|1\rangle.$$
    The hamiltonian of the system without coupling between the atom and the photon is
    $$H_0=\hbar\omega_1|a\rangle\langle a|+\hbar\omega_2|b\rangle\langle b|+\hbar\omega_3|c\rangle\langle c|+\hbar\nu_1a^{\dagger}_1a_1+\hbar\nu_2a^{\dagger}_2a_2.$$
    The coupling between the atom and the photon only allows transition between energy level $a$ and $b$, and energy level $a$ and $c$. Thus, the interaction Hamiltonian can be written as:
    $$H_I=\hbar g_1(|a\rangle\langle b|a_1+|b\rangle\langle a|a^{\dagger}_1)+\hbar g_2(|a\rangle\langle c|a_2+|c\rangle\langle a|a^{\dagger}_2).$$
    Now we consider a system that stays in $c_1(t)=0$ for a long period of time. We call the state a "dark state". Derive the probability to find the atom in state $|b\rangle$ and $|c\rangle$ respectively when observing a system that is in a dark state. ($5$ pts, **bonus**)