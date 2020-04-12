Let $Y_1, Y_2, \dots, Y_n$ be a random sample from a distribution $F$，and let $Y_{n1}, Y_{n2}, \dots, Y_{nn}$ denote the order statistics obtained from this sample.  The limit distribution for $Y_{nk}$ that denotes the $k$-th order statistic is depend on the $F$ and the sequence $k(n)$ where $n\to\infty$.

Suppose that $\beta_n Y_{nk}=\frac{Y_{nk}-b_n}{a_n} \to V$, where $V$ is a non-constant random variable, $\beta_n$ is  a positive affine transformation, $a_n>0$, $b_n\in\mathbb{R}$, and $k=k(n)$ is a sequence of integers such that $1\leqslant k\leqslant n$.

*   If $k=n$, then $Y_{nk}$ is the maximum of the sample. Therefore, $V$ is distributed according to one of generalized extreme value distribution. 

*   In this paper, the authors restrict to the case $\min\{k, n-k\}\to \infty$. $Y_{nk}$ is well-known to be asymptotically normal if $F$ is the uniform distribution on $(0,1)$. The distribution of $Y_{nk}$ is 

$$
P(Y_{nk}\leqslant x) = \int_0^x t^{k-1}(1-t)^{n-k}dt/B(k,n+1-k) \quad for\quad  0\leqslant x \leqslant 1.
$$
​		where $B(\cdot)$ is Beta distribution.

*   If $k/n \to p \in (0,1)$ so that $\sqrt{n}(k/n-p)$ converges to a constant $t \in \mathbb{R}, t=-c\sqrt{p(1-p)}$, then $V$ is distributed like $\varphi(U)$, where $U$ is standard normal and $\varphi \in \Phi_c$ for some $c \leqq \infty$.

