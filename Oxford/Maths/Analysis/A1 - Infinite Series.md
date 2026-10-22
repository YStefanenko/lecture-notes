Analysis I, Chapter 6.1. Back to [[A1]]. Next: [[A1 - Convergence Tests]].

The field axioms give finite sums only. An infinite sum is defined as a limit, and some familiar properties of sums (like reordering) can fail.

> **Definition 6.1 (Partial sums, series)**
> For a real or complex sequence $(a_n)_1^\infty$, the **$n$th partial sum** is $s_n = \sum_{k=1}^n a_k$. The **series** $\sum_{k=1}^\infty a_k$ (or $\sum a_k$) means the sequence of partial sums $(s_n)$.

> [!example]- Example 6.2 (key series)
> (a) **Geometric:** $\sum x^n$, partial sums $(1, 1 + x, 1 + x + x^2, \dots)$, $x \in \mathbb{C}$.
> (b) **Harmonic:** $\sum \frac1n$, partial sums $(1, 1 + \frac12, 1 + \frac12 + \frac13, \dots)$.
> (c) **Exponential:** $\sum \frac{x^n}{n!}$, partial sums $(1, 1 + x, 1 + x + \frac{x^2}{2!}, \dots)$.
> (d) **Cosine:** $a_n = \frac{(-1)^m x^{2m}}{(2m)!}$ if $n = 2m$, else $0$. Partial sums $(1, 1, 1 - \frac{x^2}{2!}, 1 - \frac{x^2}{2!}, 1 - \frac{x^2}{2!} + \frac{x^4}{4!}, \dots)$.

> **Definition 6.3 (Convergence of a series)**
> $\sum a_k$ **converges** (resp. **diverges**) if $(s_n)$ converges (resp. diverges). If $s_n \to L$ write $\sum_{k=1}^\infty a_k = L$, the **sum** of the series.

Convergence only depends on a tail: $\sum_1^\infty a_k$ converges iff $\sum_K^\infty a_k$ does (Remark 6.4). But the *value* depends on where you start.

> **Proposition 6.5**
> If $\sum a_n$ converges then $a_n \to 0$. **The converse is false.**

> [!proof]- Proof
> If $s_n \to L$ then $a_n = s_n - s_{n-1} \to L - L = 0$ (AOL). Counterexample to the converse: $\sum \frac1n$ diverges (Example 3.38) though $\frac1n \to 0$. $\square$

> [!example]- Example 6.6: the geometric series
> For $x \neq 1$: $s_n = 1 + x + \dots + x^n = \frac{1 - x^{n+1}}{1 - x}$.
> - $|x| < 1$: $x^n \to 0$, so $\sum x^n = \frac{1}{1-x}$ (AOL).
> - $|x| \geq 1$: diverges, since $x^n \not\to 0$.

> [!example]- Example 6.7: $\sum \frac{1}{n^2}$ converges
> Partial sums are increasing, and compared with a telescoping sum:
> $$s_n = \sum_{k=1}^n \frac{1}{k^2} \leq 1 + \sum_{k=2}^n \frac{1}{k(k-1)} = 1 + \sum_{k=2}^n \left(\frac{1}{k-1} - \frac1k\right) = 2 - \frac1n \leq 2.$$
> Bounded and increasing, so convergent. (Exact sum $\pi^2/6$: Euler 1734, the **Basel problem**, Remark 6.8.) $\square$

> **Theorem 6.9 (Cauchy's Criterion for Series)**
> $\sum_0^\infty a_k$ converges iff for all $\varepsilon > 0$ there is $N$ such that for all $m, n \geq N$:
> $$|s_n - s_m| = \left|\sum_{k=m+1}^n a_k\right| < \varepsilon.$$

(This is just [[A1 - Cauchy Sequences|Cauchy's criterion]] applied to $(s_n)$.)

> **Definition 6.10 (Absolute / conditional convergence)**
> $\sum a_n$ is **absolutely convergent (AC)** if $\sum |a_n|$ converges. A series that converges but is not AC is **conditionally convergent**.

> **Theorem 6.11** An AC (real or complex) series converges.

> [!proof]- Proof
> Given $\varepsilon$, Cauchy's criterion for $\sum |a_n|$ gives $N$ with $\sum_{k+1}^l |a_n| < \varepsilon$ for $l > k \geq N$. By the triangle inequality $\left|\sum_{k+1}^l a_n\right| \leq \sum_{k+1}^l |a_n| < \varepsilon$, so $\sum a_n$ satisfies Cauchy's criterion. $\square$

> [!example]- Example 6.12
> (a) $\sum_0^\infty x^n$ is AC for $|x| < 1$ and diverges for $|x| \geq 1$ (Example 6.6).
> (b) $\sum \frac{(-1)^n}{n^2}$ is AC (Example 6.7).
> (c) $\sum \frac{\sin n}{n^3}$ is AC: $\sum_1^n \frac{|\sin k|}{k^3} \leq \sum_1^n \frac{1}{k^2} \leq \sum_1^\infty \frac{1}{k^2}$, so the partial sums are increasing and bounded.
> (d) $\sum \frac{(-1)^{n+1}}{n}$ is conditionally convergent (Examples 5.32 and 3.38).

## Rearrangements and Products

> **Definition 6.13 (Rearrangement)**
> If $p : \mathbb{N} \to \mathbb{N}$ is a bijection and $b_n = a_{p(n)}$, then $\sum b_n$ is a **rearrangement** of $\sum a_n$.

> [!example]- Example 6.14 (rearranging changes the sum)
> $$1 - \tfrac12 + \tfrac13 - \tfrac14 + \dots = \log 2, \qquad 1 + \tfrac13 - \tfrac12 + \tfrac15 + \tfrac17 - \tfrac14 + \dots = \tfrac32 \log 2.$$
> (Sheet 6, Ex 6.)

> **Theorem 6.15 (Dirichlet, 1837)** *(off-syllabus)*
> If $\sum a_n$ is AC then every rearrangement $\sum a_{p(n)}$ is AC with the same sum. So a series is AC iff it is **unconditionally convergent**.

> **Theorem 6.16 (Riemann Rearrangement Theorem, 1853)** *(off-syllabus)*
> If $\sum a_n$ is a real conditionally convergent series and $-\infty \leq L \leq \infty$, there is a rearrangement with $\sum a_{p(n)} = L$.

> **Theorem 6.17 (Cauchy product, 1821)** *(off-syllabus)*
> If $\sum_0^\infty a_n$ and $\sum_0^\infty b_n$ are AC and $c_n = \sum_{k=0}^n a_k b_{n-k}$, then $\sum c_n$ is AC and
> $$\sum_0^\infty c_n = \left(\sum_0^\infty a_n\right)\left(\sum_0^\infty b_n\right).$$
> *(Proof: Sheet 6, Ex 7.)*

Mertens (1875): it's enough for one series to be AC and the other convergent (Remark 6.18).

> [!example]- Example 6.19: $\left(\sum \frac{x^n}{n!}\right)\left(\sum \frac{y^n}{n!}\right) = \sum \frac{(x+y)^n}{n!}$
> Both series are AC (Example 6.26). The Cauchy product term is
> $$c_n = \sum_{r+s=n} \frac{x^r}{r!}\frac{y^s}{s!} = \frac{1}{n!}\sum_{r=0}^n \binom nr x^r y^{n-r} = \frac{(x+y)^n}{n!}$$
> by the binomial theorem. (This is $\exp(x)\exp(y) = \exp(x+y)$.) $\square$
