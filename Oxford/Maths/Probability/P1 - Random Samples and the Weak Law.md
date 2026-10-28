Prelims Probability, Chapter 6. Back to [[P1 - Basics]].

> **Definition 6.1 (Random sample)**
> i.i.d. random variables $X_1, \dots, X_n$ form a **random sample** of size $n$ from their common ("parent") distribution.

> **Definition 6.2 (Sample mean)**
> $$\bar X_n = \frac1n\sum_{i=1}^n X_i.$$

By induction from the two-variable rule:
$$\operatorname{var}\Big(\sum_{i=1}^n X_i\Big) = \sum_{i=1}^n \operatorname{var}(X_i) + 2\sum_{i<j}\operatorname{cov}(X_i, X_j).$$

> **Theorem 6.3**
> For a random sample with mean $\mu$ and variance $\sigma^2$:
> $$\mathbb{E}[\bar X_n] = \mu, \qquad \operatorname{var}(\bar X_n) = \frac{\sigma^2}{n}.$$

> [!proof]- Proof
> Linearity: $\mathbb{E}[\bar X_n] = \frac1n\sum \mathbb{E}[X_i] = \mu$. Independence makes all covariances 0, so
> $$\operatorname{var}(\bar X_n) = \frac{1}{n^2}\sum \operatorname{var}(X_i) = \frac{\sigma^2}{n}. \quad \square$$

> [!example]- Example 6.4 (Bernoulli sample)
> $X_i \sim \text{Ber}(p)$: $\mathbb{E}[\bar X_n] = p$ and $\operatorname{var}(\bar X_n) = \frac{p(1-p)}{n}$. If $X_i = \mathbb{1}_A$ on the $i$th repeat of an experiment, $\bar X_n$ is the proportion of times $A$ happened. The weak law says this approaches $p = \mathbb{P}(A)$, which justifies the frequency interpretation of probability.

> **Theorem 6.5 (Weak Law of Large Numbers)**
> If $X_1, X_2, \dots$ are i.i.d. with mean $\mu$, then for any fixed $\epsilon > 0$,
> $$\mathbb{P}\left(\left|\frac1n\sum_{i=1}^n X_i - \mu\right| > \epsilon\right) \to 0 \quad \text{as } n \to \infty.$$
> Equivalently, $\mathbb{P}(|\bar X_n - \mu| \leq \epsilon) \to 1$. It only depends on the distribution through its mean.

The proof below assumes a finite variance and uses two inequalities.

> **Theorem 6.6 (Markov's inequality)**
> If $Y \geq 0$ and $\mathbb{E}[Y]$ exists, then for all $t > 0$:
> $$\mathbb{P}(Y \geq t) \leq \frac{\mathbb{E}[Y]}{t}.$$

> [!proof]- Proof
> Let $A = \{Y \geq t\}$; WLOG $\mathbb{P}(A) \in (0, 1)$ (otherwise trivial). By the partition theorem for expectations,
> $$\mathbb{E}[Y] = \mathbb{E}[Y|A]\mathbb{P}(A) + \mathbb{E}[Y|A^c]\mathbb{P}(A^c) \geq \mathbb{E}[Y|A]\mathbb{P}(A) \geq t\,\mathbb{P}(A),$$
> since $\mathbb{E}[Y|A^c] \geq 0$ and $\mathbb{E}[Y | Y \geq t] \geq t$. $\square$

> **Theorem 6.7 (Chebyshev's inequality)**
> If $Z$ has finite variance, then for all $t > 0$:
> $$\mathbb{P}(|Z - \mathbb{E}[Z]| \geq t) \leq \frac{\operatorname{var}(Z)}{t^2}.$$

> [!proof]- Proof
> $\mathbb{P}(|Z - \mathbb{E}Z| \geq t) = \mathbb{P}((Z - \mathbb{E}Z)^2 \geq t^2)$; apply Markov to $Y = (Z - \mathbb{E}Z)^2$. $\square$

> [!proof]- Proof of the Weak Law (assuming finite variance $\sigma^2$)
> With $Z = \bar X_n$: $\mathbb{E}[Z] = \mu$ and $\operatorname{var}(Z) = \sigma^2/n$ (Theorem 6.3). By Chebyshev,
> $$\mathbb{P}(|\bar X_n - \mu| > \epsilon) \leq \frac{\sigma^2}{n\epsilon^2} \to 0 \quad \text{as } n \to \infty. \quad \square$$
