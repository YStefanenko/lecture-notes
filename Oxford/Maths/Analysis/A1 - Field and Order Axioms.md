Analysis I, Chapter 1.1–1.2. Back to [[A1]].

## The Real Number Axioms

> **Definition 1.1 (Real numbers)**
> The **real numbers** are a set $\mathbb{R}$ with two binary operations, **addition** $+ : \mathbb{R}^2 \to \mathbb{R}$ and **multiplication** $\times : \mathbb{R}^2 \to \mathbb{R}$, satisfying
> - the **field axioms** A1–A4, M1–M4, D, Z,
> - the **order axioms** P1–P3,
> - the **completeness axiom** C (see [[A1 - Completeness, Sup and Inf]]).

## Field Axioms

> **Addition axioms** (for all $a, b, c$)
> - **A1** $a + b = b + a$ (commutative)
> - **A2** $a + (b + c) = (a + b) + c$ (associative)
> - **A3** there is an additive identity $0$ with $a + 0 = a$
> - **A4** each $a$ has an additive inverse $-a$ with $a + (-a) = 0$

A1–A4 say $(\mathbb{R}, +)$ is an abelian group (Remark 1.2).

> [!note]- Remark 1.3 (associativity and bracketings)
> Associativity means a sum $a_1 + \dots + a_k$ doesn't depend on how it is bracketed. Four terms can be bracketed in five ways; in general $n$ terms can be bracketed in $C_n = \frac{1}{n+1}\binom{2n}{n}$ ways (the Catalan numbers), and strong induction shows they all agree.

> **Proposition 1.4**
> If $a + x = a$ for all $a$, then $x = 0$. So the additive identity is unique.

> [!proof]- Proof
> Take $a = 0$: $x = x + 0 = 0 + x = 0$ (A3, A1, hypothesis). $\square$

> **Proposition 1.5**
> If $a + x = a + y$ for some $a$, then $x = y$. So additive inverses are unique.

> [!proof]- Proof
> $$\begin{aligned} y &= y + 0 = y + (a + (-a)) = (y + a) + (-a) = (a + y) + (-a) \\ &= (a + x) + (-a) = (x + a) + (-a) = x + (a + (-a)) = x + 0 = x \end{aligned}$$
> using A3, A4, A2, A1, the hypothesis, A1, A2, A4, A3.
> 
> *Alternative ("subtract $a$ from both sides"):* add $-a$ to both sides of $a + x = a + y$, use A1 and A2 to get $x + (a + (-a)) = y + (a + (-a))$, then A4 and A3 give $x = y$.
> 
> Uniqueness of inverses: if $a + x = 0 = a + (-a)$ then $x = -a$. $\square$

> **Proposition 1.6** $-(-a) = a$.

> [!proof]- Proof
> $(-a) + a = a + (-a) = 0$ and $(-a) + (-(-a)) = 0$, so by uniqueness of additive inverses $-(-a) = a$. $\square$

> **Proposition 1.7** $-(a + b) = (-a) + (-b)$. *(Sheet 1, Ex 1(iii).)*

> **Proposition 1.8** $-0 = 0$.

> [!proof]- Proof
> $0 + (-0) = 0$ and $0 + 0 = 0$; by uniqueness of inverses $-0 = 0$. $\square$

> **Multiplication axioms** (for all $a, b, c$)
> - **M1** $a \times b = b \times a$ (commutative)
> - **M2** $a \times (b \times c) = (a \times b) \times c$ (associative)
> - **M3** there is a multiplicative identity $1$ with $a \times 1 = a$
> - **M4** each $a \neq 0$ has a multiplicative inverse $a^{-1}$ with $a \times a^{-1} = 1$

M1–M4 say $(\mathbb{R} \setminus \{0\}, \times)$ is an abelian group (Remark 1.9).

> **Propositions 1.10 – 1.13** *(proofs as for addition; exercises)*
> - **1.10** If $a \times x = a$ for all $a$ then $x = 1$ (the identity is unique).
> - **1.11** If $a \neq 0$ and $a x = a y$ then $x = y$ (inverses are unique).
> - **1.12** If $a \neq 0$ then $(a^{-1})^{-1} = a$.
> - **1.13** If $a \neq 0 \neq b$ then $(ab)^{-1} = a^{-1} b^{-1}$.

> **Remaining field axioms**
> - **D** $a \times (b + c) = (a \times b) + (a \times c)$ (distributive law)
> - **Z** $0 \neq 1$

Why Z? If $1 = 0$ then $x = x \times 1 = x \times 0 = 0$ for all $x$, so $\{0\}$ would satisfy every other field axiom. Deriving $0 = 1$ is also a handy contradiction.

> **Proposition 1.14** $(a + b) \times c = a \times c + b \times c$.

> [!proof]- Proof
> $(a + b)c = c(a + b) = ca + cb = ac + bc$ by M1, D, M1. $\square$

> **Proposition 1.15** $a \times 0 = 0$.

> [!proof]- Proof
> $a \times 0 + 0 = a \times 0 = a \times (0 + 0) = a \times 0 + a \times 0$ (A3, A3, D). By Prop 1.5, $a \times 0 = 0$. $\square$

> **Proposition 1.16**
> If $a \times b = 0$ then $a = 0$ or $b = 0$ (or both).

> [!proof]- Proof
> If $a \neq 0$:
> $$0 = a^{-1} \times 0 = a^{-1}(ab) = (a^{-1}a)b = 1 \times b = b \times 1 = b,$$
> by Prop 1.15, hypothesis, M2, M4, M1, M3. So either $a = 0$ or $b = 0$. $\square$

> **Proposition 1.17** $(-b) \times a = -(b \times a)$. In particular $(-1) \times a = -a$.

> [!proof]- Proof
> $(b \times a) + ((-b) \times a) = (b + (-b)) \times a = 0 \times a = 0$ (Prop 1.14, A4, Prop 1.15 + M1). Also $(b \times a) + (-(b \times a)) = 0$. By uniqueness of additive inverses, $(-b) \times a = -(b \times a)$. Put $b = 1$ for the last part. $\square$

> **Proposition 1.18** $(-1) \times (-1) = 1$.

> [!proof]- Proof
> $(-1)(-1) = -(-1) = 1$ by Prop 1.17 then Prop 1.6. $\square$

> **Notation 1.19**
> Write $ab$ for $a \times b$, $a - b$ for $a + (-b)$, $a/b$ for $a \times b^{-1}$. Integer powers for $a \neq 0$:
> $$a^0 = 1, \qquad a^{k+1} = a^k \times a \ (k \geq 0), \qquad a^{-l} = (a^l)^{-1} \ (l \geq 1).$$

Only integer powers so far. Rational powers come after Theorem 1.73; $a^x = e^{x \log a}$ for real $x$ only in [[A1 - Elementary Functions]] (Remark 1.20).

> [!note]- Remark 1.21 (fields)
> Any system satisfying A1–A4, M1–M4, D, Z is a **field** (Dedekind, 1871). $\mathbb{Q}$, $\mathbb{R}$, $\mathbb{C}$, $\mathbb{Z}_p$ ($p$ prime) are fields. $\mathbb{Z}$ is not (fails M4); $\mathbb{N}$ also fails A4.

## Order Axioms

> **Definition 1.22 (Order Axioms)**
> There is a subset $\mathbb{P} \subseteq \mathbb{R}$ of **positive** numbers such that:
> - **P1** if $a, b$ are positive then $a + b$ is positive;
> - **P2** if $a, b$ are positive then $ab$ is positive;
> - **P3** (**trichotomy**) for any $a$, exactly one of: $a$ is positive, $a = 0$, $-a$ is positive.

So $\mathbb{P} = (0, \infty)$, and by P3, $0$ is not positive.
A structure satisfying the field and order axioms is an **ordered field** (Remark 1.23): $\mathbb{Q}$ and $\mathbb{R}$ are, $\mathbb{C}$ can't be made one (Prop 1.80).

> **Proposition 1.24** $1$ is positive.

> [!proof]- Proof
> By P3 exactly one of $1 \in \mathbb{P}$, $1 = 0$, $-1 \in \mathbb{P}$. Z rules out $1 = 0$. If $-1 \in \mathbb{P}$, then by P2 $(-1)(-1) = 1 \in \mathbb{P}$ (Prop 1.18), so both $\pm 1 \in \mathbb{P}$, contradicting P3. Hence $1 \in \mathbb{P}$. $\square$

> **Notation 1.25**
> $a > b$ means $a - b \in \mathbb{P}$; $a < b$ means $b - a \in \mathbb{P}$; $a \geq b$ means $a - b \in \mathbb{P} \cup \{0\}$; $a \leq b$ means $b - a \in \mathbb{P} \cup \{0\}$.
> **Non-negative**: $[0, \infty)$. **Non-positive**: $(-\infty, 0]$. **Negative**: $(-\infty, 0)$.

P3 now reads: exactly one of $a > 0$, $a = 0$, $a < 0$.

> **Proposition 1.26** $a > b \iff -a < -b$. In particular $x > 0 \iff -x < 0$.

> [!proof]- Proof
> $a > b \iff a - b \in \mathbb{P} \iff -(-a) - b \in \mathbb{P} \iff -b - (-a) \in \mathbb{P} \iff -b > -a$ (definition, Prop 1.6, A1, definition). Last part: $-0 = 0$. $\square$

> **Proposition 1.27** ($\leq$ is a total order) For all $a, b, c$:
> 1. $a \leq a$ (reflexive)
> 2. $a \leq b$ and $b \leq a \implies a = b$ (anti-symmetric)
> 3. $a \leq b$ and $b \leq c \implies a \leq c$ (transitive)
> 4. either $a \leq b$ or $b \leq a$ (total)

> [!proof]- Proof
> 1. $a - a = 0 \in \mathbb{P} \cup \{0\}$.
> 2. $b - a$ and $a - b = -(b - a)$ are both in $\mathbb{P} \cup \{0\}$. Both in $\mathbb{P}$ contradicts P3, so one is $0$ and $a = b$.
> 3. Trivial if $a = b$ or $b = c$. Otherwise $c - a = (c - b) + (b - a) \in \mathbb{P}$ by P1.
> 4. Exactly one of $b - a \in \mathbb{P}$ (so $a \leq b$), $b - a = 0$ (both), $a - b \in \mathbb{P}$ (so $b \leq a$). $\square$

> **Proposition 1.28** If $a \leq b$ then $a + c \leq b + c$.

> [!proof]- Proof
> $(b + c) - (a + c) = b - a \in \mathbb{P} \cup \{0\}$. $\square$

> **Proposition 1.29** If $a \leq b$ and $0 \leq c$ then $ca \leq cb$.

> [!proof]- Proof
> Immediate if $c = 0$ or $a = b$. Otherwise $b - a, c \in \mathbb{P}$, so by P2 $c(b - a) = cb - ca \in \mathbb{P}$ (using D and Prop 1.17). $\square$

> **Corollary 1.30** If $a \leq b$ and $c \leq 0$ then $ca \geq cb$. *(Sheet 1, Ex 1(v).)*

> **Corollary 1.31** $a^2 \geq 0$ for any real $a$.

> [!proof]- Proof
> If $a > 0$, $a^2 \in \mathbb{P}$ by P2. If $a < 0$, $a^2 \geq a \cdot 0 = 0$ by Cor 1.30 and Prop 1.15. If $a = 0$, $a^2 = 0$. $\square$

> **Proposition 1.32** If $a > 0$ then $a^{-1} > 0$.

> [!proof]- Proof
> $a^{-1} \neq 0$. If $a^{-1} < 0$ then $-a^{-1} > 0$, so $-1 = (-a^{-1})a > 0$ by P2, a contradiction. $\square$

> **Corollary 1.33** If $0 < a < b$ then $b^{-1} < a^{-1}$.

> [!proof]- Proof
> $a^{-1} - b^{-1} = a^{-1} b^{-1}(b - a) > 0$ by Prop 1.32 and P2. $\square$

## Max, Min and Modulus

> **Definition 1.34 (max, min)**
> $$\max(x, y) = \begin{cases} x & x \geq y \\ y & y > x \end{cases} \qquad \min(x, y) = \begin{cases} y & x \geq y \\ x & y > x \end{cases}$$
> Extended recursively: $\max(a_1, \dots, a_{n+1}) = \max(\max(a_1, \dots, a_n), a_{n+1})$.

> [!example]- Example 1.35: $\max(x, y) = -\min(-x, -y)$
> By cases using Prop 1.26 ($x < y \Rightarrow -x > -y$):
> - $x > y$: $\max = x$; $-x < -y$ so $-\min(-x,-y) = -(-x) = x$.
> - $x = y$: both give $x$.
> - $x < y$: $\max = y$; $-y < -x$ so $-\min = -(-y) = y$. $\square$

> **Definition 1.36 (Modulus)**
> $$|x| = \begin{cases} x & x \geq 0 \\ -x & x < 0 \end{cases}$$
> Also called the absolute value.

Proofs about max, min and $|\cdot|$ usually go case by case (Remark 1.37).

> **Proposition 1.38** For any $x$:
> 1. $0 \leq |x|$
> 2. $x \leq |x|$
> 3. $|-x| = |x|$
> 4. $|x|^2 = x^2$

> [!proof]- Proof
> 1. Obvious for $x \geq 0$; if $x < 0$ then $|x| = -x > 0$.
> 2. If $x \geq 0$, $x = |x|$; if $x < 0$, $x < 0 \leq |x|$.
> 3. If $x \geq 0$ then $-x \leq 0$, so $|-x| = -(-x) = x = |x|$. If $x < 0$ then $-x > 0$, so $|-x| = -x = |x|$.
> 4. $|x|^2 = x^2$ or $(-x)^2 = x^2$ (Prop 1.17). $\square$

> **Proposition 1.39 (Modulus of a product)** $|ab| = |a||b|$.

> [!proof]- Proof
> Trivial if $a = 0$ or $b = 0$, or $a, b > 0$. If $a > 0 > b$: $ab < 0$ and $|ab| = -(ab) = a(-b) = |a||b|$. If $a, b < 0$: $ab > 0$ and $|ab| = ab = (-a)(-b) = |a||b|$. (Prop 1.17.) $\square$

> **Definition 1.40 (Monotone functions)**
> For $S \subseteq \mathbb{R}$ and $f : S \to \mathbb{R}$, $f$ is
> - **increasing** if $x \leq y \Rightarrow f(x) \leq f(y)$;
> - **decreasing** if $x \leq y \Rightarrow f(x) \geq f(y)$;
> - **strictly increasing** if $x < y \Rightarrow f(x) < f(y)$;
> - **strictly decreasing** if $x < y \Rightarrow f(x) > f(y)$.

> **Proposition 1.41** $f(x) = x^2$ is strictly increasing on $[0, \infty)$.

> [!proof]- Proof
> For $0 \leq a < b$: $f(b) - f(a) = (b - a)(b + a)$, a product of two positives. $\square$

> **Theorem 1.42 (Triangle Inequality)**
> For any real $a, b$,
> $$|a + b| \leq |a| + |b|,$$
> with equality iff ($a \geq 0$ and $b \geq 0$) or ($a \leq 0$ and $b \leq 0$).

> [!proof]- Proof
> $$|a + b|^2 = (a + b)^2 = |a|^2 + 2ab + |b|^2 \leq |a|^2 + 2|ab| + |b|^2 = (|a| + |b|)^2$$
> (Prop 1.38(d), 1.38(b), 1.39). As $x^2$ is strictly increasing on $[0, \infty)$, $|a| + |b| < |a + b|$ is impossible. Equality cases: Sheet 1, Ex 3(i). $\square$

> **Corollary 1.43 (Reverse triangle inequality)**
> $$|a - b| \geq \big||a| - |b|\big|.$$

> [!proof]- Proof
> Triangle inequality: $|a - b| + |b| \geq |a|$ and $|b - a| + |a| \geq |b|$, so $|a - b| \geq |a| - |b|$ and $|a - b| \geq |b| - |a|$. One of these is $\big||a| - |b|\big|$. $\square$

> **Definition 1.44 (Distance)**
> $d(x, y) = |x - y|$. It is a **metric**:
> - **M1** $d(x, y) \geq 0$, with equality iff $x = y$;
> - **M2** $d(x, y) = d(y, x)$;
> - **M3** $d(x, z) \leq d(x, y) + d(y, z)$ (equivalent to the triangle inequality).

## Two Useful Inequalities

> **Theorem 1.45 (Bernoulli's inequality)**
> Let $x > -1$ and $n$ a positive integer. Then
> $$(1 + x)^n \geq 1 + nx.$$

> [!proof]- Proof (induction)
> $n = 1$ is immediate. Suppose $(1 + x)^N \geq 1 + Nx$ for all $x > -1$. Since $1 + x > 0$ and $Nx^2 \geq 0$:
> $$(1 + x)^{N+1} = (1 + x)(1 + x)^N \geq (1 + x)(1 + Nx) = 1 + (N+1)x + Nx^2 \geq 1 + (N+1)x$$
> (hypothesis + Prop 1.29, then Prop 1.28). $\square$

> **Proposition 1.46 (Powers dominate polynomials)**
> Let $a > 1$ and $k$ a positive integer. Then there exists $c > 0$ such that
> $$a^n \geq c n^k \quad \text{for } n = 1, 2, 3, \dots$$

> [!proof]- Proof
> Write $a = 1 + b$, $b > 0$, and take $n > k$. Then $n \geq k + 1$ gives $\frac{n-k}{n} = 1 - \frac kn \geq 1 - \frac{k}{k+1} = \frac{1}{k+1}$. By the binomial theorem (all terms positive):
> $$a^n \geq \binom nk b^k = \frac{n(n-1)\cdots(n-k+1)}{k!}b^k > \frac{(n-k)^k}{k!}b^k = \frac{b^k}{k!}\left(\frac{n-k}{n}\right)^k n^k \geq \frac{b^k}{k!(k+1)^k} n^k.$$
> So $a^n / n^k \geq \frac{b^k}{k!(k+1)^k}$ for $n > k$. Taking
> $$c = \min\left\{a, \frac{a^2}{2^k}, \dots, \frac{a^k}{k^k}, \frac{b^k}{k!(k+1)^k}\right\} > 0$$
> covers $n \leq k$ too. Note $c$ depends only on $a$ and $k$, not $n$. $\square$

Later, using $e^x$: $a^x = e^{x \log a} > \frac{(\log a)^{k+1}}{(k+1)!} x^{k+1}$ gives a slicker proof for all real $x > 0$ (Remark 1.47).

> [!example]- Example 1.48 (comparing growth)
> For (a) $x(n) = \frac{3^n + n^3}{2^n}$, $y(n) = n^4 + 3n^2$ and (b) $x(n) = \frac{2^n + n^5}{n^2}$, $y(n) = \frac{(-3)^n}{n^3 + 1}$, decide whether (i) $\exists c > 0$ with $x(n) \geq c\,y(n)$ for all $n$, (ii) $\exists c > 0$ with $x(n) \leq c\,y(n)$ for all $n$, or (iii) neither.
> 
> *Idea:* see which terms dominate; e.g. in (a) the $n^3$ is irrelevant next to $3^n$. You only need *some* $c$, not the best one.
> 
> **(a)** By Prop 1.46 there are $c_1, c_2 > 0$ with $(3/2)^n \geq c_1 n^4$ and $(3/2)^n \geq c_2 n^2$. So
> $$\frac{3^n + n^3}{2^n} \geq \left(\tfrac32\right)^n = \tfrac12\left(\tfrac32\right)^n + \tfrac12\left(\tfrac32\right)^n \geq \frac{c_1}{2}n^4 + \frac{c_2}{6}(3n^2) \geq \min\left(\frac{c_1}{2}, \frac{c_2}{6}\right)(n^4 + 3n^2).$$
> So (i) holds with $c = \min(c_1/2, c_2/6)$.
> 
> **(b)** (ii) fails: $x(n) > 0$ but $y(n) < 0$ for odd $n$. For (i) we'd need, for even $n$,
> $$(n^3 + 1)\left(\tfrac23\right)^n + \frac{n^8 + n^5}{3^n} \geq c n^2.$$
> By Prop 1.46 the LHS is bounded (by $\frac{1}{c_1} + 1 + \frac{1}{c_2} + \frac{1}{c_3}$) while the RHS is unbounded, so $\frac1c(\dots) \geq n^2 \geq n$ would bound $\mathbb{N}$, which is impossible (Cor 1.56). So (iii) neither. $\square$
