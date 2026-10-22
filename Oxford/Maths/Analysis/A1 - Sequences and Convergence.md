Analysis I, Chapter 3. Back to [[A1]]. Next: [[A1 - Algebra of Limits]].

## Sequences

> **Definitions 3.1 – 3.3 (Sequences)**
> A **real sequence** is a function $a : \mathbb{N} \to \mathbb{R}$; a **complex sequence** is $a : \mathbb{N} \to \mathbb{C}$. ($\mathbb{N}$ may start at 0 or 1.)
> The **$n$th term** is $a(n)$, written $a_n$. The sequence is written $(a_n)$ or $(a_n)_{n=1}^\infty$.

Sums, scalar multiples, products and quotients of sequences are defined termwise ($(a_n/b_n)$ needs every $b_n \neq 0$). Different $n$ can give the same term: the function needn't be injective.

> [!example]- Examples 3.4 & 3.5
> **3.4** $\alpha(n) = (-1)^n$, $\beta(n) = 0$, $\gamma(n) = n$.
> **3.5** With $a_n = (-1)^n$, $b_n = 1$: $(a_n + b_n) = (0, 2, 0, 2, \dots)$, $(-a_n) = ((-1)^{n+1})$, $(a_n b_n) = (a_n)$, $(a_n^2) = (b_n)$.

## Convergence

> **Definition 3.6 (Convergence)**
> A real sequence $(a_n)$ **converges to** (or **tends to**) $L \in \mathbb{R}$ if
> $$\forall \varepsilon > 0 \ \ \exists N \in \mathbb{N} \ \ \forall n \geq N \quad |a_n - L| < \varepsilon.$$
> Write $(a_n) \to L$, or $a_n \to L$ as $n \to \infty$.

$N$ may (and usually will) depend on $\varepsilon$: smaller $\varepsilon$ needs larger $N$. You don't need the *smallest* $N$, just one that works (Remark 3.10).

> **Definition 3.7 (Limit)** If $a_n \to L$, $L$ is a **limit** of $(a_n)$: $L = \lim_{n \to \infty} a_n$.

> **Definition 3.8 (Convergent)**
> $(a_n)$ **converges** if $\exists L \in \mathbb{R} \ \forall \varepsilon > 0 \ \exists N \in \mathbb{N} \ \forall n \geq N \ |a_n - L| < \varepsilon$.

> **Definition 3.9 (Divergent)**
> $(a_n)$ **diverges** if it does not converge:
> $$\forall L \in \mathbb{R} \ \ \exists \varepsilon > 0 \ \ \forall N \in \mathbb{N} \ \ \exists n \geq N \quad |a_n - L| \geq \varepsilon.$$

To show convergence, first guess the candidate limit $L$, then prove $a_n \to L$.

**Remark 3.11** It's enough to check $\varepsilon \in (0, 1)$ (or $(0, \varepsilon_0)$ for any fixed $\varepsilon_0 > 0$): being eventually within $0.5$ of $L$ also means being eventually within $2$.

> **Definition 3.12 (Tails and neighbourhoods)**
> The **$k$th tail** of $(a_n)$ is $n \mapsto a_{n+k}$, i.e. $(a_k, a_{k+1}, \dots)$, written $(a_{n+k})_{n=0}^\infty$ or $(a_n)_k^\infty$.
> For $\varepsilon > 0$, $(L - \varepsilon, L + \varepsilon)$ is a (basic) **neighbourhood** of $L$.

So: $a_n \to L$ iff **every neighbourhood of $L$ contains a tail of $(a_n)$**. Convergence depends only on long-term behaviour.

> **Proposition 3.13**
> For a real sequence $(a_n)$ and $L \in \mathbb{R}$, these are equivalent:
> 1. $(a_n)$ converges to $L$;
> 2. some tail of $(a_n)$ converges to $L$;
> 3. all tails of $(a_n)$ converge to $L$.

> [!proof]- Proof
> (1 ⇒ 3) Given $k$ and $\varepsilon$, take $N$ with $|a_n - L| < \varepsilon$ for $n \geq N$. Then $n + k \geq N$, so $|a_{n+k} - L| < \varepsilon$ for $n \geq N$.
> (3 ⇒ 2) Clear.
> (2 ⇒ 1) If the $k$th tail converges: $|a_{n+k} - L| < \varepsilon$ for $n \geq N$, so $|a_n - L| < \varepsilon$ for $n \geq N + k$. $\square$

**Remark 3.14 (Intersection of tails)** If one fact holds for $n \geq N_1$ and another for $n \geq N_2$, both hold for $n \geq \max(N_1, N_2)$. This works for finitely many facts only: infinitely many tails can have empty intersection (e.g. $N_k = k^2$).

> **Theorem 3.15 (Uniqueness of Limits)**
> If $a_n \to L_1$ and $a_n \to L_2$ then $L_1 = L_2$.

> [!proof]- Proof
> Suppose not; let $\varepsilon = |L_1 - L_2| > 0$. There are $N_1, N_2$ with $|a_n - L_1| < \varepsilon/2$ for $n \geq N_1$ and $|a_n - L_2| < \varepsilon/2$ for $n \geq N_2$. For $n \geq \max(N_1, N_2)$:
> $$|L_1 - L_2| \leq |L_1 - a_n| + |a_n - L_2| < \varepsilon = |L_1 - L_2|,$$
> a contradiction. $\square$
> 
> *Idea:* two different limits would need tails in two disjoint neighbourhoods at once.

> [!example]- Example 3.16: $\frac{2^n - 1}{2^n} \to 1$
> $|a_n - 1| = 2^{-n}$. Let $\varepsilon > 0$. Since $2^n > n$, for $N > 1/\varepsilon$ (Archimedean property) and $n \geq N$:
> $$|a_n - 1| = \frac{1}{2^n} < \frac1n \leq \frac1N < \varepsilon. \quad \square$$

> [!example]- Example 3.17: $\frac{n^2 + n + 1}{3n^2 + 4}$ converges (to $\frac13$)
> Guess: $\frac{1 + 1/n + 1/n^2}{3 + 4/n^2} \approx \frac13$. Let $\varepsilon > 0$:
> $$\left|a_n - \frac13\right| = \frac{3n - 1}{3(3n^2 + 4)} \leq \frac{3n}{3(3n^2 + 4)} \leq \frac{3n}{3 \cdot 3n^2} < \frac1n.$$
> Take $N > 1/\varepsilon$; then for $n \geq N$, $|a_n - \frac13| < \frac1n \leq \frac1N < \varepsilon$. $\square$

> [!example]- Example 3.18: $\frac{(-1)^n n^2}{n^2 + 1}$ diverges
> Even terms $\approx 1$, odd terms $\approx -1$ (in fact $a_{2n} \geq \frac45$, $a_{2n-1} \leq -\frac12$).
> Suppose $a_n \to L$; take $\varepsilon = \frac12$ and $N$ with $|a_n - L| < \frac12$ for $n \geq N$.
> - Even $n \geq N$: $\frac{n^2}{n^2+1} - L < \frac12$, so $L > \frac{1}{1 + n^{-2}} - \frac12 \geq \frac{1}{5/4} - \frac12 = \frac{3}{10}$.
> - Odd $n \geq N$: $L + \frac{n^2}{n^2+1} < \frac12$, so $L < \frac12 - \frac{1}{1 + n^{-2}} \leq \frac12 - \frac12 = 0$.
> 
> $L > \frac{3}{10}$ and $L < 0$: contradiction. $\square$

> **Corollary 3.19**
> If $a > 1$ and $k$ is a positive integer, then $\dfrac{n^k}{a^n} \to 0$.

> [!proof]- Proof
> By Prop 1.46 (with $k + 1$) there's $c > 0$ with $a^n / n^{k+1} \geq c$ for $n \geq 1$, so $0 < n^k / a^n \leq \frac{1}{cn}$. Given $\varepsilon$, the Archimedean property gives $N$ with $\frac{1}{cn} < \varepsilon$ for $n \geq N$. $\square$

> **Proposition 3.20 (Convergent sequences are bounded)**
> A convergent real sequence is bounded. *(Sheet 3, Ex 5(iii).)*

*Idea:* a tail lies in $(L - 1, L + 1)$, and only finitely many terms are outside that tail.

## Complex Sequences

> **Definition 3.21 (Complex convergence)**
> A complex sequence $(z_n)$ converges to $L \in \mathbb{C}$ if
> $$\forall \varepsilon > 0 \ \ \exists N \in \mathbb{N} \ \ \forall n \geq N \quad |z_n - L| < \varepsilon,$$
> i.e. $|z_n - L| \to 0$.

> **Corollary 3.22 (Uniqueness of Limits)** Complex limits are unique (same proof as 3.15).

> **Corollary 3.23** A convergent complex sequence is bounded (same proof as 3.20).

Neighbourhoods of $L \in \mathbb{C}$ are open discs $|z - L| < \varepsilon$; $z_n \to L$ iff every such disc contains a tail (Remark 3.24).

> **Theorem 3.25**
> Let $z_n = x_n + i y_n$. Then $(z_n)$ converges iff $(x_n)$ and $(y_n)$ both converge.

> [!proof]- Proof
> (⇐) Let $x_n \to x$, $y_n \to y$, $L = x + iy$, $\varepsilon > 0$. Take $N_1, N_2$ with $|x_n - x| < \varepsilon/2$ and $|y_n - y| < \varepsilon/2$. For $n \geq \max(N_1, N_2)$:
> $$|z_n - L| \leq |x_n - x| + |y_n - y| < \varepsilon.$$
> (⇒) If $z_n \to L = x + iy$, take $N$ with $|z_n - L| < \varepsilon$. Since $|\operatorname{Re} w|, |\operatorname{Im} w| \leq |w|$: $|x_n - x| \leq |z_n - L| < \varepsilon$ and likewise for $y_n$. $\square$

> [!example]- Example 3.26: $\left(\frac{1}{1+i}\right)^n \to 0$
> $|z_n| = \frac{1}{|1 + i|^n} = \left(\frac{1}{\sqrt2}\right)^n$, and $(\sqrt 2)^{-n} = 2^{-n/2} < \varepsilon$ for $n > 2/\varepsilon$. $\square$
> 
> (Remark 3.27: splitting into real and imaginary parts, $\frac{\cos(n\pi/4)}{2^{n/2}}$ and $\frac{(-1)^n \sin(n\pi/4)}{2^{n/2}}$, would just be extra work. It's often easier to treat a complex sequence as a whole.)

> **Notation 3.28 (Asymptotic notation)**
> 1. $a_n = O(b_n)$ (**big O**) if there is $c$ such that $|a_n| < c b_n$ for all $n \geq$ some $N$.
> 2. $a_n = o(b_n)$ (**little o**) if $a_n / b_n \to 0$.
> 3. $a_n \sim b_n$ (**asymptotically equal**) if $a_n / b_n \to 1$.

> [!example]- Example 3.29
> $n = O(n^2)$, $n = o(n^2)$, $\sin n = O(1)$, $\sin n = o(n)$, $(n+1)^2 = n^2 + O(n)$, $(n+1)^2 \sim n^2$.

## Infinity

> **Definition 3.30 (Real infinities)**
> $a_n \to \infty$ means $\forall M \in \mathbb{R} \ \exists N \in \mathbb{N} \ \forall n \geq N \ a_n > M$.
> $b_n \to -\infty$ means $\forall M \in \mathbb{R} \ \exists N \in \mathbb{N} \ \forall n \geq N \ b_n < M$.

> **Definition 3.31 (Complex infinity)**
> For complex $(z_n)$, $z_n \to \infty$ means $\forall M \in \mathbb{R} \ \exists N \ \forall n \geq N \ |z_n| > M$, i.e. $|z_n| \to \infty$.

**$\pm\infty$ are not real numbers and $\infty$ is not a complex number.** Never write $\lim \frac{n}{n+1} = \frac{\infty}{\infty} = 1$.

> [!note]- Remark 3.32 (Indeterminate forms)
> If $a_n, b_n \to \infty$, nothing follows about $a_n / b_n$: "$\frac\infty\infty$" is indeterminate. So are $\frac00$, $0 \times \infty$, $\infty - \infty$, $0^0$, $1^\infty$, $\infty^0$. (Not $\infty + \infty$ or $\infty \times \infty$: those do tend to $\infty$.)
> 
> | Type | $a_n$ | $b_n$ | form | long term |
> |---|---|---|---|---|
> | $\frac00$ | $\frac1n$ | $\frac1n$ | $1$ | $\to 1$ |
> | $\frac00$ | $\frac1n$ | $\frac{(-1)^n}{n}$ | $(-1)^n$ | no limit |
> | $0 \times \infty$ | $\frac1n$ | $n$ | $1$ | $\to 1$ |
> | $0 \times \infty$ | $\frac1n$ | $n^2$ | $n$ | $\to \infty$ |
> | $0 \times \infty$ | $(-2)^{-n}$ | $2^n$ | $(-1)^n$ | no limit |
> | $\infty - \infty$ | $n$ | $2n$ | $-n$ | $\to -\infty$ |
> | $\infty - \infty$ | $n$ | $n + \sin n$ | $-\sin n$ | no limit |
> | $0^0$ | $\frac1n$ | $\frac1n$ | $1/\sqrt[n]{n}$ | $\to 1$ |
> | $0^0$ | $2^{-n}$ | $\frac1n$ | $\frac12$ | $\to \frac12$ |
> | $1^\infty$ | $1 + \frac1n$ | $n$ | $(1 + \frac1n)^n$ | $\to e$ |
> | $1^\infty$ | $1 + \frac{1}{n^2}$ | $n$ | $(1 + \frac{1}{n^2})^n$ | $\to 1$ |
> | $1^\infty$ | $1 + \frac1n$ | $n^2$ | $(1 + \frac1n)^{n^2}$ | $\to \infty$ |
> | $\infty^0$ | $n$ | $\frac1n$ | $\sqrt[n]{n}$ | $\to 1$ |
> | $\infty^0$ | $2^n$ | $\frac1n$ | $2$ | $\to 2$ |

> [!note]- Remarks 3.33 – 3.34 (off-syllabus: hyperreals, neighbourhoods of infinity, Riemann sphere)
> **Hyperreals** (Hewitt 1948, Robinson 1966) formalise infinities and infinitesimals ("non-standard analysis").
> 
> A **neighbourhood of $\infty$** in $\mathbb{R}$ is $(M, \infty)$: $a_n \to \infty$ iff every such interval contains a tail. Adding $\pm\infty$ gives the extended real line $[-\infty, \infty]$.
> 
> In $\mathbb{C}$ there is one $\infty$, with neighbourhoods $\{|z| > M\}$. Adding it gives $\mathbb{C}_\infty = \mathbb{C} \cup \{\infty\}$, topologically a sphere (the **Riemann sphere**). **Stereographic projection** from the north pole $N = (0,0,1)$ of the unit sphere $S$:
> $$\pi(x, y, z) = \begin{cases} \frac{x + iy}{1 - z} & z \neq 1 \\ \infty & z = 1 \end{cases}, \qquad \pi^{-1}(X + iY) = \left(\frac{2X}{1 + X^2 + Y^2}, \frac{2Y}{1 + X^2 + Y^2}, \frac{X^2 + Y^2 - 1}{1 + X^2 + Y^2}\right).$$
> Circles through $N$ map to lines, other circles to circles; $\pi$ is conformal (angle-preserving); Möbius maps $z \mapsto \frac{az + b}{cz + d}$ ($ad \neq bc$) are the conformal bijections of the sphere.

> **Proposition 3.35**
> 1. For a sequence of **positive** reals: $a_n \to \infty \iff 1/a_n \to 0$. (Fails if the $a_n$ are merely non-zero.)
> 2. For a sequence of **non-zero complex** numbers: $a_n \to \infty \iff 1/a_n \to 0$.

> [!proof]- Proof
> (1, ⇒) Given $\varepsilon$, set $M = 1/\varepsilon$; eventually $a_n > M$, so $0 < 1/a_n < \varepsilon$.
> (1, ⇐) Given $M > 0$, set $\varepsilon = 1/M$; eventually $1/a_n < \varepsilon$, so $a_n > M$.
> Counterexample for non-zero reals: $a_n = (-1)^n n$ has $1/a_n \to 0$, but $a_{2n+1} \to -\infty$.
> (2) Same arguments with $|a_n|$. $\square$

> [!example]- Example 3.36 ($a_n \to \infty$; what about $a_n / b_n$?)
> (a) $(b_n)$ bounded, non-zero ⇒ $a_n / b_n \to \infty$? **False:** $a_n = n$, $b_n = (-1)^n$.
> (b) $(b_n)$ bounded, positive ⇒ $a_n / b_n \to \infty$? **True:** $0 < b_n < K$; given $M$, eventually $a_n > MK$, so $a_n / b_n > M$.
> (c) $b_n \neq 0$, $b_n \to L > 0$ ⇒ $a_n / b_n \to \infty$? **True:** with $\varepsilon = L/2$, eventually $L/2 < b_n < 3L/2$; apply (b) to that tail. $\square$

> [!example]- Example 3.37 (real vs complex $\infty$)
> (a) Real $a_n \to \infty$ ⇒ $a_n \to \infty$ as a complex sequence: **true** ($|a_n| \to \infty$).
> (b) The converse is **false**: $a_n = (-1)^n n$.

> [!example]- Example 3.38 (Harmonic numbers): $H_n = 1 + \frac12 + \dots + \frac1n \to \infty$
> Group terms:
> $$H_{2^k} = 1 + \tfrac12 + \left(\tfrac13 + \tfrac14\right) + \left(\tfrac15 + \dots + \tfrac18\right) + \dots > 1 + \tfrac12 + \tfrac12 + \dots + \tfrac12 = 1 + \frac k2.$$
> Given $M$, choose $k$ with $1 + k/2 \geq M$. Since $H_n$ is increasing, $H_n > M$ for all $n \geq 2^k$. $\square$

> **Proposition 3.39**
> If $p_n, q_n$ are integers with $q_n > 0$ and $p_n / q_n \to \alpha$ irrational, then $q_n \to \infty$.

> [!proof]- Proof
> Suppose not: there's a positive integer $M$ with $q_n \leq M$ for infinitely many $n$. As $\alpha$ is irrational it lies in some open interval $\left(\frac{k}{M!}, \frac{k+1}{M!}\right)$, at distance $d > 0$ from the nearer end-point. When $q_n \leq M$, $p_n / q_n$ is an integer multiple of $\frac{1}{M!}$, so $|p_n / q_n - \alpha| \geq d$ for infinitely many $n$. This contradicts $p_n / q_n \to \alpha$. $\square$
