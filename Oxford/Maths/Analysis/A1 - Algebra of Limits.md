Analysis I, Chapter 4. Back to [[A1]]. Builds on [[A1 - Sequences and Convergence]].

Limits respect inequalities and algebraic operations, so complicated sequences don't need first-principles $\varepsilon$–$N$ proofs.

## Limits and Inequalities

> **Theorem 4.1 (Limits respect weak inequalities)**
> If $a_n \to L$, $b_n \to M$ and $a_n \leq b_n$ for all $n$, then $L \leq M$.

> [!proof]- Proof
> Suppose $L > M$; set $\varepsilon = (L - M)/2 > 0$. Take $N_1$ with $|a_n - L| < \varepsilon$ and $N_2$ with $|b_n - M| < \varepsilon$. Then for $n \geq \max(N_1, N_2)$:
> $$a_n > L - \varepsilon = \frac{L + M}{2} = M + \varepsilon > b_n,$$
> contradicting $a_n \leq b_n$. $\square$
> 
> *Idea:* the neighbourhoods $(M - \varepsilon, M + \varepsilon)$ and $(L - \varepsilon, L + \varepsilon)$ are disjoint, with $L$'s to the right.

**Remark 4.2** Limits do **not** respect strict inequalities: $\frac1n > 0$ for all $n$, but $\lim \frac1n = 0 = \lim 0$.

> **Theorem 4.3 (Sandwich Rule / Squeeze Theorem)**
> If $x_n \leq a_n \leq y_n$ for all $n$ and $\lim x_n = \lim y_n = L$, then $a_n \to L$.

> [!proof]- Proof
> Let $\varepsilon > 0$. There are $N_1, N_2$ with $x_n - L > -\varepsilon$ for $n \geq N_1$ and $y_n - L < \varepsilon$ for $n \geq N_2$. For $n \geq \max(N_1, N_2)$:
> $$-\varepsilon < x_n - L \leq a_n - L \leq y_n - L < \varepsilon. \quad \square$$

> [!example]- Example 4.4: $\frac{2n + \cos(n^2)}{3n^2 - \sin(n^3)}$ converges
> For $n \geq 1$:
> $$\frac{1}{3n} = \frac{n}{3n^2} \leq \frac{2n - 1}{3n^2 + 1} \leq a_n \leq \frac{2n + 1}{3n^2 - 1} \leq \frac{3n}{2n^2} = \frac{3}{2n}.$$
> Both bounds tend to 0, so $a_n \to 0$ by sandwiching. $\square$

## The Algebra of Limits (AOL)

Throughout, $(a_n), (b_n)$ are real or complex sequences.

> **Proposition 4.5 (AOL: Constants)** If $a_n = a$ for all $n$, then $a_n \to a$.

> [!proof]- Proof
> Take $N = 1$: $|a_n - a| = 0 < \varepsilon$. $\square$

> **Proposition 4.6 (AOL: Sums)** If $a_n \to a$ and $b_n \to b$ then $a_n + b_n \to a + b$.

> [!proof]- Proof
> Let $\varepsilon > 0$. Take $N_1, N_2$ with $|a_n - a| < \varepsilon/2$ and $|b_n - b| < \varepsilon/2$. For $n \geq \max(N_1, N_2)$:
> $$|(a_n + b_n) - (a + b)| \leq |a_n - a| + |b_n - b| < \varepsilon/2 + \varepsilon/2 = \varepsilon. \quad \square$$
> 
> *Two standard techniques:* intersect the tails, and aim for $\varepsilon/2$ in each part so the total is $\varepsilon$.

> **Proposition 4.7 (AOL: Scalar Products)** If $a_n \to a$ and $\lambda \in \mathbb{R}$ (or $\mathbb{C}$) then $\lambda a_n \to \lambda a$.

> [!proof]- Proof
> Take $N$ with $|a_n - a| < \frac{\varepsilon}{|\lambda| + 1}$ for $n \geq N$. Then $|\lambda a_n - \lambda a| = |\lambda||a_n - a| \leq \frac{|\lambda|\varepsilon}{|\lambda| + 1} < \varepsilon$. (Using $|\lambda| + 1$ avoids dividing by zero.) $\square$

> **Corollary 4.8 (AOL: Differences)** If $a_n \to a$ and $b_n \to b$ then $a_n - b_n \to a - b$.

> **Corollary 4.9 (AOL: Translations)** If $a_n \to a$ and $c$ is a constant then $a_n + c \to a + c$.

> **Lemma 4.10** If $x_n \to 0$ and $y_n \to 0$ then $x_n y_n \to 0$.

> [!proof]- Proof
> Let $0 < \varepsilon < 1$ (WLOG, Remark 3.11). Eventually $|x_n| < \varepsilon$ and $|y_n| < \varepsilon$, so $|x_n y_n| < \varepsilon^2 < \varepsilon$. $\square$

> **Proposition 4.11 (AOL: Products)** If $a_n \to a$ and $b_n \to b$ then $a_n b_n \to ab$.

> [!proof]- Proof
> $$a_n b_n - ab = (a_n - a)(b_n - b) + b(a_n - a) + a(b_n - b).$$
> The first term $\to 0$ by Lemma 4.10, the others by Prop 4.7; add by Prop 4.6. $\square$

> **Proposition 4.12 (AOL: Reciprocals)** If $a_n \to a \neq 0$ and $a_n \neq 0$ for all $n$, then $1/a_n \to 1/a$.

> [!proof]- Proof
> We need $\left|\frac{1}{a_n} - \frac1a\right| = \frac{|a_n - a|}{|a_n||a|}$ small; the danger is $|a_n|$ being small, so stay in a tail near $a$.
> 
> Let $\varepsilon > 0$. Take $N_1$ with $|a_n - a| < |a|/2$ for $n \geq N_1$. Then $|a| \leq |a_n| + |a - a_n|$ gives $|a_n| > |a|/2$, so $1/|a_n| < 2/|a|$. Take $N_2$ with $|a_n - a| < |a|^2 \varepsilon / 2$. For $n \geq \max(N_1, N_2)$:
> $$\left|\frac{1}{a_n} - \frac1a\right| = \frac{|a_n - a|}{|a_n||a|} < \frac{|a|^2 \varepsilon}{2} \cdot \frac{2}{|a|} \cdot \frac{1}{|a|} = \varepsilon. \quad \square$$

> **Corollary 4.13 (AOL: Quotients)** If $a_n \to a$, $b_n \to b$, $b_n \neq 0$ for all $n$ and $b \neq 0$, then $a_n / b_n \to a/b$. *(From 4.11 and 4.12.)*

> **Proposition 4.14 (AOL: Modulus)** If $a_n \to a$ then $|a_n| \to |a|$.

> [!proof]- Proof
> By the reverse triangle inequality $0 \leq \big||a_n| - |a|\big| \leq |a_n - a| \to 0$; sandwich. $\square$

> [!example]- Example 4.15: $\frac{n^2 + n + 1}{3n^2 + 4} \to \frac13$ by AOL
> $$\frac{n^2 + n + 1}{3n^2 + 4} = \frac{1 + \frac1n + \frac{1}{n^2}}{3 + 4\frac{1}{n^2}} \to \frac{1 + 0 + 0}{3 + 0} = \frac13,$$
> using: $\frac1n \to 0$ (Archimedean), $\frac{1}{n^2} \to 0$ (4.11), constants (4.5), sums (4.6), quotient (4.13), product (4.11). Compare the first-principles proof in Example 3.17. $\square$

> [!example]- Example 4.16 & Proposition 4.17: Fibonacci ratios converge to the golden ratio
> $F_1 = F_2 = 1$, $F_{n+2} = F_{n+1} + F_n$. **Claim:** $F_{n+1}/F_n$ converges.
> 
> Let $x_n = F_{n+1}/F_n$. By induction $F_n \geq 1$, and $\frac{F_{n+2}}{F_{n+1}} = 1 + \frac{F_n}{F_{n+1}}$, so $x_{n+1} = 1 + 1/x_n$ with $x_n \geq 1$.
> 
> *If* $x_n \to L$, then $L \geq 1$ and by AOL $L = 1 + \frac1L$, so $L^2 - L - 1 = 0$ and $L = \frac{1 + \sqrt5}{2} = \varphi$ (the **golden ratio**).
> 
> *Proof it converges:* since $\varphi^2 = \varphi + 1$,
> $$x_{n+1} - \varphi = \frac{1}{x_n} - \frac1\varphi = -\frac{x_n - \varphi}{x_n \varphi}, \quad \text{so} \quad \left|\frac{x_{n+1} - \varphi}{x_n - \varphi}\right| = \frac{1}{\varphi x_n} \leq \frac1\varphi.$$
> By induction $-\varphi^{-n} \leq x_n - \varphi \leq \varphi^{-n}$, and $\varphi^{-n} \to 0$ as $\varphi > 1$. Sandwich. $\square$

> [!example]- Example 4.18 (true or false? $(a_n)$ non-zero)
> (a) $(a_n)$ converges ⇒ $a_{n+1} - a_n \to 0$. **True** (AOL: $L - L = 0$).
> (b) $a_{n+1} - a_n \to 0$ ⇒ $(a_n)$ converges. **False:** $a_n = H_n$ (harmonic numbers).
> (c) $(a_n)$ converges ⇒ $a_{n+1}/a_n \to 1$. **False:** $a_n = (-1)^n/n$, ratio $\to -1$.
> (d) $a_n \to L \neq 0$ ⇒ $a_{n+1}/a_n \to 1$. **True** (AOL).
> (e) $a_{n+1}/a_n \to 1$ ⇒ $(a_n)$ converges. **False:** $a_n = n$.
> (f) $a_{n+1}/a_n \to 1$ and $(a_n)$ bounded ⇒ converges. **False:** $a_n = e^{iH_n}$; ratio $e^{i/(n+1)} \to 1$ but $H_n \to \infty$. (Justifying this needs continuity, from Analysis II: if $a_n \to L$ and $f$ is continuous then $f(a_n) \to f(L)$, Remark 4.19.)

## AOL with Infinity

$\infty - \infty$, $\frac\infty\infty$, $0 \times \infty$ are indeterminate, but some results hold:

> **Proposition 4.20 (AOL: Infinity)** For real sequences:
> 1. $a_n \to \infty$, $b_n \to \infty$ ⇒ $a_n + b_n \to \infty$.
> 2. $a_n \to \infty$, $b_n \to \infty$ ⇒ $a_n b_n \to \infty$.
> 3. $a_n \to \infty$, $b_n \to -\infty$ ⇒ $a_n b_n \to -\infty$.
> 4. $a_n \to \infty$, $(b_n)$ bounded ⇒ $a_n + b_n \to \infty$.
> 5. $a_n \to \infty$, $(b_n)$ bounded ⇒ $b_n / a_n \to 0$.
> 6. $a_n \to \infty$, $b_n \to L > 0$ ⇒ $a_n b_n \to \infty$.
> 
> *(Exercises.)*

> **Proposition 4.21 (AOL: Asymptotics)** For real sequences:
> 1. $a_n = O(\alpha_n)$, $b_n = O(\beta_n)$ ⇒ $a_n b_n = O(\alpha_n \beta_n)$.
> 2. $a_n = O(\alpha_n)$, $b_n = O(\beta_n)$ ⇒ $a_n + b_n = O(\max(|\alpha_n|, |\beta_n|))$.
> 3. $a_n \sim \alpha_n$, $b_n \sim \beta_n$ ⇒ $a_n b_n \sim \alpha_n \beta_n$.
> 4. $a_n \sim \alpha_n$, $b_n \sim \beta_n$ ⇒ $a_n / b_n \sim \alpha_n / \beta_n$.
> 
> *(Exercises.)*

**Remark 4.22 (Relative orders of terms)** In the long run:
$$\text{bounded trig and constants} < \text{logarithms} < \text{polynomials} < \text{exponentials}.$$
- $|\cos n|, |\sin n| \leq 1$.
- For rational $q > 0$, $\frac{\log n}{n^q} \to 0$ (put $n = e^t$: $\frac{t}{(e^q)^t} \to 0$).
- For $a > 1$ and polynomial $p$, $\frac{p(n)}{a^n} \to 0$ (Cor 3.19).

> [!example]- Example 4.23 (spotting the dominant term)
> - $(-1)^n \frac{n^6 + 7n^2}{2^n} \to 0$, oscillating: $2^n$ dominates.
> - $\frac{2n + 3}{3n + 8}\cos n$ diverges: the fraction $\to \frac23$, and $\cos n$ oscillates.
> - $\frac{\log n}{\sqrt n}\cos\left(\frac{2^n - n}{n^2 + 3n - 6}\right) \to 0$: $|\cos| \leq 1$ makes the messy argument irrelevant, and $\sqrt n$ dominates $\log n$.
> 
> Exercise: turn these first thoughts into rigorous proofs with AOL and sandwiching.
