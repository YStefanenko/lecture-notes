Analysis I, Chapter 7.1. Back to [[A1]]. Next: [[A1 - Elementary Functions]].

> **Definition 7.1 (Power series)**
> A **power series** is $\sum_{n=0}^\infty a_n z^n$, with $(a_n)$ a fixed complex sequence and $z \in \mathbb{C}$ variable.

Power series centred at $z_0$, $\sum a_n (z - z_0)^n$, work identically (Remark 7.2).

> [!example]- Example 7.3 (standard power series)
> - **Geometric** $\sum z^n$ ($a_n = 1$): converges for $|z| < 1$, diverges for $|z| \geq 1$.
> - **Exponential** $\sum z^n / n!$: converges for all $z$ (Example 6.26).
> - **Logarithmic** $\sum_{n \geq 1} z^n / n$: ratio $\frac{n|z|}{n+1} \to |z|$, so converges for $|z| < 1$. On $|z| = 1$: converges at $z = -1$ (Leibniz), diverges at $z = 1$ (harmonic). At $z = i$, real and imaginary parts are both alternating series, and the sum is $-\frac12\log2 + \frac{i\pi}{4}$. In fact it converges everywhere on $|z| = 1$ except $z = 1$.
> - **Cosine** $\sum \frac{(-1)^n}{(2n)!}z^{2n}$ and **sine** $\sum \frac{(-1)^n}{(2n+1)!}z^{2n+1}$: converge for all $z$ (ratio test).

> **Definition 7.4 (Radius of convergence)**
> Let $S = \{z \in \mathbb{C} : \sum a_n z^n \text{ converges}\}$ (non-empty, as $0 \in S$). The **radius of convergence** is
> $$R = \begin{cases} \sup\{|z| : z \in S\} & S \text{ bounded} \\ \infty & S \text{ unbounded.} \end{cases}$$

> **Lemma 7.5**
> If $\sum a_n z_0^n$ converges, then $\sum a_n z^n$ converges absolutely whenever $|z| < |z_0|$.

> [!proof]- Proof
> $a_n z_0^n \to 0$, so it's bounded: $|a_n z_0^n| < M$. For $|z| < |z_0|$:
> $$|a_n z^n| = |a_n z_0^n|\left|\frac{z}{z_0}\right|^n < M\left|\frac{z}{z_0}\right|^n,$$
> a convergent geometric series. Comparison. $\square$

> **Theorem 7.6**
> If $\sum a_n z^n$ has radius of convergence $R$, then it is AC for $|z| < R$ and diverges for $|z| > R$. (If $R = \infty$, AC for all $z$.)

> [!proof]- Proof
> If $|z| < R$, the approximation property gives $z_0 \in S$ with $|z| < |z_0| < R$; apply Lemma 7.5. If $|z| > R$ then $z \notin S$. $\square$

> **Definition 7.7 (Disc of convergence)** The set $S$ is the **disc of convergence**.

On the boundary $|z| = R$ anything can happen. Which subsets of the circle can be exactly the convergence set is still an open problem (Remark 7.8).

Usually the ratio test finds $R$, but not always (Remark 7.9). *Off-syllabus* exact formula from Cauchy's root test (Remark 7.10):
$$R = \left(\limsup \sqrt[n]{|a_n|}\right)^{-1}. \tag{7.1}$$

> [!example]- Example 7.11 (radius and boundary behaviour)
> - $\sum z^n / n^2$: ratio $(1 + \frac1n)^2 |z| \to |z|$, so $R = 1$; on $|z| = 1$ it's AC by comparison with $\sum n^{-2}$.
> - $\sum z^n / n$: $R = 1$; diverges at $z = 1$, converges elsewhere on $|z| = 1$.
> - $\sum_{p \text{ prime}} z^p$: $R = 1$. The ratio test is awkward here; instead $z^p \not\to 0$ for $|z| \geq 1$, while for $|z| < 1$ it is AC by comparison with $\sum z^n$.
> - Cosine series: $\frac{|z|^{2n+2}/(2n+2)!}{|z|^{2n}/(2n)!} = \frac{|z|^2}{(2n+2)(2n+1)} \to 0$, so AC for all $z$.
> - Sine series: $\frac{|z|^2}{(2n+2)(2n+3)} \to 0$, so AC for all $z$.

> [!example]- Example 7.12 (using (7.1))
> - $a_n = \frac1n$: $n^{1/n} \to 1$, so $\limsup \sqrt[n]{|a_n|} = 1$ and $R = 1$.
> - $\sum_p z^p$: $a_p = 1$ for infinitely many $p$, so $\limsup = 1$ and $R = 1$.
> - $a_n = \frac{1}{n!}$: by Stirling, $\sqrt[n]{1/n!} \sim \frac{1}{\sqrt[2n]{2\pi n}}\cdot\frac en \to 0$, so $R = \infty$.

> **Theorem 7.13 (Term-by-term differentiation)** *(proved in Hilary Term)*
> If $\sum_0^\infty a_n z^n$ has radius of convergence $R$, it defines a differentiable function on $|z| < R$, and
> $$\frac{d}{dz}\sum_0^\infty a_n z^n = \sum_1^\infty n a_n z^{n-1} = \sum_0^\infty (n+1)a_{n+1}z^n.$$
> This **derived series** also has radius of convergence $R$.

> **Remark 7.14 (Uniqueness of coefficients)**
> If $f(x) = \sum a_n x^n$ on $|x| < R$, repeated differentiation gives
> $$a_n = \frac{f^{(n)}(0)}{n!}.$$
> So if $f$ is locally a power series (**analytic**), its coefficients are unique. In particular, if an analytic $f$ has $f' = 0$ everywhere then $f = a_0$ is constant.

> [!note]- Remark 7.15 (smooth ≠ analytic)
> Analytic functions are **smooth** (derivatives of all orders), but not conversely:
> $$f(x) = \begin{cases} e^{-1/x^2} & x \neq 0 \\ 0 & x = 0 \end{cases}$$
> has $f^{(n)}(0) = 0$ for all $n$, so its power series would be $0$, yet $f(x) \neq 0$ for $x \neq 0$. (For complex functions it's different: differentiable once on a disc implies analytic, Part A Complex Analysis.)

> **Proposition 7.16** A product of analytic functions is analytic.

> [!proof]- Proof
> If $f(z) = \sum a_n z^n$ and $g(z) = \sum b_n z^n$ converge for $|z| < R$, then by the Cauchy product $f(z)g(z) = \sum c_n$ with
> $$c_n = \sum_{k=0}^n (a_k z^k)(b_{n-k}z^{n-k}) = \left(\sum_{k=0}^n a_k b_{n-k}\right)z^n.$$
> So $fg = \sum d_n z^n$ with $d_n = c_n / z^n$, analytic on $|z| < R$. $\square$

> **Proposition 7.17**
> Let $f(x) = \sum_0^\infty a_n x^n$ converge on $(-R, R)$.
> 1. $f$ is even iff $a_{2n+1} = 0$ for all $n \geq 0$.
> 2. $f$ is odd iff $a_{2n} = 0$ for all $n \geq 0$.

> [!proof]- Proof of (1)
> If all $a_{2n+1} = 0$, then $f(x) = \sum a_{2n}x^{2n} = \sum a_{2n}(-x)^{2n} = f(-x)$.
> Conversely, if $f$ is even then (chain rule) $f^{(n)}$ is even for even $n$ and odd for odd $n$. So $f^{(2n+1)}(0) = 0$ and $a_{2n+1} = \frac{f^{(2n+1)}(0)}{(2n+1)!} = 0$. (2) is almost identical. $\square$
