Analysis I, Chapter 6.2. Back to [[A1]]. Builds on [[A1 - Infinite Series]].

Tests won't always apply directly, but they suggest which estimates to make. Real series often need a combination of tests.

## Divergence and Comparison

> **Proposition 6.20 (A Simple Test for Divergence)**
> If $\sum a_n$ converges then $a_n \to 0$. The converse is false.
> In practice use the contrapositive: **if $a_n \not\to 0$ then $\sum a_n$ diverges.**

> **Theorem 6.21 (The Comparison Test)**
> Let $0 \leq a_n \leq b_n$. Then
> - $\sum b_n$ converges ⇒ $\sum a_n$ converges;
> - $\sum a_n$ diverges ⇒ $\sum b_n$ diverges.

> [!proof]- Proof
> The second is the contrapositive of the first. If $\sum b_k$ converges, then $\sum_1^n a_k \leq \sum_1^n b_k \leq \sum_1^\infty b_k$, so the partial sums of $\sum a_k$ are increasing and bounded. $\square$

Typical use: compare $|a_n|$ with something to show $\sum a_n$ is AC, hence convergent. It also absorbs awkward but harmless factors, like $(2 + \cos n)^{-1} \in [\frac13, 1]$ (Remark 6.22).

> [!example]- Example 6.23 (comparison in action)
> All converge:
> (a) $\sum n^{-5/2}$: compare with $\sum n^{-2}$.
> (b) $\sum \frac{1}{n(n+1)(2 + \cos n)}$: compare with $\sum n^{-2}$.
> (c) $\sum \frac{x^n}{n}$, $|x| < 1$: AC by comparison with $\sum |x|^n$.
> (d) $\sum \frac{\sin n}{n^2 + 1}$: AC by comparison with $\sum n^{-2}$.

## Ratio Test

> **Theorem 6.24 (The Ratio Test)**
> Let $a_n \neq 0$ for all $n$ and suppose $L = \lim_{n \to \infty} \left|\frac{a_{n+1}}{a_n}\right|$ exists.
> - $L < 1$: $\sum a_n$ converges absolutely.
> - $L > 1$: $\sum a_n$ diverges.
> - $L = 1$: inconclusive.

> [!proof]- Proof
> (a) Choose $L < K < 1$. With $\varepsilon = K - L$, there's $N$ with $\left|\frac{a_{n+1}}{a_n}\right| \leq K$ for $n \geq N$. So
> $$|a_{N+k}| = \left|\frac{a_{N+k}}{a_{N+k-1}}\right| \cdots \left|\frac{a_{N+1}}{a_N}\right| |a_N| \leq |a_N| K^k.$$
> $\sum K^k$ is a convergent geometric series, so the tail $\sum_N^\infty a_n$ is AC by comparison, hence so is $\sum a_n$.
> (b) Choose $1 < K < L$; eventually $|a_{n+1}/a_n| > K$, so $|a_{N+k}| \geq K^k |a_N|$ and $a_n \not\to 0$. Diverges by 6.20.
> (c) $\sum n^{-1}$ and $\sum n^{-2}$ both have $L = 1$; the first diverges, the second converges. $\square$

A convergent positive series needn't have a limiting ratio: $1 + \frac13 + \frac12 + \frac19 + \frac14 + \frac1{27} + \frac18 + \dots$ converges absolutely, but $|a_{n+1}/a_n|$ has no limit (Remark 6.25).

> [!example]- Example 6.26: the exponential series converges absolutely for all $x \in \mathbb{C}$
> For $x \neq 0$: $\left|\frac{a_{n+1}}{a_n}\right| = \frac{|x|}{n+1} \to 0 < 1$. Ratio test. $\square$

> [!example]- Example 6.27: $\sum (\sinh n) x^n$
> AC for $|x| < e^{-1}$, divergent for $|x| \geq e^{-1}$. With $\sinh n = \frac{e^n - e^{-n}}{2}$:
> $$\left|\frac{a_{n+1}}{a_n}\right| = \frac{e^{n+1} - e^{-n-1}}{e^n - e^{-n}}|x| = \frac{e - e^{-2n-1}}{1 - e^{-2n}}|x| \to e|x|.$$
> At $|x| = e^{-1}$ the test is inconclusive, but there $|a_n| = \sinh n \cdot e^{-n} \to \frac12 \neq 0$, so the series diverges. $\square$

## Alternating Series

> **Theorem 6.28 (Leibniz Alternating Series Test, 1676)**
> If $(a_n)$ is non-negative, decreasing and $a_n \to 0$, then $\sum_{n=0}^\infty (-1)^n a_n$ converges.

> [!proof]- Proof
> With $s_n = \sum_0^n (-1)^k a_k$:
> $$s_{2k} = (a_0 - a_1) + (a_2 - a_3) + \dots + (a_{2k-2} - a_{2k-1}) + a_{2k}$$
> is increasing (each bracket $\geq 0$), and
> $$s_{2k} = a_0 + (-a_1 + a_2) + (-a_3 + a_4) + \dots + (-a_{2k-1} + a_{2k}) \leq a_0.$$
> So $s_{2k} \to L$. Then $s_{2k+1} = s_{2k} - a_{2k+1} \to L - 0 = L$. When both the even and odd subsequences converge to $L$, $s_k \to L$ (Sheet 5, Ex 4(i)). $\square$

## Integral Test

This uses integration (Analysis III) and logarithms (see [[A1 - Elementary Functions]]) before they're properly developed. There's no circularity (Remark 6.29).

> **Theorem 6.30**
> Let $K \in \mathbb{N}$ and $f : [K, \infty) \to [0, \infty)$ be continuous and decreasing. For $n > K$ let
> $$\delta_n = \sum_{k=K}^{n-1} f(k) - \int_K^n f(x)\,dx.$$
> Then $0 \leq \delta_n \leq \delta_{n+1} \leq f(K)$, so $\delta_n$ converges.

> **Corollary 6.31 (The Integral Test)**
> With $f$ as above, $\sum_K^\infty f(k)$ converges iff $\int_K^n f(x)\,dx$ converges as $n \to \infty$.

> [!proof]- Proof of Theorem 6.30
> As $f$ is decreasing, $f(k+1) \leq f(x) \leq f(k)$ on $[k, k+1]$. Integration preserves weak inequalities, $\int_n^{n+1} 1\,dx = 1$, and $\int$ is additive and linear, so
> $$f(k+1) \leq \int_k^{k+1} f(x)\,dx \leq f(k).$$
> Adding these: $f(K+1) + \dots + f(n) \leq \int_K^n f \leq f(K) + \dots + f(n-1)$.
> - The right inequality gives $\delta_n \geq 0$.
> - The left gives $\delta_n \leq \sum_{K}^{n-1} f(r) - \sum_{K+1}^n f(r) = f(K) - f(n) \leq f(K)$.
> - $\delta_{n+1} - \delta_n = f(n) - \int_n^{n+1} f \geq 0$.
> 
> So $(\delta_n)$ is increasing and bounded above, hence convergent. Picture: $\delta_n$ is the "excess area" of the step function above the graph. The sum and the integral differ by a convergent sequence, so they converge or diverge together (AOL). $\square$

> [!example]- Example 6.32: $\sum \frac{1}{n^\alpha}$ converges iff $\alpha > 1$
> If $\alpha \leq 0$, the terms don't tend to 0. For $\alpha > 0$, $f(x) = x^{-\alpha}$ is positive, continuous and decreasing. With $K = 1$:
> - $\alpha \neq 1$: $\int_1^n t^{-\alpha}\,dt = \frac{n^{1-\alpha} - 1}{1 - \alpha}$ converges iff $\alpha > 1$.
> - $\alpha = 1$: $\int_1^n \frac{dt}{t} = \log n$ diverges.
> 
> So $\sum n^{-\alpha}$ converges for $\alpha > 1$ and diverges for $\alpha \leq 1$.

> [!example]- Example 6.33: $\sum \frac{1}{n \log n}$ diverges
> $f(x) = \frac{1}{x \log x}$ is decreasing on $(2, \infty)$ and $\int_2^n \frac{dx}{x\log x} = \log\log n - \log\log 2 \to \infty$.

> [!example]- Example 6.34 (Euler's constant $\gamma$, 1734)
> With $f(x) = 1/x$: $\gamma_n = 1 + \frac12 + \dots + \frac1n - \log n = \delta_n + \frac1n$ converges. Its limit
> $$\gamma = \lim_{n \to \infty}\left(\sum_1^n \frac1k - \log n\right) \approx 0.5772156649\dots$$
> is **Euler's constant**. Whether $\gamma$ is irrational is still open. It's used to show $1 - \frac12 + \frac13 - \dots = \log 2$ (Example 6.35, Sheet 6 Ex 6).

## $e$ and Stirling

> **Example 6.36 (Euler's number)**
> $e = \sum_{r=0}^\infty \frac{1}{r!} = 1 + 1 + \frac1{2!} + \frac1{3!} + \dots \approx 2.718281828\dots$ converges to an irrational number (Sheet 4, Ex 5). Bernoulli (1683) defined it as $\lim (1 + \frac1n)^n$.

> **Proposition 6.37 (Euler, 1748)**
> $$e = \lim_{n \to \infty}\left(1 + \frac1n\right)^n.$$

> [!proof]- Proof
> Let $\alpha_n = (1 + \frac1n)^n$ (increasing and bounded, Sheet 1 Ex 6, so convergent) and $\beta_n = \sum_0^n \frac{1}{k!} \to e$. By the binomial theorem
> $$\alpha_n = 1 + 1 + \frac{1}{2!}\left(1 - \tfrac1n\right) + \frac{1}{3!}\left(1 - \tfrac1n\right)\left(1 - \tfrac2n\right) + \dots \leq \beta_n,$$
> so $\lim \alpha_n \leq e$. For fixed $m < n$, keeping only the first $m + 1$ terms:
> $$1 + 1 + \left(1 - \tfrac1n\right)\frac{1}{2!} + \dots + \left(1 - \tfrac1n\right)\cdots\left(1 - \tfrac{m-1}{n}\right)\frac{1}{m!} \leq \alpha_n.$$
> Let $n \to \infty$ (AOL, limits respect $\leq$): $\sum_0^m \frac{1}{k!} \leq \lim \alpha_n$. Then $m \to \infty$ gives $e \leq \lim \alpha_n$. $\square$

**Remark 6.38 (Why fix $m$ first?)** AOL applies to a **fixed** finite number of terms. Otherwise $1 = \underbrace{\tfrac1n + \dots + \tfrac1n}_{n} \to 0 + 0 + \dots = 0$.

> [!example]- Example 6.39 (combining tests)
> - $\sum \frac{\cos(n^2 + 1)}{n^2 + \log n}$: $\left|\frac{\cos(n^2+1)}{n^2 + \log n}\right| \leq \frac{1}{n^2}$, so AC by comparison.
> - $\sum (-1)^n \frac{\log(n^2 + 1)}{\sqrt{n + 2}}$: with $y(x) = \log(x^2 + 1)(x+2)^{-1/2}$,
> $$y'(x) = \frac{1}{(x+2)^{3/2}}\left[\frac{2x(x+2)}{x^2 + 1} - \frac12\log(x^2 + 1)\right] < \frac{1}{(x+2)^{3/2}}\left[4 - \frac12\log(x^2+1)\right] < 0 \text{ for } x > e^4.$$
> So the terms are eventually decreasing (to 0); Leibniz on a tail gives convergence.
> - $\sum \frac{1}{\sqrt{n^2 + n}}$: $\frac{1}{\sqrt{n^2 + n}} > \frac{1}{\sqrt{2n^2}} = \frac{1}{n\sqrt2}$, so it diverges by comparison with the harmonic series.
> - $\sum \frac{\sqrt{n+1} - \sqrt n}{\sqrt{n^2 + n}}$: each term is $\frac{1}{\sqrt n} - \frac{1}{\sqrt{n+1}}$, so it telescopes: $\sum_1^N = 1 - \frac{1}{\sqrt{N+1}} \to 1$.

> **Proposition 6.40 (Stirling's Approximation, 1730)** *(proof off-syllabus)*
> $$\frac{n!}{\sqrt{2\pi n}\,(n/e)^n} \to 1, \qquad \text{i.e.} \quad n! \sim \sqrt{2\pi n}\left(\frac ne\right)^n.$$

> [!proof]- Proof (trapezium rule for $\log x$)
> $\log n! = \log 2 + \dots + \log n$. Let $f$ be the piecewise-linear interpolant of $\log x$ at $1, 2, \dots, n$ (the trapezium rule). For $k \leq x \leq k+1$, $\frac{1}{k+1} \leq \frac1x \leq \frac1k$, and integrating gives $\log k + \frac{x - k}{k+1} \leq \log x \leq \log k + \frac{x-k}{k}$. Since $\log$ is concave, $f \leq \log$, and $f$'s slope (the average gradient) is at least $\frac{1}{k+1}$, so
> $$0 \leq \log x - f(x) \leq \left(\frac1k - \frac{1}{k+1}\right)(x - k) \quad \text{on } [k, k+1].$$
> Integrating and summing (telescoping):
> $$0 \leq I_n = \int_1^n (\log x - f(x))\,dx \leq \frac12\left(1 - \frac1n\right).$$
> Using $\int \log x = x\log x - x$ and the trapezium formula,
> $$I_n = \left(n + \tfrac12\right)\log n - n + 1 - \log n!.$$
> $(I_n)$ is increasing and bounded by $\frac12$, so $I_n \to L$, giving $e^{L-1} = \lim \frac{(n/e)^n\sqrt n}{n!}$. Combined with $\binom{2n}{n}\frac{\sqrt n}{2^{2n}} \to \frac{1}{\sqrt\pi}$ (Sheet 6, Ex 11(ii)):
> $$\frac{1}{\sqrt\pi} = \lim \frac{(2n)!}{n!\,n!}\frac{\sqrt n}{2^{2n}} = \sqrt2 \times (e^{L-1})^{-1} \times (e^{L-1})^2 = \sqrt2\, e^{L-1}.$$
> So $e^{1-L} = \sqrt{2\pi}$ and $\frac{n!}{\sqrt{2\pi n}(n/e)^n} \to \frac{e^{1-L}}{\sqrt{2\pi}} = 1$. $\square$

> [!note]- Remark 6.41 (accuracy of Stirling)
> Stirling slightly underestimates; the relative error is under 1% at $n = 10$. Better: $n! = \sqrt{2\pi n}(n/e)^n(1 + O(1/n))$, and more precisely
> $$n! = \sqrt{2\pi n}\left(\frac ne\right)^n \exp\left\{\sum_{k=2}^m \frac{(-1)^k B_k}{k(k-1)n^{k-1}} + O\left(\frac{1}{n^m}\right)\right\},$$
> with $B_k$ the Bernoulli numbers (Sheet 7, Ex 9).
