ExAMPLE $2.11$ (Crouzeix-Raviart element). Let $K$ be a triangle in $\mathbb{R}^2$, $\mathcal{P}=P_1$ the set of linear polynomials, and $\mathcal{N}=\left\{N_1, N_2, N_3\right\}$, where $N_i(v)=$ $v\left(M_i\right)$ and $M_i, i=1,2,3$, are the midpoints of three edges. It is easy to see that $(K, \mathcal{P}, \mathcal{N})$ is a finite element. Define
$$
\hat{V}_h=\left\{v:\left.v\right|_K \in P_1, \quad \forall K \in \mathcal{M}_h, v\right. \text { is continuous }
$$
at the midpoints of the triangle edges $\}$.
Then $\hat{V}_h \subset L^2(\Omega)$ but $\hat{V}_h \not \subset H^1(\Omega) . \hat{V}_h$ is an example of $H^1$-nonconforming finite element spaces.