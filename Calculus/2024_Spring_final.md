# Calculus A(2) 2024 Spring Final
## General Information
**time**: 2024-06-20 09:00-11:00

**format**: closed book

**language**: Chinese
## 填空 (3pts * 10)
1. 求积分 
    $$
    \int_0^{\ln 3}dx\int_{x}^{\ln 3}\frac{\sin y}{y}dy=\underline{\hspace{1cm}}.
    $$
2. 求积分$\int_{C^+}e^xdy+ye^xdx=\underline{\hspace{1cm}}$，其中积分路径$C^+$是$y=x^3$的图像，从$(0,0)$到$(1,1)$。
3. 计算$\int_\Omega (x^2+y^2)dxdy=\underline{\hspace{1cm}}$，其中$\Omega=\{(x,y)|x^2+y^2\le 1,0\le x,y\}$
4. 考虑一个矩阵$A$，其特征值为$3,0,-2$。设$f=A(x,y,z)^T$，试求$\nabla\cdot f$的值$\underline{\hspace{1cm}}$.
5. $z=x^2+y^2(0\le z\le 2)$的面积为$\underline{\hspace{1cm}}$.
6. 计算曲线积分$\int xydl=\underline{\hspace{1cm}}$，其中曲线为$(x,y,z)=(2t,t,2-2t)$，$0\le t\le 1$。
7. 求$\sum_{n=1}^{\infty}\frac{x^n}{3^n\ln n}$的收敛半径 $\underline{\hspace{1cm}}$.
8. 判断级数$\sum_{n=1}^{\infty}\frac{(-1)^nn}{n^2+1}$的敛散性：A. 绝对收敛；B. 条件收敛；C. 发散。$\underline{\hspace{1cm}}$.
9. 计算柱面$x^2+y^2=2x$被半球面$x^2+y^2+z^2=4(z\ge 0)$和平面$z=0$截出的面积$\underline{\hspace{1cm}}$.
10. 求 $\ln (3+x)$ 在$x=0$ 处的泰勒级数$\underline{\hspace{1cm}}$，不需指出收敛区间。


## Solve problems (total 70 pts)
1. 设$C^+$是函数$y=\sin x$在$[-\pi,\pi]$上的图像，从$(-\pi,0)$到$(\pi,0)$。计算积分
    $$
    \int_{C^+}(e^{x^2}\sin x^3+\sin y)dx+(x\cos y-y^3)dy
    $$
2. 计算 $\oint_{C^+}(y-z)dx+(z-x)dy+(x-y)dz$，其中$C^+$是柱面$x^2+y^2=2x$和$x+z=1$的交线，且从$x$轴正方向看去，$C^+$是逆时针方向。
3. (12 pts)考虑球体$x^2+y^2+z^2=2z$和$x^2+y^2+z^2=4z$之间的区域$\Omega$，计算 $\iiint_{\Omega}zdxdydz$.
4. (10 pts) 函数$\mathbf{F}(x,y,z)=(x^3-x,y^3-y,z^3-z)^T$。求连续光滑定向曲面$S^+$，外法向为正，使得积分
    $$
    \oiint_{S^+}\mathbf{F}\cdot d\mathbf{S}
    $$
    最小。同时，给出这一最小值。
5. (10 pts) 考虑级数$S(x)=\sum_{n=1}^{\infty}(n-1)x^{n}$。
    1. 求收敛半径。
    2. 求收敛域。
    3. 求和函数。
6. (10 pts) 考虑函数$f(x)=x^2,x\in [-1,1]$。
    1. 计算$f(x)$的周期为2的傅立叶级数。
    2. 利用前一问的结果，计算$\sum_{n=1}^{\infty}\frac{(-1)^{n-1}}{n^2}$的值。

7. (8 pts)判断级数
    $$
    \sum_{n=1}^{\infty}\frac{1+\frac{1}{2}+\cdots+\frac{1}{n}}{n}\cdot \sin n
    $$
    的敛散性，并说明理由。

### 附加题（不计入总评，仅用于评判A+）

设$a_n$是正项数列，记$S_n$为部分和，$S_n=\sum_{k=1}^n a_k$。证明：$\sum_{n=1}^{\infty}a_n$和$\sum_{n=1}^{\infty}\frac{a_n}{S_n}$的敛散性相同。