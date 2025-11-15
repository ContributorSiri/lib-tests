## 2025 Fall Intro to Optimization: Midterm

Time: 2025.11.5 9:50 - 12:15

Open book

**Problem 1. Polyhedron [20pts]** Consider the problem of minimizing $c^Tx$ over the set
$$
P=\{x\in\mathbb R^n\mid Ax=b,Dx\le f,Ex\le g\}
$$
Let $x^*\in P$ satisfy $Dx^*=f,Ex^*<g$. Show that the set of feasible directions at point $x^*$ is
$$
\{d\in\mathbb R^n\mid Ad=0, Dd\le 0\}
$$
**Problem 2. Linear duality [20pts]** Consider a standard LP:
$$
\begin{aligned}
\min_x~~&~~c^Tx\\
\text{s.t.}~~~&~~Ax=b\\
			 &~~x\ge 0
\end{aligned}
$$

- Write out its dual form.
- Let $p^*$ be a known optimal dual solution. Explain how to compute the optimal primal solution by solving a linear system.

**Problem 3. Lagrangian duality [20pts]** Let $f:\mathbb R^n\to\mathbf R$ be second-order differentiable, with positive definite Hessian $H:=\nabla^2f(x)\succ 0$. The *Newton decrement* at $x$ is
$$
\lambda(x)^2:=\nabla f(x)^TH^{-1}\nabla f(x)
$$

- Consider the quadratic program
  $$
  \begin{aligned}
  \max_{v\in\mathbb R^n}~~&~~-\nabla f(x)^Tv&\text{s.t.}~~&~~v^THv\le 1
  \end{aligned}
  $$
  Write the Lagrangian and KKT conditions. Show that any maximizer has the form
  $$
  v^*=-\dfrac{H^{-1}\nabla f(x)}{\sqrt{\nabla f(x)^TH^{-1}\nabla f(x)}}
  $$

- Prove the identity 
  $$
  \lambda(x)=\sup_{v\neq 0}\dfrac{-\nabla f(x)^Tv}{(v^THv)^{1/2}}
  $$

**Problem 4. Epigraphs of Convex Polynomials are SDR [40pts]** Fix an integer $k\ge 0$. For ()$y=(y_0,y_1,\cdots,y_{2k})\in \mathbb R^{2k+1}$ define the *Hankel map* $\mathcal M:\mathbb R^{2k+1}\to \mathbf S^{k+1}$ by 
$$
(\mathcal M(y))_{ij}=y_{i+j},~~~~~~~i,j=0,\cdots,k
$$
and equip $\mathbb R^{2k+1}$ with the standard dot product and $\mathbf S^{k+1}$ with the Frobenius inner productor.

The *adjoint* $\mathcal M^*:\mathbf S^{k+1}\to \mathbb R^{2k+1}$ is the unique linear map satisfying $\langle \mathcal M(y),x\rangle = \langle y,\mathcal M^*x\rangle$ for all $y,X$; explicitly, 
$$
(\mathcal M^*x)_{l} = \sum_{i=0}^{l}x_{i,l-i},~~~~~~~l=0,\cdots,2k
$$
 A set $S\subseteq \mathbb R^{m}$ is *spectrahedrally representable (SDR)* if there are symmetric matrices $A_0,A_1,\cdots,A_m,B_1,\cdots,B_r$ such that
$$
S=\{x\in\mathbb R^m\mid \exists z\in\mathbb R^r: A_0+\sum_{i=1}^{m}x_iA_i+\sum_{j=1}^{r}z_jB_j\succeq 0\}
$$
Let $\pi(x)=\sum_{l=0}^{2k}\pi_lx^l$ be a real polynomial of even degree $2k$ that is convex on $\mathbb R$. Denote its epigraph by
$$
\text{epi}(\pi)=\{(t,x)\in\mathbb R^2:t\ge \pi(x)\}
$$
Define
$$
\mathcal X[\pi]=\{(t,x)\mid \exists y_2,\cdots,y_{2k}\text{ such that }\mathcal H(y)\succeq 0,\sum_{l=0}^{2k}\pi_ly_l\le t\}
$$
where $y_0=1,y_1=x$, and $\mathcal H(y)=\mathcal M(y)$ is the Hankel matrix
$$
\mathcal H(y)=\begin{pmatrix}1&x&y_2&\cdots&y_k\\x&y_2&y_3&\cdots&y_{k+1}\\y_2&y_3&y_4&\cdots&y_{k+2}\\\vdots&\vdots&\vdots&\ddots&\vdots\\y_k&y_{k+1}&y_{k+2}&\cdots&y_{2k}\end{pmatrix}
$$
**Assumption (Hilbert's problem).** You may use without proof: the image $\mathcal M^*(\mathbf S_+^{k+1})$ is precisely the set of coefficient vectors of real univariate polynomials of degree $\le 2k$ that are nonnegative on $\mathbb R$.

**1. ** *(Express SDR as LMIs, 10pts)* Given symmetric matrices $A_i,B_j$ which defines a set $S$. Explain how to check whether $S$ is empty through semidefinite programming.

**2.** *(Easy direction: $\text{epi}(\pi)\subseteq \mathcal X[\pi]$, 15pts)* Prove that $\text{epi}(\pi)\subseteq \mathcal X[\pi]$.

**3.** *(Hard direction: $\mathcal X[\pi]\subseteq \text{epi}(\pi)$, 15pts)* Prove that $\mathcal X[\pi]\subseteq \text{epi}(\pi)$. Hint: consider the tangent line at $x$ and the nonnegative polynomial $q(z):=\pi(z)-[\pi(x)+\pi'(x)(z-x)]$.

Putting 2 and 3 together proves
$$
\mathcal X[\pi]= \text{epi}(\pi)
$$
so the epigraph of any univariate convex polynomial of even degree is SDR.

