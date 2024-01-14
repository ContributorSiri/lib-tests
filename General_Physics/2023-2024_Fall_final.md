# General Physics Final

Date: 2024/1/11

Teacher: Luyan Sun

## Short Answer Problems(5 pts each)

1. Directly write down the boundary conditions when the two sides of the interface has dieletric constant $\epsilon_1,\epsilon_2$ (its is $\epsilon_0\epsilon_{r_{1,2}}$ )and magnetic permiability $\mu_0$. You should note the direction of normal vector $\overrightarrow{n}$.
2. Prove that the inpedance of the infinite ladder network is $z_0=\frac{z_1}{2}+\sqrt{\frac{z_1^2}{4}+z_1z_2}$. See the figure below.

![Pict1](/Images/General_Physics/2023-2024_Fall_Final_ladder.png)

3. Prove the wave equations for $E$ and $B$: $\nabla^2\overrightarrow{E}-\frac{1}{c^2}\frac{\partial^2 \overrightarrow{E}}{\partial t^2}=0$ and $\nabla^2\overrightarrow{B}-\frac{1}{c^2}\frac{\partial^2 \overrightarrow{B}}{\partial t^2}=0$.
4. Prove that for a plane wave propogating along the $x$ axis in the vaccum(i.e. the waves have form $e^{ikx-i\omega t}$), the eletric field $E$, the magnetic field $B$, and the unit vector $e_x$ are mutually orthogonal.

## Induced electromotive force(10 pts)

Two coaxial circular coils with radius $R$ and $r$ are placed parallel to each other, with their centers separated by a distance of $x$. The larger coil carries a current $I$. The direction of the current is facing to the right side under the right hand screw rule. Assuming $x\gg r$, the magnetic field produced by the larger coil at the plane of the smaller coil can be treated as a uniform magnetic field. Calculate the induced electromotive force within the smaller coil as it moves parallel to theaxis at a velocity $v$.

## Current and Magnetic Field(10 pts)

Consider a solid cylinder (radius $R$) with a hollow part having radius $r$. The vector pointing from the center of the solid cylinder to the center of the hollow cylinder is $\overrightarrow{a}$, and $a>r$ . Current $I$ flows along the axis of the cylinder.

(a) Find the $\vec{B}$ along the axis of the solid cylinder and the hollow cylinder.

(b) Find the $\vec{B}$ in the hollow part of the pipe.

## Coaxis Transmission line(10 pts)

Consider a coaxial transmission line with inner radius $R_1$ and outer radius $R_2$. Assume the outer shell is perferctly grounded

(a) Calculate the inductance and capacitance per unit length, denoting as $L_0$ and $C_0$.

(b) Use the infinitely small ladder circuit method mentioned in the class to calculate the characteristic polynomial $Z_0$ of the transmission line. You can directly use the results in problem 1(b). If $Z_0=60 \Omega$, find the ratio $\frac{R_2}{R_1}$.(Hint: $\mu_0=4\pi\times 10^{-7} N\cdot A^{-2},c=3\times 10^8 m/s.$)

## AC circuit(10 pts)

Consider the $R-C$ circuit: the AC voltage $u_i=A\sin(\omega t+\phi)$ is exerted on one resistance and one capacitance connecting in series. Let the voltage on the resistance to be $u_o$.

(a) Find $u_o$.  Also find the approximate solution when $\omega CR<<1$. Your final solution should be a real value.

(b) Now consider $u_i$ being an abitary low-frequency signal. Prove that we can write $u_o=k\frac{\text{d}u_i}{\text{d}t}$, and find the value of $k$ in terms of $R$ and $C$.
Hint: we can use the Fourier expansion for an abitary signal:

$$
u_i(t)=\int_{0}^{+\infty}A(\omega)\sin{\omega t}+\int_{0}^{+\infty}B(\omega)\cos{\omega t}
$$

where $A(\omega)$ and $B(\omega)$ are functions respect with $\omega$ and must **not** be regarded as constants. However, for the low-frequency signals, we can change the upper limit from $+\infty$ to a number $\omega_0$ where $\omega_0\ll\frac{1}{CR}$. Notice that you can't regard $A(\omega)$ and $B(\omega)$ as constant in this formula

## Rectangular Cavity(15 pts)

For a rectangular cavity mentioned in class with sides $L_1,L_2,L_3$ along $x,y,z$ axis respectly, solve the Maxwell equations as in class.

(a) Assuming the fields have time-dependence $e^{-i\omega t}$ , find the equations that the electic field must satisfy. Write down the general solutions for $E$. After that, use boundary conditions to simplyfy your answer.

(b) Calculate the resonant frequency $\omega$.

(c) Now assume that $L_1=L_2=L_3=1\text{ cm}$ , find the total number of modes in the range $0.5\text{ cm}\le \lambda \le 2\text { cm}$. Also find the total numbers of permitted wavelengths.

## One-dim Waveguide(15 pts)

A pair of infinitely large parallel ideal conductor plates are separated by distance $b$ and with vacuum inside. Electromagnetic waves propagate along thez-direction parallel to the plates (Perpendicular to the paper, facing inward). The wave is uniform in the $x$-direction, meaning that both the electric and magnetic fields are functions independent of $x$. The $z$-component of the electric feld is given as $E_z(x,y,z,t)=\Phi(y)e^{ik z-i\omega t}$. The TM modes are denoted with two subscripts $m,n$ in rectangular waveguides because they are related to vibrations in the $x-y$ plane, while in parallel plate waveguides, the TM modes are denoted with only one subscript $n$ because they are independent of the $x$ direction.

(a) In the TM mode, what equations and boundary conditions does $E_z$ satisfy? Substitute the provided expression for $E_z$ into the equations and determine the solution for TM modes based on the boundary conditions.

(b) Find the cut-off frequency for each TM mode. What is the lowest cut-off frequency? Is TEM mode able to propogate in this configuration?

(c) For TM modes, find $E_x,E_y,B_x,B_y$. Also find the surface charge density and the surface current.

Hints: You can use the formula below:

$$
E_x=\frac{ik}{\mu_0 \epsilon_0 \omega^2-k^2}\frac{\partial E_z}{\partial x}, E_y=\frac{ik}{\mu_0 \epsilon_0 \omega^2-k^2}\frac{\partial E_z}{\partial y}
$$

$$
B_x=-\frac{i\mu_0 \epsilon_0\omega}{\mu_0 \epsilon_0 \omega^2-k^2}\frac{\partial E_z}{\partial y},B_y=\frac{i\mu_0 \epsilon_0\omega}{\mu_0 \epsilon_0 \omega^2-k^2}\frac{\partial E_z}{\partial x}
$$

## Half-infinite Waveguide(10 pts)

Consider a waveguide in the $z$ direction, and it has side length $a,b$ in $x,y$ directions. It can be sought as a rectangular cavity with the third length $L_3=+\infty$.

(a) Assuming the fields have time-dependence $e^{-i\omega t}$ , find the equations that the electic field must satisfy. Write down the general solutions for $E$. After that, use boundary conditions to simplyfy your answer.

(b) Calculate the cut-off frequency $\omega$ for each mode. What is the lowest cut-off frequency?
