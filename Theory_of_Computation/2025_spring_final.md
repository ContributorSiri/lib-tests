# Theory of Computation, Spring 2025 - Final

### General Information
- **Date:** 2025/06/03, totally closed book, 13:30-15:30.
- **Choose 6 problems to answer**.

## I 
Consider the following language: 
$$\text{CYCLE}=\langle G,s\rangle\text{|G is a directed simple graph such that vertex s is contained in a directed cycle}$$
Prove that this language is NL-complete.
## II
(1)Prove that $BPP=BPP^{BPP}$
(2)Prove that $NP^{BPP}\subseteq BPP^{NP}$
(3)Prove that if $NP=BPP$ then $PH=BPP$
## III
Consider the random algorithm of deciding whether a number is prime we have introduced on class.Define the  Carmichael number to be a odd composites $n$ which satisfies $$ \forall a \in \mathbb{Z}_{n}^{+}, (a,n)=1, a^{n-1}\equiv 1(\text{mod } n) $$ 
prove that for a odd composite which is not a Carmichael number, the random algorithm has probability greater or equal to $\frac{1}{2}$ to succeed.
## IV
Show that if $P=NP$ then there is a language in $EXP$ that requires circuits of size $\Omega(\frac{2^{n}}{n})$
## V
Consider the following function on $n^2$ boolean variables:
$$f(x_1,x_2,\cdots x_{n^2})=(x_1\vee x_2\vee\cdots\vee x_n )\wedge(x_{n+1}\vee x_{n+2}\vee\cdots\vee x_{2n} )\wedge\cdots\wedge(x_{n(n-1)+1}\vee x_{n(n-1)+2}\vee\cdots\vee x_{n^2} ) $$
decide the decision tree complexity $D(f)$ and the certificate complexity $C(f)$ of this function.
## VI
Define the language $MAJ$ on $n\in \mathbb{N}$ boolean variables iff there are more or equal than a half of the variables are 1.Prove that $MAJ\notin AC_{0}$
## VII
Consider the following problem called APSP problem: Let $G=(V,E,w)$be a weighted directed simple Graph with the set of nodes $V$ and the set of edges $E$, each edge $e\in E$ has a weight $w(e)$assigned.If there are no edge from vertex $i$ to vertex $j$, then the weight of $ij$ is defined to be $+\infty$. We assume there is no directed negative cycle in this graph and the edge weight satisfies $|w(e)|\leq n^{3}$.The goal of the all-pair-shortest-paths problem is to find the shortest path between all pairs of nodes of the graph. 
The APSP conjecture states that for any $\delta>0$, there does not exist a algorithm with $O(n^{3-\delta})$ that solves the APSP problem.
(1)Consider the negative triangle problem which decides whether a simple directed weighted graph has a negative triangle. Prove that if this problem has a truly subcubic algorithm then the APSP conjecture is incorrect.
(2)Consider the following problem: for a simple directed weighted graph $G$ define the following function $$d(G)=\min_{i\in V} \max_{j\in V}d(i,j)$$ where $d(i,j)$ is the distance of the shortest path from $i$ to $j$.Prove that if this problem has a truly subcubic algorithm then the APSP conjecture is incorrect.
