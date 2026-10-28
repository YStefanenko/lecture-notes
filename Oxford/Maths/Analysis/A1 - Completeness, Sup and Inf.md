Analysis I, Chapter 1.3. Back to [[A1]]. Builds on [[A1 - Field and Order Axioms]].

$\mathbb{Q}$ is also an ordered field, so the field and order axioms alone don't pin down $\mathbb{R}$. Completeness is what's missing.

> **Theorem 1.49** There is no $\alpha \in \mathbb{Q}$ with $\alpha^2 = 2$.

> [!proof]- Proof
> Suppose $\alpha = m/n$ in lowest terms ($m, n$ coprime). Then $2n^2 = m^2$, so $m^2$ is even, so $m$ is even (odd × odd is odd). Write $m = 2k$: $n^2 = 2k^2$, so $n$ is even too. Contradiction with lowest terms. $\square$

## Max, Min and Bounds

> **Definition 1.50 (Minimum, maximum)**
> Let $B \subseteq \mathbb{R}$. $b_1$ is a **least element / minimum** of $B$ if $b_1 \in B$ and $b_1 \leq b$ for all $b \in B$; write $b_1 = \min B$.
> $b_2$ is a **greatest element / maximum** of $B$ if $b_2 \in B$ and $b \leq b_2$ for all $b \in B$; write $b_2 = \max B$.

> [!example]- Example 1.51
> $1 = \min[1, 2)$, but $[1, 2)$ has no maximum: if $x \in [1, 2)$ then $x < 2$, so $1 + x/2 \in [1,2)$ is bigger.

> **Proposition 1.52** A maximum (if it exists) is unique; similarly a minimum.

> [!proof]- Proof
> If $b, c$ are both maxima of $B$: $b \in B$ and $c$ is a max, so $b \leq c$; likewise $c \leq b$. By anti-symmetry $b = c$. $\square$

> **Proposition 1.53** Every non-empty subset of $\mathbb{N}$ has a minimum.

> [!proof]- Proof
> Suppose $S \subseteq \mathbb{N}$ is non-empty with no minimum. Let $S^* = \{n \in \mathbb{N} : \text{none of } 0, 1, \dots, n \text{ is in } S\}$. $0 \in S^*$ (else $0 = \min S$). If $n \in S^*$ then $n + 1 \notin S$ (else it would be $\min S$), so $n + 1 \in S^*$. By induction $S^* = \mathbb{N}$, so $S = \varnothing$. Contradiction. $\square$

> **Definition 1.54 (Bounds)**
> Let $B \subseteq \mathbb{R}$.
> - $l$ is a **lower bound** of $B$ if $l \leq b$ for all $b \in B$; then $B$ is **bounded below**.
> - $u$ is an **upper bound** of $B$ if $b \leq u$ for all $b \in B$; then $B$ is **bounded above**.
> - $B$ is **bounded** if it is bounded above and below.

> [!example]- Example 1.55
> (a) $23$ and $\pi$ are upper bounds of $[1, 2)$; $1$ and $-37$ are lower bounds. Upper bounds: $[2, \infty)$. Lower bounds: $(-\infty, 1]$.
> (b) $\mathbb{Q}$ is bounded neither above nor below; $\mathbb{N}$ is bounded below; $(-\infty, e]$ is bounded above.
> (c) $\varnothing$ is bounded: every real is both an upper and a lower bound.

> **Corollary 1.56**
> 1. A non-empty subset of $\mathbb{Z}$ that is bounded below has a minimum.
> 2. A non-empty subset of $\mathbb{Z}$ or $\mathbb{N}$ that is bounded above has a maximum.
> 3. $\mathbb{N}$ has no maximal element.

## The Completeness Axiom  and  Supremum

> **Definition 1.57 (Completeness Axiom)**
> **(C)** Let $S \subseteq \mathbb{R}$ be non-empty and bounded above. Then the set of upper bounds of $S$ has a least element (a.k.a. supremum).

> [!note]- Remark 1.58 (equivalent forms of completeness)
> Equivalent to C:
> - If $A, B$ are non-empty bounded sets with $a \leq b$ for all $a \in A$, $b \in B$, then there is $c$ with $a \leq c \leq b$ for all $a \in A$, $b \in B$ (Sheet 2, Ex 10).
> - Bounded monotone sequences converge (Theorem 5.3).
> - Cauchy completeness (Theorem 5.29) + Archimedean property.
> - Nested Intervals Theorem (Theorem 5.7) + Archimedean property.
> - Bolzano–Weierstrass (Theorem 5.20).
> - (Off-syllabus) Dedekind completeness: every Dedekind cut $A$ equals $(-\infty, z) \cap \mathbb{Q}$ for a unique real $z$.

> [!note]- Remark 1.59 (existence and uniqueness of $\mathbb{R}$)
> $\mathbb{R}$ can be constructed from $\mathbb{Q}$ (see Remark 5.34 on Cauchy sequences). Up to order isomorphism there is a unique complete ordered field (Körner pp. 359–360).

> **Definition 1.60 (Supremum)**
> The least upper bound of $S$ (from C) is its **supremum**, $\sup S$. It is unique by Prop 1.52.

> [!example]- Example 1.61: $\sup[1, 2) = 2$
> $2$ is an upper bound. If $t < 2$ were a smaller upper bound, then $t \geq 1$ and $\frac32 \leq \frac{t+2}{2} < 2$, so $\frac{t+2}{2} \in [1, 2)$ but $t < \frac{t+2}{2}$, a contradiction. $\square$

Example 1.62: the set of upper bounds of $\varnothing$ is $\mathbb{R}$, which has no minimum, so $\sup \varnothing$ doesn't exist (that's why C needs non-empty).

> **Proposition 1.63** If $S$ has a maximum then $\max S = \sup S$.

> [!proof]- Proof
> $\max S \geq x$ for all $x \in S$, so it's an upper bound. Any upper bound $u$ satisfies $u \geq \max S$ since $\max S \in S$. $\square$

> **Proposition 1.64 (The Approximation Property)**
> Let $S$ be non-empty and bounded above, and $\varepsilon > 0$. Then there exists $s \in S$ with
> $$\sup S - \varepsilon < s \leq \sup S.$$

> [!proof]- Proof
> Otherwise $\sup S - \varepsilon$ would be an upper bound smaller than the least upper bound. $\square$

> **Remark 1.65 (How to prove $M = \sup S$)**
> Show 
> 	1. $s \leq M$ for all $s \in S$, 
> and either
> 	2. $M \leq M'$ for every upper bound $M'$, or
> 	2'. for every $\varepsilon > 0$ there is $s \in S$ with $M - \varepsilon < s \leq M$.

> **Corollary 1.66**
> If $S$ is non-empty and bounded above, there is $a : \mathbb{N} \to S$ with $\sup S - \frac1n < a(n) \leq \sup S$ for all $n \geq 1$. (So a sequence in $S$ converges to $\sup S$.)

## Infimum

> **Theorem 1.67**
> Let $T$ be non-empty and bounded below. Then the set of lower bounds of $T$ has a greatest element.

> [!proof]- Proof
> Let $S = \{-t : t \in T\}$, non-empty. If $l$ is a lower bound of $T$ then $-t \leq -l$ for all $t$, so $S$ is bounded above and $\sup S$ exists. Claim $-\sup S$ is the greatest lower bound of $T$:
> (i) For $t \in T$, $-t \leq \sup S$, so $t \geq -\sup S$: it's a lower bound.
> (ii) If $l \leq t$ for all $t$, then $-l \geq -t$ for all $t$, so $-l \geq \sup S$, i.e. $l \leq -\sup S$. $\square$

> **Definition 1.68 (Infimum)**
> This greatest lower bound is the **infimum** of $T$, written $\inf T$. It is unique, and if $T$ has a minimum then $\min T = \inf T$.

Example 1.69: $\sup[1, 2) = 2$, $\inf[1, 2) = 1 = \min[1,2)$, and $\max[1, 2)$ doesn't exist.

> **Corollary 1.70 (Approximation Property for infima)**
> Let $T$ be non-empty and bounded below, and $\varepsilon > 0$. Then there exists $t \in T$ with
> $$\inf T \leq t < \inf T + \varepsilon.$$

> **Corollary 1.71**
> There is $a : \mathbb{N} \to T$ with $\inf T \leq a(n) < \inf T + \frac1n$ for all $n$.

> [!example]- Example 1.72: $\sup(cS) = c \inf S$ for $c < 0$
> Let $S$ be bounded, $c < 0$, $cS = \{cs : s \in S\}$.
> (i) $s \geq \inf S$ for all $s$, and $c < 0$, so $cs \leq c \inf S$: $c \inf S$ is an upper bound of $cS$.
> (ii) If $u$ is an upper bound of $cS$, then $cs \leq u$, so $s \geq u/c$ for all $s$. So $u/c$ is a lower bound of $S$, hence $\inf S \geq u/c$ and $c \inf S \leq u$.
> (ii)' Alternatively: for $\varepsilon > 0$ pick $s$ with $\inf S \leq s < \inf S - \varepsilon/c$; then $c\inf S - \varepsilon < cs \leq c \inf S$. $\square$

## Square Roots and the Archimedean Property

> **Theorem 1.73 ($\sqrt 2$ exists)**
> There exists a unique positive $\alpha$ with $\alpha^2 = 2$.

> [!proof]- Proof
> Let $S = \{x \in \mathbb{R} : x^2 < 2\}$. $1 \in S$, and if $x > 2$ then $x^2 > 2x > 4 > 2$, so $2$ is an upper bound. Let $\alpha = \sup S \geq 1 > 0$. Rule out $\alpha^2 < 2$ and $\alpha^2 > 2$:
> - **$\alpha^2 < 2$:** for $0 < h < 1$ (so $h^2 < h$), $(\alpha + h)^2 < \alpha^2 + (2\alpha + 1)h$. Choosing $0 < h < \min\left(1, \frac{2 - \alpha^2}{2\alpha + 1}\right)$ gives $(\alpha + h)^2 < 2$, so $\alpha + h \in S$, contradicting $\alpha = \sup S$.
> - **$\alpha^2 > 2$:** $(\alpha - h)^2 > \alpha^2 - 2h\alpha$, so for $0 < h < \frac{\alpha^2 - 2}{2\alpha}$, $(\alpha - h)^2 > 2$. As $x^2$ is increasing for $x > 0$, no element of $S$ lies in $(\alpha - h, \alpha)$, contradicting the approximation property.
> 
> By trichotomy $\alpha^2 = 2$. Uniqueness: if $\beta > 0$ and $\beta^2 = 2$, then $(\alpha + \beta)(\alpha - \beta) = 0$, so $\beta = \pm\alpha$; only $\alpha$ is positive. $\square$

So $\mathbb{Q}$ isn't complete: $\{x \in \mathbb{Q} : x^2 < 2\}$ has no supremum in $\mathbb{Q}$ (Remark 1.74). Notation 1.75: write $\sqrt 2$ for $\alpha$.

> **Theorem 1.76**
> For any $a > 0$ there is a unique real $\sqrt a > 0$ with $(\sqrt a)^2 = a$. *(Same argument; see also Example 5.9.)*

> **Theorem 1.77 (Archimedean Property)**
> $\mathbb{N}$ is not bounded above in $\mathbb{R}$: for any $x \in \mathbb{R}$ there is $n \in \mathbb{N}$ with $x < n$.

> [!proof]- Proof
> Otherwise let $\alpha = \sup \mathbb{N}$. By approximation $\alpha - 1 < k$ for some $k \in \mathbb{N}$. Then $k + 1 \in \mathbb{N}$ and $\alpha < k + 1$, contradiction. $\square$

> **Corollary 1.78** For any $\varepsilon > 0$ there is $n \in \mathbb{N}$ with $0 < \frac1n < \varepsilon$.

> [!proof]- Proof
> Apply the Archimedean property to $1/\varepsilon$. $\square$

> **Corollary 1.79 (Density)**
> If $a < b$ there are a rational $q$ and an irrational $r$ with $a < q < b$ and $a < r < b$. *(Sheet 2, Ex 5.)*
