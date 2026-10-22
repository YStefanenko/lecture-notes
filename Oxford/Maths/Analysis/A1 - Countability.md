Analysis I, Chapter 2. Back to [[A1]]. Related: cardinality in [[IUM - Sets]] and [[IUM - Functions]].

> **Definition 2.1 (Equinumerous)**
> Sets $A$ and $B$ are **equinumerous**, $A \approx B$, if there is a bijection $f : A \to B$.

$\approx$ is reflexive, symmetric and transitive (identity is a bijection, bijections invert, compositions of bijections are bijections).

> [!example]- Example 2.2
> $\{0, 1, 2, \dots\} \approx \{1, 2, 3, \dots\}$ via $f(n) = n + 1$, even though the second is a proper subset of the first.

> **Definition 2.3 (Finite, cardinality)**
> $A$ is **finite** if $A = \varnothing$ (cardinality $0$) or $A \approx \{1, 2, \dots, k\}$ for some non-zero $k \in \mathbb{N}$ (cardinality $k$). Write $|A|$.

> [!note]- Remark 2.4 (cardinality is well-defined)
> If $A \approx \{1, \dots, k\}$ and $A \approx \{1, \dots, l\}$ with $k \neq l$, take the smallest such $k$; a bijection $\{1..k\} \to \{1..l\}$ with $k$ and $f(k)$ removed gives a smaller counterexample $k - 1 \neq l - 1$. ("Least criminal" argument.)

**Exercise 2.5** For finite $A, B$: if $A \subseteq B$ then $|A| \leq |B|$; if $f : A \to B$ is 1-1 then $|A| \leq |B|$; if $g : A \to B$ is onto then $|A| \geq |B|$.

> [!note]- Remark 2.6 (Cantor–Bernstein–Schröder, off-syllabus)
> For any sets, write $|A| \leq |B|$ if there's a 1-1 map $A \to B$. **CBS:** if $|A| \leq |B|$ and $|B| \leq |A|$ then $A \approx B$.

> **Definition 2.7 (Infinite)** A set which is not finite is **infinite**.

Equivalently, a set is infinite iff it is equinumerous with a proper subset (Remark 2.8). $\mathbb{N}, \mathbb{Z}, \mathbb{Q}, \mathbb{R}, \mathbb{C}$ are all infinite (Example 2.9), but not all equinumerous.

> **Definition 2.10 (Countable)**
> $A$ is **countably infinite** (denumerable) if $\mathbb{N} \approx A$. $A$ is **countable** if it is finite or countably infinite; otherwise **uncountable**.

(Some authors use "countable" to mean countably infinite.)

> **Proposition 2.11** $A$ is countable iff there is a 1-1 map $f : A \to \mathbb{N}$.

> **Corollary 2.12** If $B \subseteq A$ and $A$ is countable then $B$ is countable. Equivalently, if $B$ is uncountable, so is $A$.

> [!example]- Example 2.13: $\mathbb{Z}$ is countably infinite
> List $0, 1, -1, 2, -2, 3, -3, \dots$, i.e. $f(n) = (n+1)/2$ for $n$ odd and $-n/2$ for $n$ even.

> **Proposition 2.14**
> If $A_1, A_2$ are disjoint and countably infinite, then $A_1 \cup A_2$ is countably infinite.

> [!proof]- Proof
> With bijections $f_i : \mathbb{N} \to A_i$, define $g(n) = f_1(n/2)$ for $n$ even and $g(n) = f_2((n-1)/2)$ for $n$ odd. This is a bijection onto $A_1 \cup A_2$. $\square$

(Still true if not disjoint: skip repetitions, Remark 2.15.)

> **Proposition 2.16**
> If $A, B$ are countably infinite then $A \times B$ is countably infinite.

> [!proof]- Proof
> List $A = \{a_0, a_1, \dots\}$, $B = \{b_0, b_1, \dots\}$. Put $(a_i, b_j)$ in a grid and list it by zig-zagging along the diagonals:
> $$(a_0,b_0), (a_1,b_0), (a_0,b_1), (a_0,b_2), (a_1,b_1), (a_2,b_0), (a_3,b_0), \dots \quad \square$$

> **Corollary 2.17**
> If $A_0, A_1, A_2, \dots$ are countable then so is $\bigcup_{i=0}^\infty A_i$.

> [!proof]- Proof
> List each $A_i$ as $a_{i0}, a_{i1}, \dots$, place the $a_{ij}$ in a grid and count diagonally as in 2.16, skipping repeats. (Choosing a listing of every $A_i$ quietly uses the Axiom of Choice, Remark 2.18.) $\square$

**Notation 2.19** $\aleph_0$ ("aleph-null") denotes $|\mathbb{N}|$, the cardinality of any countably infinite set.

> [!example]- Examples 2.20 & 2.21: $\mathbb{N}^2$ and $\mathbb{Q}$ are countable
> **2.20** $f(m, n) = 2^m 3^n$ is an injection $\mathbb{N}^2 \to \mathbb{N}$.
> **2.21** $m/n$ in lowest terms $\mapsto (m, n)$ injects $\mathbb{Q}^+$ into $\mathbb{N}^2 \approx \mathbb{N}$. So $\mathbb{Q} = \{0\} \cup \mathbb{Q}^+ \cup \{-q : q \in \mathbb{Q}^+\}$ is countable.

> **Theorem 2.22** $\mathbb{R}$ is uncountable.

> [!proof]- Proof 1 (nested intervals)
> Suffices to show $[0, 1]$ isn't countably infinite (it is infinite: it contains every $1/k$). Suppose $f : \mathbb{N} \to [0,1]$ is a bijection, $x_k = f(k)$.
> - Choose $a_0 < b_0$ in $[0,1]$ with $x_0 \notin [a_0, b_0]$ (if $x_0 = 1$ take $[0, \frac12]$).
> - Given $[a_0, b_0]$, choose $a_0 < a_1 < b_1 < b_0$ with $x_1 \notin [a_1, b_1]$ (if $x_1 < b_0$ take $\max(a_0, x_1) < a_1 < b_1 < b_0$; if $x_1 \geq b_0$ take the middle third).
> - Repeat: $0 \leq a_0 < a_1 < \dots < b_1 < b_0 \leq 1$ with $x_i \notin [a_i, b_i]$.
> 
> Let $\lambda = \sup\{a_j\}$, $\mu = \inf\{b_j\}$. Every $b_n$ is an upper bound of the $a$'s so $\lambda \leq b_n$; so $\lambda$ is a lower bound of the $b$'s and $\lambda \leq \mu$. Hence $a_n \leq \lambda \leq \mu \leq b_n$ for all $n$, so $\lambda \in [a_n, b_n]$ while $x_n \notin [a_n, b_n]$. So $\lambda \neq x_n$ for every $n$: $f$ isn't onto. $\square$

> [!proof]- Proof 2 (Cantor's diagonal argument)
> Show $(0, 1]$ is uncountable. Each $x$ there has a unique decimal expansion $0.a_1a_2a_3\dots$ not ending in all zeros. Suppose $f : \mathbb{N} \to (0, 1]$ is a bijection with $f(k) = 0.r_{k1}r_{k2}r_{k3}\dots$. Define $\alpha = 0.a_1a_2\dots$ with
> $$a_k = \begin{cases} 6 & r_{kk} \neq 6 \\ 7 & r_{kk} = 6. \end{cases}$$
> This is a valid expansion, and $\alpha \neq f(k)$ since they differ in the $k$th digit. So $f$ is not onto. $\square$

**Notation 2.23** $\mathfrak{c}$ ("continuum") denotes $|\mathbb{R}|$.

> **Corollary 2.24** $\mathbb{C}$ is uncountable. (In fact $\mathbb{C} \approx \mathbb{R}$, by CBS.)

> **Theorem 2.25 (Cantor's Theorem, 1891)**
> For any set $A$, $|A| < |\mathcal{P}(A)|$: there is an injection $A \to \mathcal{P}(A)$ but no bijection.

> [!proof]- Proof
> $a \mapsto \{a\}$ is an injection. Given any $f : A \to \mathcal{P}(A)$, let $X = \{a \in A : a \notin f(a)\}$. If $X = f(x)$ for some $x$, then $x \in X \iff x \notin f(x) = X$, a contradiction. So $X \notin f(A)$ and $f$ is not onto. $\square$

> [!example]- Example 2.26
> $A = \{1, 2, 3\}$, $f(1) = \varnothing$, $f(2) = A$, $f(3) = \{1, 2\}$. Since $1 \notin f(1)$, $2 \in f(2)$, $3 \notin f(3)$: $X = \{1, 3\}$, which is not in $f(A)$.

Example 2.27: $\mathcal{P}(\mathbb{N}) \approx \mathbb{R}$ (via CBS).

> [!note]- Remark 2.28 (computable numbers)
> $\mathbb{Z}$, $\mathbb{Q}$ and the algebraic numbers are countable, and so are the **computable numbers** (reals a finite program can approximate to any accuracy), since there are only countably many programs. So describing all reals needs infinite descriptions, like infinite decimal expansions.
