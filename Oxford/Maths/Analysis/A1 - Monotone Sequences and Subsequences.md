Analysis I, Chapter 5.1–5.2. Back to [[A1]]. Next: [[A1 - Cauchy Sequences]].

## Monotone Sequences

> **Definition 5.1 (Monotone sequences)**
> A real sequence $(a_n)$ is
> - **increasing** if $a_n \leq a_m$ whenever $n < m$;
> - **decreasing** if $a_n \geq a_m$ whenever $n < m$;
> - **strictly increasing** if $a_n < a_m$ whenever $n < m$;
> - **strictly decreasing** if $a_n > a_m$ whenever $n < m$;
> - **monotone** if it is increasing or decreasing.

Example 5.2: $a_n = n$ and $a_n = (2n+1)^2$ are increasing; $(-1)^n$ is not monotone.

> **Theorem 5.3 (Monotone Convergence)**
> An increasing sequence that is bounded above converges.

> [!proof]- Proof
> Let $L = \sup\{a_n : n \in \mathbb{N}\}$ (exists by completeness). Given $\varepsilon > 0$, the approximation property gives $N$ with $L - \varepsilon < a_N \leq L$. As $(a_n)$ is increasing, for $n \geq N$:
> $$L - \varepsilon < a_N \leq a_n \leq L,$$
> so $|a_n - L| < \varepsilon$. $\square$

> **Corollary 5.4** An increasing real sequence either converges or tends to $\infty$.

> [!proof]- Proof
> If bounded above, it converges. Otherwise, for any $M$ there's $N$ with $a_N \geq M$, and then $a_n \geq M$ for all $n \geq N$. $\square$

> **Corollary 5.5** A decreasing sequence that is bounded below converges.

> [!proof]- Proof
> $(-a_n)$ is increasing and bounded above, so $-a_n \to L$, and $a_n \to -L$ by AOL. $\square$

Theorem 5.3 is equivalent to the completeness axiom (Remark 5.6), and so is the next theorem together with the Archimedean property.

> **Theorem 5.7 (Nested Intervals Theorem, Cantor 1872)**
> Let $I_n = [a_n, b_n]$ be nested closed bounded intervals ($I_{n+1} \subseteq I_n$).
> 1. $\bigcap_{n=1}^\infty I_n \neq \varnothing$.
> 2. If $b_n - a_n \to 0$ then $\bigcap_{n=1}^\infty I_n$ is a single point.
> 3. It can fail if the intervals aren't closed ($I_n = (0, 1/n)$) or aren't bounded ($I_n = [n, \infty)$).

> [!proof]- Proof
> (1) $a_n \leq a_{n+1} \leq b_{n+1} \leq b_n$, so $(a_n)$ is increasing and bounded above and $(b_n)$ is decreasing and bounded below. Let $\alpha = \lim a_n$, $\beta = \lim b_n$. Then $a_m \leq \alpha \leq \beta \leq b_n$ for all $m, n$, so $[\alpha, \beta] \subseteq I_n$ for every $n$.
> (2) $b_n - a_n \geq \beta - \alpha$ and $b_n - a_n \to 0$, so $\alpha = \beta$. If $x < y$ were both in every $I_n$, then $0 < y - x < b_n - a_n$ for all $n$, impossible. So the intersection is $\{\alpha\}$. $\square$

> [!example]- Example 5.8: $x^n / n! \to 0$ (real and complex)
> (a) For $x \neq 0$ let $a_n = |x|^n / n!$. Then $\frac{a_{n+1}}{a_n} = \frac{|x|}{n+1} \to 0$, so eventually $a_{n+1} < a_n$: a tail is decreasing and bounded below by 0, so $a_n \to L$. From $a_{n+1} = \frac{|x|}{n+1}a_n$, AOL gives $L = 0 \times L = 0$.
> (b) For $z \in \mathbb{C}$, $|z^n/n!| = |z|^n / n! \to 0$. $\square$

> [!example]- Example 5.9: existence and uniqueness of $\sqrt a$ (Babylonian / Newton–Raphson)
> **(a)** Let $a \geq 1$, $x_0 = a$, $x_{n+1} = \frac12\left(x_n + \frac{a}{x_n}\right)$. Claims:
> 1. $a \leq x_n^2$ for all $n$: true for $n = 0$ since $a^2 - a \geq 0$; and
> $$x_{n+1}^2 - a = \frac{1}{4x_n^2}\left[(x_n^2 + a)^2 - 4ax_n^2\right] = \frac{(x_n^2 - a)^2}{4x_n^2} \geq 0.$$
> 2. $(x_n)$ is decreasing: $x_n - x_{n+1} = \frac{x_n^2 - a}{2x_n} \geq 0$.
> 3. So $x_n \to L$ (decreasing, bounded below). AOL in the recurrence gives $L = \frac12(L + a/L)$, i.e. $L^2 = a$, and $L \geq 0$. Since $x^2 - a = (x - L)(x + L)$, the square roots of $a$ are exactly $\pm L$: a unique positive one.
> 
> **(b)** For $0 < a < 1$: $x^2 = a \iff (1/x)^2 = a^{-1} \iff 1/x = \pm\sqrt{a^{-1}}$, so $\sqrt a = (\sqrt{a^{-1}})^{-1}$ is the unique positive root. ($0$ is the only root of $0$.) $\square$

> [!note]- Remarks 5.10 – 5.11 (Newton–Raphson and cobwebbing)
> **Newton–Raphson** for $f(x) = 0$: $x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}$ (follow the tangent at $x_n$ to the $x$-axis). For $f(x) = x^2 - a$ this is exactly $x_{n+1} = \frac12(x_n + a/x_n)$.
> 
> **Cobwebbing** solves $x = f(x)$ by iterating $x_{n+1} = f(x_n)$: draw $y = x$ and $y = f(x)$, go vertically to the curve then horizontally to the line, and repeat. If $x_n \to \alpha$ then $\alpha = f(\alpha)$ is a fixed point. Near it, $x_{n+1} - \alpha \approx f'(\alpha)(x_n - \alpha)$:
> - $|f'(\alpha)| < 1$: **attracting** fixed point (monotone convergence if $0 < f'(\alpha) < 1$, oscillating if $-1 < f'(\alpha) < 0$);
> - $|f'(\alpha)| > 1$: **repelling**, and generally no convergence.
> 
> For $f(x) = \frac12(x + a/x)$, $f'(\sqrt a) = 0$, so convergence is fast. (A picture proves nothing, but it guides the proof.)

> [!example]- Example 5.12 (Decimal expansions)
> For $0 < x \leq 1$ there is a unique sequence of integers $a_1, a_2, \dots$ with
> 1. $0 \leq a_n \leq 9$;
> 2. $x - \frac{1}{10^n} \leq \sum_{k=1}^n \frac{a_k}{10^k} < x$ for each $n$;
> 3. $\sum_{k=1}^n \frac{a_k}{10^k} \to x$.
> 
> *Proof (induction).* $a_1$ must satisfy $10x - 1 \leq a_1 < 10x$: the interval $[10x - 1, 10x)$ contains exactly one integer, and $-1 < 10x - 1 \leq a_1 < 10x \leq 10$ gives $0 \leq a_1 \leq 9$.
> Given $a_1, \dots, a_N$, condition (2) for $N + 1$ rearranges to
> $$\left(10^{N+1}x - \sum_{k=1}^N 10^{N+1-k}a_k\right) - 1 \leq a_{N+1} < 10^{N+1}x - \sum_{k=1}^N 10^{N+1-k}a_k,$$
> which has a unique integer solution. By the hypothesis $0 < x - \sum_{k \leq N} 10^{-k}a_k \leq 10^{-N}$, so $-1 < a_{N+1} < 10$. Sandwiching (2) gives (3). Write $x = 0.a_1a_2a_3\dots$, the **decimal expansion**. $\square$
> 
> **Remark 5.13** In this convention $\frac15 = 0.1999\dots$, not $0.2000\dots$: the truncations never equal $x$, which removes the ambiguity. The same works in any base $b \geq 2$ (e.g. $\frac12 = 0.0111\dots_2$).

## Subsequences

> [!example]- Example 5.14 (subsequences of $1/n^2$)
> From $(1, \frac14, \frac19, \frac1{16}, \dots)$: everything after the second place $(\frac19, \frac1{16}, \dots)$, all odd terms $(1, \frac19, \frac1{25}, \dots)$, all prime terms $(\frac14, \frac19, \frac1{25}, \frac1{49}, \dots)$. Here $n_r = r + 2$, $n_r = 2r - 1$, $n_r = p_r$ respectively (Example 5.16).

> **Definition 5.15 (Subsequence)**
> $(b_n)$ is a **subsequence** of $(a_n)$ if there is a strictly increasing sequence of natural numbers $(f(n))$ with $b_n = a_{f(n)}$. Usually written $n_r = f(r)$ and $(a_{n_r})_{r=1}^\infty$.

> [!example]- Example 5.17
> $(a_n) = (n^2)$, $(b_n) = (0)$, $f(n) = 2n$, $g(n) = 2n - 1$:
> $(a_{f(n)}) = (4, 16, 36, \dots)$, $(a_{g(n)}) = (1, 9, 25, \dots)$, and both subsequences of $(b_n)$ are $(0, 0, 0, \dots)$.

> **Proposition 5.18**
> If $a_n \to L$ then every subsequence $a_{n_r} \to L$.

> [!proof]- Proof
> Take $N$ with $|a_n - L| < \varepsilon$ for $n \geq N$. Since $r \mapsto n_r$ is strictly increasing, $n_r \geq r$, so $r \geq N \Rightarrow n_r \geq N \Rightarrow |a_{n_r} - L| < \varepsilon$. $\square$

The converse "all subsequences converge to $L$ ⇒ $a_n \to L$" is trivially true (the sequence is a subsequence of itself), but **one** convergent subsequence isn't enough: $(-1)^n$ diverges though $a_{2n} \to 1$.

> **Theorem 5.19**
> Every real sequence has a monotone subsequence.

> [!proof]- Proof ("scenic viewpoints")
> Let $V = \{k \in \mathbb{N} : m > k \Rightarrow a_m < a_k\}$: the points $(k, a_k)$ from which you can see all the way to $\infty$ with nothing as tall in the way.
> - **$V$ infinite:** list it $k_1 < k_2 < \dots$; then $r > s \Rightarrow a_{k_r} < a_{k_s}$, so $(a_{k_r})$ is strictly decreasing.
> - **$V$ finite:** let $m_1$ be past the last viewpoint. Since $m_1$ isn't a viewpoint, there's $m_2 > m_1$ with $a_{m_2} \geq a_{m_1}$; since $m_2$ isn't one, there's $m_3 > m_2$ with $a_{m_3} \geq a_{m_2}$; and so on. This gives an increasing subsequence $(a_{m_k})$. $\square$

> **Theorem 5.20 (Bolzano–Weierstrass, Bolzano 1817, Weierstrass c.1861)**
> Every bounded real sequence has a convergent subsequence.

> [!proof]- Proof
> By Theorem 5.19 there's a monotone subsequence; it's bounded, so it converges by Theorem 5.3 (or Cor 5.5). $\square$

> **Theorem 5.21 (Bolzano–Weierstrass in $\mathbb{C}$)**
> Every bounded complex sequence has a convergent subsequence.

> [!proof]- Proof
> With $z_n = x_n + iy_n$, both $(x_n), (y_n)$ are bounded. B–W gives $x_{n_k} \to L_1$. Then $(y_{n_k})$ is bounded, so has a subsequence $y_{n_{k_r}} \to L_2$. Also $x_{n_{k_r}} \to L_1$ (Prop 5.18), so $z_{n_{k_r}} \to L_1 + iL_2$ (Theorem 3.25). $\square$

> **Definition 5.22 (Limit point)**
> $x$ is a **limit point** (accumulation point) of $S \subseteq \mathbb{R}$ if for every $\varepsilon > 0$ there is $y \in S$ with $0 < |y - x| < \varepsilon$. ($x$ need not be in $S$.) The set of limit points is $S'$.

> [!example]- Example 5.23
> Limit points of $(0, 1)$: $[0, 1]$. Of $\mathbb{Q}$: $\mathbb{R}$. Of $\mathbb{Z}$: $\varnothing$. Of $\{1, \frac12, \frac13, \dots\}$: $\{0\}$.

**Remark 5.24 (B–W restated)** Every infinite bounded subset of $\mathbb{R}$ or $\mathbb{C}$ has a limit point. (Pick a sequence of distinct points of $S$; a convergent subsequence's limit is a limit point.)
