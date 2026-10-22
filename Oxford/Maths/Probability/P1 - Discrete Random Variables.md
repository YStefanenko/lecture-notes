Prelims Probability, Chapter 2.0–2.3. Back to [[P1]]. Next: [[P1 - Joint Discrete Distributions]].

> **Definition 2.1 (Discrete random variable)**
> A **discrete random variable** on $(\Omega, \mathcal{F}, \mathbb{P})$ is a function $X : \Omega \to \mathbb{R}$ such that
> 1. $\{\omega \in \Omega : X(\omega) = x\} \in \mathcal{F}$ for each $x \in \mathbb{R}$;
> 2. $\operatorname{Im}X = X(\Omega)$ is a finite or countable subset of $\mathbb{R}$.

(1) says $\{X = x\}$ is an event, so $\mathbb{P}(X = x)$ makes sense. (2) says $X$ takes countably many values. If $\Omega$ is countable and $\mathcal{F}$ is its power set, both hold automatically. Abbreviation: r.v.

> [!example]- Example 2.2
> Two dice, $\Omega = \{(i, j) : 1 \leq i, j \leq 6\}$: $X(i, j) = \max\{i, j\}$ and $Y(i, j) = i + j$ are random variables.

> **Definition 2.3 (Probability mass function)**
> The **p.m.f.** of $X$ is $p_X : \mathbb{R} \to [0, 1]$, $p_X(x) = \mathbb{P}(X = x)$.

$p_X(x) = 0$ for $x \notin \operatorname{Im}X$, and $\sum_{x \in \operatorname{Im}X}p_X(x) = \mathbb{P}(\Omega) = 1$ (the events $\{X = x\}$ are disjoint and cover $\Omega$).

> [!example]- Example 2.4 (indicator function)
> For $A \in \mathcal{F}$, $X(\omega) = 1$ if $\omega \in A$, else $0$. Then $p_X(1) = \mathbb{P}(A)$, $p_X(0) = 1 - \mathbb{P}(A)$. Written $X = \mathbb{1}_A$, the **indicator function** of $A$.

## Classical Discrete Distributions (2.1)

| Distribution | p.m.f. | Models |
|---|---|---|
| **Bernoulli** $\text{Ber}(p)$ | $\mathbb{P}(X = 1) = p$, $\mathbb{P}(X = 0) = 1 - p = q$ | one trial (e.g. $\mathbb{1}_A$ with $p = \mathbb{P}(A)$) |
| **Binomial** $\text{Bin}(n, p)$ | $\binom nk p^k(1-p)^{n-k}$, $k = 0, \dots, n$ | successes in $n$ independent trials |
| **Geometric** $\text{Geom}(p)$ | $p(1-p)^{k-1}$, $k = 1, 2, \dots$ | trials needed for the first success |
| **Poisson** $\text{Po}(\lambda)$ | $\frac{\lambda^k e^{-\lambda}}{k!}$, $k = 0, 1, \dots$ | many rare events (limit of $\text{Bin}(n, \lambda/n)$) |

- **Binomial:** any particular sequence with $k$ successes has probability $p^k(1-p)^{n-k}$, and there are $\binom nk$ of them.
- **Geometric warning:** an alternative convention counts the *failures* before the first success: $Y = X - 1$, $\mathbb{P}(Y = k) = p(1-p)^k$, $k = 0, 1, \dots$. State which one you use.
- **Exercise 2.5:** check each is a valid p.m.f. ($p_X \geq 0$ and $\sum p_X = 1$).

Any function $p \geq 0$ with $\sum p = 1$ is the p.m.f. of some r.v. (e.g. take $\Omega = \{x : p(x) \neq 0\}$ and $X$ the identity). Different probability spaces can give the same distribution: $\text{Bin}(3, \frac12)$ can also be built from $\Omega = \{0,1\}^3$ with $X(i,j,k) = i + j + k$. In practice we rarely mention $\Omega$; we work with events, random variables and their distributions.

## Expectation (2.2)

> **Definition 2.6 (Expectation)**
> The **expectation** (expected value, mean) of $X$ is
> $$\mathbb{E}[X] = \sum_{x \in \operatorname{Im}X} x\,\mathbb{P}(X = x), \tag{2.1}$$
> provided $\sum_{x}|x|\,\mathbb{P}(X = x) < \infty$. Otherwise the expectation does not exist.

Absolute convergence is needed so the order of summation doesn't matter (see [[A1 - Infinite Series]]). If $X \geq 0$ and the sum diverges, write $\mathbb{E}[X] = \infty$.

> [!example]- Example 2.7
> 1. Fair die: $\mathbb{E}[X] = \frac16(1 + 2 + \dots + 6) = 3.5$.
> 2. Indicator: $\mathbb{E}[\mathbb{1}_A] = 0\cdot\mathbb{P}(A^c) + 1\cdot\mathbb{P}(A) = \mathbb{P}(A)$.
> 3. $\mathbb{P}(X = n) = \frac{6}{\pi^2}\frac{1}{n^2}$: $\sum n\,\mathbb{P}(X = n) = \frac{6}{\pi^2}\sum\frac1n = \infty$, so the expectation doesn't exist ($\mathbb{E}[X] = \infty$).
> 4. $X \sim \text{Po}(\lambda)$:
> $$\mathbb{E}[X] = \sum_{k=0}^\infty k\frac{e^{-\lambda}\lambda^k}{k!} = \lambda e^{-\lambda}\sum_{k=1}^\infty \frac{\lambda^{k-1}}{(k-1)!} = \lambda e^{-\lambda}e^\lambda = \lambda.$$

> **Theorem 2.8 (Expectation of a function)**
> For $h : \mathbb{R} \to \mathbb{R}$,
> $$\mathbb{E}[h(X)] = \sum_{x \in \operatorname{Im}X} h(x)\,\mathbb{P}(X = x),$$
> provided $\sum_x |h(x)|\,\mathbb{P}(X = x) < \infty$.

> [!proof]- Proof
> Let $A = h(\operatorname{Im}X)$. Group the terms by the value $y = h(x)$:
> $$\sum_x h(x)\mathbb{P}(X = x) = \sum_{y \in A}\ \sum_{x : h(x) = y} y\,\mathbb{P}(X = x) = \sum_{y \in A} y\,\mathbb{P}(h(X) = y) = \mathbb{E}[h(X)]. \quad \square$$

**Example 2.9** $\mathbb{E}[X^k]$ is the **$k$th moment** of $X$ (when it exists).

> **Theorem 2.10**
> If $\mathbb{E}[X]$ exists:
> 1. if $X \geq 0$ then $\mathbb{E}[X] \geq 0$;
> 2. $\mathbb{E}[aX + b] = a\,\mathbb{E}[X] + b$ for $a, b \in \mathbb{R}$.

> [!proof]- Proof
> (1) $\operatorname{Im}X \subseteq [0, \infty)$, so (2.1) is a sum of non-negative terms. (2) Exercise. $\square$

> **Definition 2.11 (Variance)**
> $$\operatorname{var}(X) = \mathbb{E}\big[(X - \mathbb{E}[X])^2\big],$$
> provided it exists.

$\operatorname{var}(X) \geq 0$ (Theorem 2.10(1)), and it's $0$ for a deterministic $X$: only randomness creates variance. Expanding with $\mu = \mathbb{E}[X]$:
$$\operatorname{var}(X) = \mathbb{E}[X^2] - 2\mu\,\mathbb{E}[X] + \mu^2 = \mathbb{E}[X^2] - (\mathbb{E}[X])^2.$$
The **standard deviation** is $\sqrt{\operatorname{var}(X)}$.

> **Theorem 2.12** If $\operatorname{var}(X)$ exists, then $\operatorname{var}(aX + b) = a^2\operatorname{var}(X)$. *(Exercise.)*

$b$ just shifts the distribution and its mean. (Statisticians like the standard deviation because it scales by $|a|$, in the same units as $X$.)

## Conditional Distributions (2.3)

> **Definition 2.13 (Conditional p.m.f. and expectation)**
> If $\mathbb{P}(B) > 0$:
> $$p_{X|B}(x) = \mathbb{P}(X = x | B) = \frac{\mathbb{P}(\{X = x\} \cap B)}{\mathbb{P}(B)}, \qquad \mathbb{E}[X|B] = \sum_x x\,\mathbb{P}(X = x|B),$$
> the latter whenever the sum converges absolutely.

> **Theorem 2.14 (Partition theorem for expectations)**
> If $\{B_i\}$ is a partition of $\Omega$ with $\mathbb{P}(B_i) > 0$, then
> $$\mathbb{E}[X] = \sum_{i \geq 1}\mathbb{E}[X|B_i]\,\mathbb{P}(B_i),$$
> whenever $\mathbb{E}[X]$ exists.

> [!proof]- Proof
> $$\mathbb{E}[X] = \sum_x x\sum_i \mathbb{P}(X = x|B_i)\mathbb{P}(B_i) = \sum_i \mathbb{P}(B_i)\sum_x x\,\mathbb{P}(X = x|B_i) = \sum_i \mathbb{E}[X|B_i]\mathbb{P}(B_i),$$
> by the law of total probability and swapping the (absolutely convergent) sums. $\square$

> [!example]- Example 2.15: mean and variance of $\text{Geom}(\frac16)$ by conditioning
> $X$ = rolls of a fair die until the first 6. Condition on whether the first roll is a 6 ($B_1$). If not, it's as if we start again after 1 wasted roll:
> $$\mathbb{E}[X] = \tfrac16\cdot 1 + \tfrac56\,\mathbb{E}[1 + X] \implies \mathbb{E}[X] = 6.$$
> $$\mathbb{E}[X^2] = \tfrac16 + \tfrac56\,\mathbb{E}[(1 + X)^2] = \tfrac16 + \tfrac56(1 + 2\mathbb{E}[X] + \mathbb{E}[X^2]) \implies \mathbb{E}[X^2] = 66.$$
> So $\operatorname{var}(X) = 66 - 36 = 30$. Much easier than summing $\sum k p q^{k-1}$ and $\sum k^2 pq^{k-1}$ directly.
