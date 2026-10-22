Prelims Probability, Appendix. Back to [[P1]].

## Useful Analysis (A.1)

Covered properly in Analysis I: [[A1 - Countability]], [[A1 - Sequences and Convergence]], [[A1 - Infinite Series]], [[A1 - Power Series]].

- **Countable:** finite, or listable as $\{x_1, x_2, \dots\}$. $\mathbb{N}$ and $\mathbb{Q}$ are countable; $\mathbb{R}$ is not.
- **Absolute convergence** ($\sum |a_k| < \infty$) implies convergence, and makes the sum independent of the order of the terms. This is why expectations need absolute convergence. E.g. $1 - \frac12 + \frac13 - \dots = \ln 2$, but reordered as $1 + \frac13 - \frac12 + \frac15 + \frac17 - \frac14 + \dots$ it sums to $\frac32\ln 2$.
- **Power series** $\sum c_k x^k$ converge absolutely for $|x| < R$ and can be differentiated term by term there: $f'(x) = \sum (k+1)c_{k+1}x^k$. For p.g.f.s, $R \geq 1$.

**Series identities:**
- Geometric ($0 \leq r < 1$): $\sum_{k=0}^{n-1}ar^k = \frac{a(1 - r^n)}{1 - r}$ and $\sum_{k=0}^\infty ar^k = \frac{a}{1 - r}$.
- Exponential: $\sum_{n=0}^\infty \frac{\lambda^n}{n!} = e^\lambda$.
- Binomial: $(x + y)^n = \sum_{k=0}^n \binom nk x^k y^{n-k}$.
- Differentiate or integrate them, e.g. $\sum_{k \geq 1} k r^{k-1} = \frac{d}{dr}\sum_{k \geq 0} r^k$ and $\sum_{k \geq 1}\frac{r^k}{k} = \int_0^r \sum_{k \geq 0} t^k\,dt$.

## Increasing Sequences of Events (A.2)

> **Proposition A.8 (Continuity of $\mathbb{P}$)**
> If $A_1 \subseteq A_2 \subseteq A_3 \subseteq \dots$ then
> $$\mathbb{P}\Big(\bigcup_{n=1}^\infty A_n\Big) = \lim_{n \to \infty}\mathbb{P}(A_n).$$

> [!proof]- Proof
> Write the union disjointly as $A_1 \cup \bigcup_{k \geq 2}(A_k \setminus A_{k-1})$, and $A_n = A_1 \cup (A_2 \setminus A_1) \cup \dots \cup (A_n \setminus A_{n-1})$. By countable additivity (P3):
> $$\mathbb{P}\Big(\bigcup A_k\Big) = \mathbb{P}(A_1) + \sum_{k=2}^\infty \mathbb{P}(A_k \setminus A_{k-1}) = \lim_{n \to \infty}\Big[\mathbb{P}(A_1) + \sum_{k=2}^n \mathbb{P}(A_k \setminus A_{k-1})\Big] = \lim_{n \to \infty}\mathbb{P}(A_n). \quad \square$$

Used for: hitting probabilities of random walks (Theorem 3.15) and the extinction probability of branching processes (4.2).

## Common Discrete Distributions

| Distribution | p.m.f. | Mean | Variance | p.g.f. |
|---|---|---|---|---|
| Uniform $U\{1, \dots, n\}$ | $\frac1n$, $1 \leq k \leq n$ | $\frac{n+1}{2}$ | $\frac{n^2 - 1}{12}$ | $\frac{s - s^{n+1}}{n(1-s)}$ |
| $\text{Ber}(p)$ | $\mathbb{P}(1) = p$, $\mathbb{P}(0) = 1 - p$ | $p$ | $p(1-p)$ | $1 - p + ps$ |
| $\text{Bin}(n, p)$ | $\binom nk p^k(1-p)^{n-k}$ | $np$ | $np(1-p)$ | $(1 - p + ps)^n$ |
| $\text{Po}(\lambda)$ | $\frac{\lambda^k}{k!}e^{-\lambda}$ | $\lambda$ | $\lambda$ | $e^{\lambda(s-1)}$ |
| $\text{Geom}(p)$, $k \geq 1$ | $(1-p)^{k-1}p$ | $\frac1p$ | $\frac{1-p}{p^2}$ | $\frac{ps}{1 - (1-p)s}$ |
| Alt. geometric, $k \geq 0$ | $(1-p)^k p$ | $\frac{1-p}{p}$ | $\frac{1-p}{p^2}$ | $\frac{p}{1 - (1-p)s}$ |
| $\text{NegBin}(k, p)$, $n \geq k$ | $\binom{n-1}{k-1}(1-p)^{n-k}p^k$ | $\frac kp$ | $\frac{k(1-p)}{p^2}$ | $\left(\frac{ps}{1 - (1-p)s}\right)^k$ |

## Common Continuous Distributions

| Distribution | p.d.f. | c.d.f. | Mean | Variance |
|---|---|---|---|---|
| $U[a, b]$ | $\frac{1}{b-a}$, $a \leq x \leq b$ | $\frac{x-a}{b-a}$ | $\frac{a+b}{2}$ | $\frac{(b-a)^2}{12}$ |
| $\text{Exp}(\lambda)$ | $\lambda e^{-\lambda x}$, $x \geq 0$ | $1 - e^{-\lambda x}$ | $\frac1\lambda$ | $\frac1{\lambda^2}$ |
| $\text{Gamma}(\alpha, \lambda)$ | $\frac{\lambda^\alpha}{\Gamma(\alpha)}x^{\alpha-1}e^{-\lambda x}$, $x \geq 0$ | | $\frac\alpha\lambda$ | $\frac{\alpha}{\lambda^2}$ |
| $N(\mu, \sigma^2)$ | $\frac{1}{\sqrt{2\pi\sigma^2}}e^{-(x-\mu)^2/2\sigma^2}$ | $\Phi\left(\frac{x-\mu}{\sigma}\right)$ | $\mu$ | $\sigma^2$ |
| $N(0, 1)$ | $\frac{1}{\sqrt{2\pi}}e^{-x^2/2}$ | $\Phi(x)$ | $0$ | $1$ |
| $\text{Beta}(\alpha, \beta)$ | $\frac{\Gamma(\alpha+\beta)}{\Gamma(\alpha)\Gamma(\beta)}x^{\alpha-1}(1-x)^{\beta-1}$, $x \in [0, 1]$ | | $\frac{\alpha}{\alpha+\beta}$ | $\frac{\alpha\beta}{(\alpha+\beta)^2(\alpha+\beta+1)}$ |
