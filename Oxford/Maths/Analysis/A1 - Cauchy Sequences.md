Analysis I, Chapter 5.3. Back to [[A1]]. Uses [[A1 - Monotone Sequences and Subsequences]] (Bolzano–Weierstrass).

Cauchy's idea: a sequence converges iff its terms eventually get close **to each other**, so you can prove convergence without knowing the limit.

> **Definition 5.25 (Cauchy sequence)**
> A real or complex sequence $(a_n)$ is **Cauchy** if
> $$\forall \varepsilon > 0 \ \ \exists N \in \mathbb{N} \ \ \forall m, n \geq N \quad |a_m - a_n| < \varepsilon.$$

No limit is mentioned. Cauchy ⟺ convergent in $\mathbb{R}$ and $\mathbb{C}$, but **not** in $\mathbb{Q}$.

> **Proposition 5.26** A convergent sequence is Cauchy.

> [!proof]- Proof
> If $a_n \to L$, take $N$ with $|a_k - L| < \varepsilon/2$ for $k \geq N$. For $m, n \geq N$: $|a_m - a_n| \leq |a_m - L| + |L - a_n| < \varepsilon$. $\square$

> **Proposition 5.27** A (real or complex) Cauchy sequence is bounded.

> [!proof]- Proof
> With $\varepsilon = 1$, there's $N$ with $|a_n - a_N| < 1$ for $n \geq N$, so $|a_n| < |a_N| + 1$ there. Hence $|a_m| \leq \max\{|a_1|, \dots, |a_{N-1}|, |a_N| + 1\}$ for all $m$. $\square$

> **Lemma 5.28**
> If $(a_n)$ is Cauchy and a subsequence $a_{n_k} \to L$, then $a_n \to L$.

> [!proof]- Proof
> Take $K$ with $|a_{n_k} - L| < \varepsilon/2$ for $k \geq K$, and $N$ with $|a_n - a_m| < \varepsilon/2$ for $m, n \geq N$. Pick $k \geq \max(K, N)$, so $n_k \geq N$. Then for $n \geq N$:
> $$|a_n - L| \leq |a_n - a_{n_k}| + |a_{n_k} - L| < \varepsilon. \quad \square$$

> **Theorem 5.29 (Cauchy, 1821)**
> A real or complex Cauchy sequence converges.

> [!proof]- Proof
> It is bounded (5.27), so by Bolzano–Weierstrass it has a convergent subsequence, and by Lemma 5.28 the whole sequence converges to the same limit. $\square$

> **Cauchy Convergence Criterion** (real or complex sequences)
> $$(a_n) \text{ is convergent} \iff (a_n) \text{ is Cauchy}.$$

Together with the Archimedean property, this is equivalent to the completeness axiom (Remark 5.30).

> [!example]- Example 5.31 (Cauchy but not convergent in $\mathbb{Q}$)
> The truncated decimals of $\sqrt2$, $1, 1.4, 1.41, 1.414, \dots$, are rational and Cauchy (they converge in $\mathbb{R}$), but have no limit in $\mathbb{Q}$.

> [!example]- Example 5.32 (Mercator's series is Cauchy)
> $s_n = 1 - \frac12 + \frac13 - \dots + (-1)^{n+1}\frac1n$. For $m \geq n > 0$, group the terms of $s_m - s_n$ in pairs:
> $$|s_m - s_n| = \left|\tfrac{1}{n+1} - \tfrac{1}{n+2} + \tfrac{1}{n+3} - \dots \pm \tfrac1m\right| \leq \frac{1}{n+1}$$
> (pairs $\frac1{n+1} - \frac1{n+2}$, … are positive, so the absolute value is the sum itself; regrouping as $\frac1{n+1} + (-\frac1{n+2} + \frac1{n+3}) + \dots$ shows it's at most $\frac{1}{n+1}$; similarly when $m - n$ is odd). So for $N > 1/\varepsilon$, $|s_m - s_n| < \varepsilon$ when $m, n \geq N$: $(s_n)$ is Cauchy, hence convergent, before we know the limit. (It is $\log 2$; Sheet 6, Ex 6. Mercator, 1668.)

> [!note]- Remark 5.33 (Double sequences)
> A double sequence is $x : \mathbb{N}^2 \to \mathbb{R}$, $x_{m,n}$. $\lim_{m,n \to \infty} x_{m,n} = L$ means $\forall \varepsilon > 0\ \exists N\ \forall m, n \geq N\ |x_{m,n} - L| < \varepsilon$. So "Cauchy" means $|a_n - a_m| \to 0$ as $m, n \to \infty$. Beware: $\lim_{m,n}$, $\lim_m \lim_n$ and $\lim_n \lim_m$ are different and may exist independently (Sheet 5, Ex 8).

> [!note]- Remark 5.34 (Construction of the number systems, off-syllabus)
> - **$\mathbb{N}$:** Peano (1889): the smallest set with $0 \in \mathbb{N}$ and $n \in \mathbb{N} \Rightarrow n + 1 \in \mathbb{N}$. Von Neumann (1923): $0 = \varnothing$, $1 = \{\varnothing\}$, $2 = \{\varnothing, \{\varnothing\}\}$, $n = \{0, 1, \dots, n-1\}$.
> - **$\mathbb{Z}$:** $\mathbb{N}^2/\sim$ with $(m_1, m_2) \sim (n_1, n_2) \iff m_1 + n_2 = n_1 + m_2$ (pairs differing by the same integer). See [[IUM - Constructing Z from N]].
> - **$\mathbb{Q}$:** $\mathbb{Z} \times (\mathbb{N} \setminus \{0\}) / \sim$ with $(m_1, n_1) \sim (m_2, n_2) \iff m_1 n_2 = n_1 m_2$.
> - **$\mathbb{R}$:** let $S$ be the set of rational Cauchy sequences and $(a_n) \sim (b_n) \iff a_n - b_n \to 0$. Sums, products, scalar multiples (and reciprocals of sequences not tending to 0) stay in $S$ and are well-defined on classes (by AOL). Order: $(a_n) \leq (b_n)$ if $b_n - a_n \geq 0$ on some tail. Then $\mathbb{R} = S/\sim$ is an ordered field, and bounded non-empty subsets have suprema (Körner pp. 352–353).
> - **$\mathbb{C}$:** ordered pairs of reals ([[A1 - Complex Numbers]]).
