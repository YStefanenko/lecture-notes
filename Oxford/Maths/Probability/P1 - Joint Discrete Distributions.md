Prelims Probability, Chapter 2.4. Back to [[P1]]. Builds on [[P1 - Discrete Random Variables]].

$\mathbb{P}(X = x)$ and $\mathbb{P}(Y = y)$ alone don't determine how $X$ and $Y$ behave together (think $Y = X^2$).

> **Definition 2.16 (Joint p.m.f.)**
> $$p_{X,Y}(x, y) = \mathbb{P}(\{X = x\} \cap \{Y = y\}) = \mathbb{P}(X = x, Y = y), \quad x, y \in \mathbb{R}.$$
> $p_{X,Y} \geq 0$ and $\sum_x\sum_y p_{X,Y}(x, y) = 1$.

**Marginals:** $p_X(x) = \sum_y p_{X,Y}(x, y)$ and $p_Y(y) = \sum_x p_{X,Y}(x, y)$, named for the margins of the joint table.

> [!example]- Examples 2.17 & 2.18 (a joint table)
> | | $X = 0$ | $X = 1$ | $p_Y(y)$ |
> |---|---|---|---|
> | $Y = 0$ | $\frac13$ | $\frac12$ | $\frac56$ |
> | $Y = 1$ | $\frac1{12}$ | $\frac1{12}$ | $\frac16$ |
> | $p_X(x)$ | $\frac5{12}$ | $\frac7{12}$ | |
> 
> $\mathbb{P}(X = 1, Y = 1) = \frac1{12} \neq \frac7{12}\cdot\frac16$, so $\{X = 1\}$ and $\{Y = 1\}$ aren't independent.
> 
> **2.18** $p_{Y|X=0}(0) = \frac{1/3}{5/12} = \frac45$, $p_{Y|X=0}(1) = \frac15$, so $\mathbb{E}[Y|X = 0] = \frac15$.

**Conditional p.m.f.** For $p_X(x) > 0$:
$$p_{Y|X=x}(y) = \mathbb{P}(Y = y | X = x) = \frac{p_{X,Y}(x, y)}{p_X(x)}, \qquad \mathbb{E}[Y|X = x] = \sum_y y\,p_{Y|X=x}(y).$$

> **Definition 2.19 (Independent random variables)**
> Discrete $X$ and $Y$ are **independent** if $\mathbb{P}(X = x, Y = y) = \mathbb{P}(X = x)\mathbb{P}(Y = y)$ for all $x, y$, i.e. $p_{X,Y}(x, y) = p_X(x)p_Y(y)$.

> [!example]- Example 2.20 (lengths of runs of coin flips)
> Heads with probability $p$, tails $q = 1 - p$. $U$ = length of the first run, $V$ = length of the second. Conditioning on the first flip:
> $$\mathbb{P}(U = m, V = n) = p\,p^{m-1}q^n p + q\,q^{m-1}p^n q = p^{m+1}q^n + q^{m+1}p^n.$$
> Summing: $\mathbb{P}(U = m) = p^m q + q^m p$, $\mathbb{P}(V = n) = p^2 q^{n-1} + q^2 p^{n-1}$.
> The joint p.m.f. doesn't factorise unless $p = q = \frac12$, so $U, V$ are dependent. Intuitively, if $p < \frac12$, a short first run is probably heads, making the second (tails) run likely long: they're negatively correlated.

**Expectation of a function of two r.v.s** (as in Theorem 2.8):
$$\mathbb{E}[h(X, Y)] = \sum_x\sum_y h(x, y)\,p_{X,Y}(x, y), \tag{2.2}$$
provided the sum converges absolutely.

> **Theorem 2.21 (Linearity of expectation)**
> If $\mathbb{E}[X]$ and $\mathbb{E}[Y]$ exist, then $\mathbb{E}[aX + bY] = a\,\mathbb{E}[X] + b\,\mathbb{E}[Y]$.

> [!proof]- Proof
> With $h(x, y) = ax + by$ in (2.2):
> $$\sum_x\sum_y(ax + by)p_{X,Y} = a\sum_x x\sum_y p_{X,Y} + b\sum_y y\sum_x p_{X,Y} = a\sum_x x\,p_X(x) + b\sum_y y\,p_Y(y). \quad \square$$

By induction $\mathbb{E}[a_1X_1 + \dots + a_nX_n] = \sum a_i\mathbb{E}[X_i]$. **No independence needed.**

> [!example]- Example 2.22 (spaghetti loops: linearity with indicators)
> $n$ strands, so $2n$ ends. Repeatedly join 2 random ends. With $k$ ends left, a loop forms with probability $\frac{1}{k-1}$. Before step $i$ there are $2(n - i + 1)$ ends, so with $X_i$ = indicator of a loop at step $i$, $\mathbb{E}[X_i] = \frac{1}{2(n-i) + 1}$. The number of loops is $M = X_1 + \dots + X_n$, so
> $$\mathbb{E}[M] = \frac{1}{2n-1} + \frac{1}{2n-3} + \dots + \frac13 + 1 \quad (\approx \tfrac12\log n \text{ for large } n).$$
> The p.m.f. of $M$ is hard to find, but linearity makes the expectation easy.

> **Theorem 2.23**
> If $X, Y$ are independent and their expectations exist, then $\mathbb{E}[XY] = \mathbb{E}[X]\,\mathbb{E}[Y]$.

> [!proof]- Proof
> $$\mathbb{E}[XY] = \sum_x\sum_y xy\,\mathbb{P}(X = x)\mathbb{P}(Y = y) = \Big(\sum_x x\,\mathbb{P}(X = x)\Big)\Big(\sum_y y\,\mathbb{P}(Y = y)\Big). \quad \square$$

## Covariance

> **Definition (Covariance)**
> $$\operatorname{cov}(X, Y) = \mathbb{E}\big[(X - \mathbb{E}[X])(Y - \mathbb{E}[Y])\big].$$
> Note $\operatorname{cov}(X, X) = \operatorname{var}(X)$.

**Exercises 2.24 – 2.25:**
- $\operatorname{cov}(X, Y) = \mathbb{E}[XY] - \mathbb{E}[X]\,\mathbb{E}[Y]$.
- $\operatorname{var}(X + Y) = \operatorname{var}(X) + \operatorname{var}(Y) + 2\operatorname{cov}(X, Y)$.
- So if $X, Y$ are independent, $\operatorname{cov}(X, Y) = 0$ and $\operatorname{var}(X + Y) = \operatorname{var}(X) + \operatorname{var}(Y)$.

**WARNING: $\operatorname{cov}(X, Y) = 0$ does NOT imply $X$ and $Y$ are independent.**

## Many Random Variables

> **Definition 2.26 (Multivariate p.m.f.)**
> $p_{X_1, \dots, X_n}(x_1, \dots, x_n) = \mathbb{P}(X_1 = x_1, \dots, X_n = x_n)$.

> **Definition 2.27 (Independent family; i.i.d.)**
> $\{X_i : i \in I\}$ are **independent** if for all finite $J \subseteq I$ and all subsets $A_i \subseteq \mathbb{R}$,
> $$\mathbb{P}\Big(\bigcap_{i \in J}\{X_i \in A_i\}\Big) = \prod_{i \in J}\mathbb{P}(X_i \in A_i).$$
> Independent r.v.s with the same distribution are **independent and identically distributed (i.i.d.)**.
