Prelims Probability, Chapter 4. Back to [[P1 - Basics]].

Throughout, $X$ takes values in $\{0, 1, 2, \dots\}$ and $p_k = \mathbb{P}(X = k)$.

> **Definition 4.1 (Probability generating function)**
> Let $S = \{s \in \mathbb{R} : \sum_k |s|^k p_k < \infty\}$. The **p.g.f.** of $X$ is $G_X : S \to \mathbb{R}$,
> $$G_X(s) = \mathbb{E}[s^X] = \sum_{k=0}^\infty s^k p_k.$$

Since $\sum p_k = 1$, $G_X$ is defined at least on $[-1, 1]$, and $G_X(1) = 1$. The variable $s$ is just a dummy argument. It's a power series with radius of convergence $\geq 1$ that can be differentiated term by term inside it (see [[A1 - Power Series]]).

> **Theorem 4.2 (Uniqueness theorem)**
> The distribution of $X$ is uniquely determined by its p.g.f. $G_X$.

> [!proof]- Proof
> $G_X(0) = p_0$. Differentiating term by term for $|s| < 1$: $G_X'(s) = p_1 + 2p_2 s + 3p_3 s^2 + \dots$, so $G_X'(0) = p_1$. In general
> $$\frac{d^k}{ds^k}G_X(s)\Big|_{s=0} = k!\,p_k,$$
> so all the $p_k$ can be recovered from $G_X$. $\square$

> **P.g.f.s of common distributions**
> | Distribution | $G_X(s)$ | valid for |
> |---|---|---|
> | $\text{Ber}(p)$ | $q + ps$ | all $s$ |
> | $\text{Bin}(n, p)$ | $(1 - p + ps)^n$ | all $s$ |
> | $\text{Po}(\lambda)$ | $e^{\lambda(s-1)}$ | all $s$ |
> | $\text{Geom}(p)$ | $\dfrac{ps}{1 - (1-p)s}$ | $\lvert s \rvert < \frac{1}{1-p}$ |

> [!proof]- Derivations
> **Binomial:** $\sum_k s^k\binom nk p^k(1-p)^{n-k} = \sum_k \binom nk (ps)^k(1-p)^{n-k} = (1 - p + ps)^n$ (binomial theorem).
> **Poisson:** $\sum_k s^k\frac{\lambda^k e^{-\lambda}}{k!} = e^{-\lambda}\sum_k\frac{(s\lambda)^k}{k!} = e^{\lambda(s-1)}$.
> **Geometric:** problem sheet. $\square$

> **Theorem 4.3** If $X$ and $Y$ are independent, then $G_{X+Y}(s) = G_X(s)\,G_Y(s)$.

> [!proof]- Proof
> $G_{X+Y}(s) = \mathbb{E}[s^X s^Y] = \mathbb{E}[s^X]\,\mathbb{E}[s^Y]$, since $s^X, s^Y$ are independent (problem sheet) and Theorem 2.23 applies. $\square$

> **Theorem 4.4** If $X_1, \dots, X_n$ are independent $\text{Ber}(p)$, then $Y = X_1 + \dots + X_n \sim \text{Bin}(n, p)$.

> [!proof]- Proof
> $G_Y(s) = \mathbb{E}[s^{X_1}]\cdots\mathbb{E}[s^{X_n}] = (1 - p + ps)^n$, the $\text{Bin}(n, p)$ p.g.f.; apply uniqueness. (Interpretation: $Y$ counts heads in $n$ independent flips.) $\square$

> **Theorem 4.5** If $X_i \sim \text{Po}(\lambda_i)$ are independent, then $\sum_{i=1}^n X_i \sim \text{Po}\left(\sum_{i=1}^n \lambda_i\right)$. In particular, the sum of $n$ i.i.d. $\text{Po}(\lambda)$ is $\text{Po}(n\lambda)$.

> [!proof]- Proof
> $\mathbb{E}[s^{X_1 + \dots + X_n}] = \prod e^{\lambda_i(s-1)} = \exp\left((s-1)\sum\lambda_i\right)$; uniqueness. $\square$

## Moments from P.g.f.s (4.1)

$G_X'(s) = \sum k s^{k-1}p_k = \mathbb{E}[X s^{X-1}]$, so:

> **Moments from the p.g.f.**
> $$G_X'(1) = \mathbb{E}[X], \qquad G_X''(1) = \mathbb{E}[X(X-1)], \qquad \operatorname{var}(X) = G_X''(1) + G_X'(1) - (G_X'(1))^2,$$
> $$\frac{d^k}{ds^k}G_X(s)\Big|_{s=1} = \mathbb{E}[X(X-1)\cdots(X-k+1)].$$

> [!example]- Example 4.6 ($G(s) = \frac16 + \frac s3 + \frac{s^2}{2}$)
> $X_1, X_2, X_3$ i.i.d. with this p.g.f., $Y = X_1 + X_2 + X_3$.
> 1. $G' = \frac13 + s$, $G'' = 1$: $\mathbb{E}[X_1] = \frac43$, $\operatorname{var}(X_1) = 1 + \frac43 - \frac{16}{9} = \frac59$.
> 2. $G_Y(s) = G(s)^3 = \frac{1}{216}(1 + 6s + 21s^2 + 44s^3 + 63s^4 + 54s^5 + 27s^6)$, so $\mathbb{P}(Y = 3) = \frac{44}{216} = \frac{11}{54}$.
> 3. $G_{3X_1}(s) = \mathbb{E}[(s^3)^{X_1}] = G(s^3) = \frac16 + \frac{s^3}{3} + \frac{s^6}{2}$. This differs from $G_Y$: $3X_1$ and $Y$ have different distributions (knowing $X_1$ determines $3X_1$, but not $Y$). $\mathbb{P}(3X_1 = 3) = \frac13$.

> [!example]- Example 4.7 (red balls before blue, via conditioning)
> Urn: $n$ red, $n$ white, 1 blue, drawn with replacement. $X$ = number of reds before the first blue. Condition on the first ball:
> $$G_X(s) = \mathbb{E}[s^{1+X}]\tfrac{n}{2n+1} + \mathbb{E}[s^X]\tfrac{n}{2n+1} + \mathbb{E}[s^0]\tfrac{1}{2n+1} \implies G_X(s) = \frac{1}{n + 1 - ns}.$$
> So $X$ is geometric (failures convention) with parameter $\frac{1}{n+1}$. Then $G_X'(s) = \frac{n}{(n+1-ns)^2}$, so $\mathbb{E}[X] = n$; $G_X''(s) = \frac{2n^2}{(n+1-ns)^3}$, so $G_X''(1) = 2n^2$ and $\operatorname{var}(X) = 2n^2 + n - n^2 = n(n+1)$.
> (For $\mathbb{E}[X]$ alone, conditioning directly is quicker; for the variance the p.g.f. is easier.)

## Random Sums

> **Theorem 4.8 (Random sums)**
> Let $X_1, X_2, \dots$ be i.i.d. with p.g.f. $G_X$, and $N$ independent of them with p.g.f. $G_N$. Then $\sum_{i=1}^N X_i$ (which is $0$ if $N = 0$) has p.g.f.
> $$G_N(G_X(s)).$$

> [!proof]- Proof
> Partition on the value of $N$:
> $$\mathbb{E}\left[s^{X_1 + \dots + X_N}\right] = \sum_n \mathbb{E}\left[s^{X_1 + \dots + X_n}\right]\mathbb{P}(N = n) = \sum_n (G_X(s))^n\,\mathbb{P}(N = n) = G_N(G_X(s)),$$
> using independence of $N$ from the $X_i$, then independence of the $X_i$. $\square$

> **Corollary 4.9 (Poisson thinning)**
> If $X_i$ are i.i.d. $\text{Ber}(p)$ and $N \sim \text{Po}(\lambda)$ independently, then $\sum_{i=1}^N X_i \sim \text{Po}(\lambda p)$.

> [!proof]- Proof
> $G_N(G_X(s)) = \exp(\lambda(1 - p + ps - 1)) = \exp(\lambda p(s - 1))$; uniqueness. $\square$

> [!example]- Example 4.10 (photomultiplier)
> Photons detected $N$: $0, 1, 2$ with probabilities $\frac12, \frac13, \frac16$, so $G_N(s) = \frac12 + \frac s3 + \frac{s^2}{6}$. Each photon releases 2, 3, 4 or 5 electrons equally likely: $G_X(s) = \frac14(s^2 + s^3 + s^4 + s^5)$. Total electrons $Y$:
> $$G_Y(s) = \tfrac12 + \tfrac13 G_X(s) + \tfrac16 G_X(s)^2 = \tfrac12 + \tfrac1{12}(s^2 + s^3 + s^4 + s^5) + \tfrac{1}{96}(s^4 + 2s^5 + 3s^6 + 4s^7 + 3s^8 + 2s^9 + s^{10}).$$
> $\mathbb{P}(Y = 5) = \frac1{12} + \frac{2}{96} = \frac{5}{48}$.

## Branching Processes (4.2)

Each individual lives one unit of time and has a random number of children with **offspring distribution** $p(i)$, $i \geq 0$, independently of everyone else. Let $X_n$ be the generation-$n$ size, $X_0 = 1$, and $C_i^{(n)}$ the number of children of the $i$th individual in generation $n$:
$$X_{n+1} = C_1^{(n)} + \dots + C_{X_n}^{(n)}.$$
Let $G(s) = \sum p(i)s^i$ and $G_n(s) = \mathbb{E}[s^{X_n}]$.

> **Theorem 4.11**
> $$G_{n+1}(s) = G_n(G(s)) = \underbrace{G(G(\dots G(s)\dots))}_{n+1 \text{ times}} = G(G_n(s)).$$

> [!proof]- Proof
> $G_0(s) = s$ and $G_1 = G$. Since $X_{n+1}$ is a random sum of $X_n$ i.i.d. copies of the offspring variable, Theorem 4.8 gives $G_{n+1}(s) = G_n(G(s))$. Induct. $\square$

> **Corollary 4.12** If the mean number of children is $\mu = \sum i\,p(i)$, then $\mathbb{E}[X_n] = \mu^n$.

> [!proof]- Proof
> $G_n'(s) = G_{n-1}'(s)\,G'(G_{n-1}(s))$ (chain rule). At $s = 1$, $G_{n-1}(1) = 1$, so $\mathbb{E}[X_n] = \mathbb{E}[X_{n-1}]\,\mu$; induct. $\square$

So there's exponential growth on average if $\mu > 1$ and decay if $\mu < 1$. If $p(0) > 0$, the population dies out with probability $\geq \mathbb{P}(X_1 = 0) = p(0) > 0$, even if $\mathbb{E}[X_n] \to \infty$.

> [!example]- Example 4.13 (geometric offspring)
> $p(i) = (\frac12)^{i+1}$, so $G(s) = \frac{1}{2 - s}$, $G_2(s) = \frac{2-s}{3-2s}$, $G_3(s) = \frac{3-2s}{4-3s}$, and by induction
> $$G_n(s) = \frac{n - (n-1)s}{(n+1) - ns}.$$
> Expanding $\frac{1}{(n+1) - ns} = \sum_k \frac{n^k s^k}{(n+1)^{k+1}}$ and multiplying out:
> $$\mathbb{P}(X_n = 0) = \frac{n}{n+1}, \qquad \mathbb{P}(X_n = k) = \frac{n^{k-1}}{(n+1)^{k+1}} \ (k \geq 1).$$
> $\mathbb{P}(X_n = 0) \to 1$: the population eventually dies out.

## Extinction Probability (4.2.1, non-examinable)

Let $q = \mathbb{P}(\text{population dies out})$. Conditioning on $X_1 = k$: the $k$ children start independent copies of the process, and all must die out, so
$$q = \sum_k q^k p(k) = G(q). \tag{4.1}$$
$1$ always solves this, so (4.1) alone doesn't determine $q$. By continuity along the increasing events $\{X_n = 0\}$ (Prop A.8):
$$q = \lim_{n \to \infty}\mathbb{P}(X_n = 0) = \lim_{n \to \infty}G_n(0). \tag{4.2}$$

> **Theorem 4.14**
> The extinction probability $q$ is the smallest non-negative solution of $x = G(x)$.

> [!proof]- Proof
> $q$ solves it by (4.1). Let $r \geq 0$ be any solution. Claim $G_n(0) \leq r$ for all $n$: $G_0(0) = 0 \leq r$, and since $G$ is non-decreasing on $[0, \infty)$, $G_n(0) = G(G_{n-1}(0)) \leq G(r) = r$. So $q = \lim G_n(0) \leq r$. $\square$

> **Theorem 4.15**
> Assume $p(1) \neq 1$. Then $q = 1$ if $\mu \leq 1$, and $q < 1$ if $\mu > 1$.

> [!proof]- Proof
> **Quick case $\mu < 1$:** $\mathbb{P}(X_n > 0) = \sum_{k \geq 1}\mathbb{P}(X_n = k) \leq \sum_k k\,\mathbb{P}(X_n = k) = \mathbb{E}[X_n] = \mu^n \to 0$, so $q = 1$ by (4.2).
> 
> **General:** $G'(s) = \sum k p(k)s^{k-1}$ is non-decreasing on $s \geq 0$, so $G$ is convex. Its graph passes through $(0, p_0)$ and $(1, 1)$ with slope $\mu$ at $1$.
> - $\mu > 1$: the slope at $1$ exceeds that of $y = x$ and $G(0) \geq 0$, so the curve crosses $y = x$ at some point in $[0, 1)$; the smallest fixed point is $< 1$.
> - $\mu \leq 1$ (and $p(1) \neq 1$): the slope is $< 1$ on $[0, 1)$, so $G(x) > x$ there and the only fixed point in $[0, 1]$ is $1$. $\square$
