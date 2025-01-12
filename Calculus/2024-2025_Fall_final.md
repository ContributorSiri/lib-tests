# 2024-2025 微积分 A(1) 期末考试

一、填空题。（每题 $3$ 分，共 $30$ 分）

1. 曲线段 $y=\dfrac{2}{3}x\sqrt x$ ($0\le x\le 8$) 的弧长为 $\underline{\qquad}$.
2. 曲线 $y=x+x^2\sin \dfrac{1}{x^2+1}$ 的渐近线为 $\underline{\qquad}$.
3. 求 $\lim\limits_{x\to 0}\dfrac{x-\sin x}{\int_0^x \dfrac{\ln (1+t^3)}{t}dt}=$ $\underline{\qquad}$.
4. 函数 $f(x)=x(1-x)^{2/3}$ ($0<x<1$) 在 $x=$ $\underline{\qquad}$ 处取得最大值.
5. 广义积分 $\int_0^1 \dfrac{(-\ln x)^p}{\sqrt x(1-x)^2}dx$ 收敛. 那么，$p$ 的取值范围是 $\underline{\qquad}$.
6. 对实数 $x$ 求 $\int_0^x |e^t-1|dt=$ $\underline{\qquad}$.
7. 求 $\int_0^{\pi/2} \dfrac{dx}{3\sin^2 x+\cos^2 x}=$ $\underline{\qquad}$.
8. 微分方程初值问题 $\begin{cases}(1+e^x)yy'=e^x\\y(0)=\sqrt{2\ln 2}\end{cases}$ 的解是 $y(x)=$ $\underline{\qquad}$.
9. 求 $\lim\limits_{n\to \infty} \dfrac{1^3+2^3+\cdots+n^3}{n(1^2+2^2+\cdots+n^2)}=$ $\underline{\qquad}$.
10. 微分方程 $x^2y''+xy'-4y=0$ 的通解是 $\underline{\qquad}$.

二、解答题。

11. （$12$ 分）设 $f(x)=xe^{-x^2}$ ($x>0$). 求 $f(x)$ 的单调区间、极值点、极值、凹凸性区间、拐点、渐近线；画出曲线 $y=f(x)$ 的草图.

12. （$10$ 分）当参数 $p>0$ 满足什么条件时，广义积分
    $$\int_1^{+\infty} \left(\dfrac{x}{x^2+p}-\dfrac{p}{x+1}\right)dx$$
    收敛？并求出此时的广义积分值.
13. （$10$ 分）通过变量代换 $x=\sin t$, $t\in (-\dfrac{\pi}{2},\dfrac{\pi}{2})$，化简以下微分方程并求解.
    $$(1-x^2)\dfrac{d^2y}{dx^2}-x\dfrac{dy}{dx}+y=0,\quad -1<x<1.$$
14. （$10$ 分）记圆周 $\begin{cases}x=2+\cos t\\y=\sin t\end{cases}$ ($0\le t\le 2\pi$) 绕 $y$ 轴旋转一周所得的旋转面为 $S$. 求 $S$ 的面积，以及由 $S$ 所包围的旋转体的体积.
15. （$10$ 分）设 $I=\int_0^2 \dfrac{x}{e^x+e^{2-x}}dx$. 

    (1) 求证：$I=\int_0^2 \dfrac{dt}{e^t+e^{2-t}}$;\
    (2) 求 $I$ 的值.
16. （$10$ 分）设函数 $f(x)$ 在 $[0,+\infty)$ 上可导, $f(0)=1$, 且满足
    $$(x^2+1)f'(x)+(x^2+1)f(x)-2\int_0^x tf(t)dt=0.$$
    (1) 求 $f'(x)$ 的表达式;\
    (2) 求证：当 $x\in [0,+\infty)$ 时，$e^{-x}\le f(x)\le 1$.
17. （$8$ 分）设 $x\in (0,1)$. 求证：

    (1) 对任意正整数 $n$，均有
        $$\dfrac{n^x\cdot n!}{(x+1)\cdots (x+n)}<1;$$
    (2) 以下极限
        $$\lim_{n\to \infty} \dfrac{n^x\cdot n!}{(x+1)\cdots(x+n)}$$
        存在（有限）.

三、附加题。（仅用于评判 A+；仅有**完全正确**和**错误**两种成绩）

18. 已知定义在 $(0,+\infty)$ 上的函数 $f(x)$ 满足：

- $f(x)>0$;
- $f(1)=1$, $f(x+1)=xf(x)$;
- $\varphi(x):=\ln f(x)$ 是下凸函数.

求证：当 $0<x<1$ 时,
$$f(x)=\lim_{n\to +\infty} \dfrac{n^x\cdot n!}{x(x+1)\cdots(x+n)}.$$