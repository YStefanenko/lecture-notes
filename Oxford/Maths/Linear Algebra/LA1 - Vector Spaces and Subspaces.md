Linear Algebra I, Chapter 3. Back to [[LA1]].

Vectors don't need coordinates: the displacement $\overrightarrow{PQ}$ exists before you choose an origin and axes. Vector spaces abstract the two operations all "vectors" share: **addition** and **scalar multiplication**. Their elements can be functions, sequences, matrices, solutions of equations…

## What Is a Vector Space?

> **Definition 59 (Real vector space)**
> A **real vector space** is a non-empty set $V$ with **addition** $V \times V \to V$ and **scalar multiplication** $\mathbb{R} \times V \to V$ such that, for all $u, v, w \in V$ and $\lambda, \mu \in \mathbb{R}$:
> 1. $u + v = v + u$ (commutative)
> 2. $u + (v + w) = (u + v) + w$ (associative)
> 3. there is $0_V$ with $v + 0_V = v = 0_V + v$ (additive identity)
> 4. each $v$ has $w$ with $v + w = 0_V = w + v$ (additive inverse)
> 5. $\lambda(u + v) = \lambda u + \lambda v$
> 6. $(\lambda + \mu)v = \lambda v + \mu v$
> 7. $(\lambda\mu)v = \lambda(\mu v)$
> 8. $1v = v$
> 
> $\mathbb{R}$ is the **field of scalars** (base field). Elements of $V$ are **vectors**; elements of $\mathbb{R}$ are **scalars**.

**More generally,** a vector space over any **field $\mathbb{F}$** uses the same axioms with $\mathbb{F} \times V \to V$. Common fields: $\mathbb{R}$, $\mathbb{C}$, $\mathbb{Q}$, $\mathbb{Z}_p$ ($p$ prime).
- A non-zero real vector space is infinite; over $\mathbb{Z}_p$ it can be finite.
- $\mathbb{C}$ is a 2-dimensional real space ($z = x\cdot1 + y\cdot i$) but a 1-dimensional complex one ($z = z\cdot 1$).

**What to check in practice (Remark 60):** $V$ has a zero vector, and is closed under addition and scalar multiplication. With natural operations the rest is routine. The subspaces of $\mathbb{R}^3$ are the origin, lines through the origin, planes through the origin, and $\mathbb{R}^3$ itself.

> [!example]- Examples 61 – 68 (vector spaces)
> - **61** $\mathbb{R}^n$ with componentwise operations: zero $(0, \dots, 0)$, inverse $(-v_1, \dots, -v_n)$. (Notation 62: coordinate vectors are bold, $\mathbf v$; abstract vectors aren't.)
> - **63** $\mathbb{C}$ as a real vector space (essentially $\mathbb{R}^2$; "isomorphic").
> - **64** $M_{m \times n}(\mathbb{R})$.
> - **65** $\mathbb{R}^\mathbb{R} = \{f : \mathbb{R} \to \mathbb{R}\}$ with pointwise operations $(f + g)(r) = f(r) + g(r)$, $(\alpha f)(r) = \alpha f(r)$.
> - **66** Differentiable $f : \mathbb{R} \to \mathbb{R}$, since $(f + g)' = f' + g'$ and $(\alpha f)' = \alpha f'$.
> - **67** $\{f : f'' = f\}$, since the equation is **linear**. Its general solution is $A\cosh x + B\sinh x = Ae^x + Be^{-x}$; both identify $V$ with $\mathbb{R}^2$, but $(1, 0)$ means $\cosh x$ in one and $e^x$ in the other (different coordinates).
> - **68** Sequences $\mathbb{R}^\mathbb{N}$, and inside it $\ell^\infty$ (bounded), $c$ (convergent), $c_0$ (tending to 0). Exercise: which theorems of Analysis make these vector spaces?

> **Lemma 69** The additive identity $0_V$ is unique.

> [!proof]- Proof
> If $0, 0'$ are both identities: $0 = 0 + 0' = 0'$. $\square$

**Remark 70:** when it's unambiguous, write $0$ for $0_V$.

> **Lemma 71** Additive inverses are unique (written $-v$, Remark 72).

> [!proof]- Proof
> If $v + w_1 = 0 = w_1 + v$ and $v + w_2 = 0 = w_2 + v$: $w_2 = 0 + w_2 = (w_1 + v) + w_2 = w_1 + (v + w_2) = w_1 + 0 = w_1$. $\square$

> **Proposition 73**
> For $v \in V$, $\lambda \in \mathbb{F}$:
> 1. $\lambda 0_V = 0_V$
> 2. $0v = 0_V$
> 3. $(-\lambda)v = -(\lambda v) = \lambda(-v)$
> 4. if $\lambda v = 0_V$ then $\lambda = 0$ or $v = 0_V$
> 5. $-v = (-1)v$

> [!proof]- Proof
> 1. $\lambda 0_V = \lambda(0_V + 0_V) = \lambda 0_V + \lambda 0_V$; add $-(\lambda 0_V)$.
> 2. Exercise (use $0 + 0 = 0$ in $\mathbb{F}$).
> 3. $\lambda v + \lambda(-v) = \lambda(v + (-v)) = \lambda 0_V = 0_V$, so $\lambda(-v) = -(\lambda v)$ by uniqueness; similarly $\lambda v + (-\lambda)v = 0v = 0_V$.
> 4. If $\lambda \neq 0$: $v = 1v = (\lambda^{-1}\lambda)v = \lambda^{-1}(\lambda v) = \lambda^{-1}0_V = 0_V$.
> 5. $v + (-1)v = (1 + (-1))v = 0v = 0_V$; uniqueness of inverses. $\square$

## Subspaces

> **Definition 74 (Subspace)**
> A **subspace** of $V$ is a subset $U \subseteq V$ that is
> 1. non-empty (usually: show $0_V \in U$),
> 2. closed under addition,
> 3. closed under scalar multiplication,
> 
> using $V$'s own operations.

> **Definition 75 (Trivial and proper subspaces)**
> $\{0_V\}$ (the **zero / trivial subspace**) and $V$ are always subspaces. Subspaces other than $V$ are **proper**.

> **Proposition 76 (Subspace test)**
> $U \subseteq V$ is a subspace iff
> 1. $0_V \in U$, and
> 2. $\lambda u_1 + u_2 \in U$ for all $u_1, u_2 \in U$, $\lambda \in \mathbb{F}$.

> [!proof]- Proof
> (⇒) $U$ is non-empty: pick $u$, then $0u = 0_V \in U$. And $\lambda u_1 \in U$, so $\lambda u_1 + u_2 \in U$.
> (⇐) $0_V \in U$, so it's non-empty. $u_1 + u_2 = 1u_1 + u_2 \in U$ and $\lambda u = \lambda u + 0_V \in U$. $\square$

**Notation 77:** $U \leqslant V$ means $U$ is a subspace of $V$.

> **Proposition 78**
> If $U \leqslant V$:
> 1. $U$ is a vector space over $\mathbb{F}$. In fact the subspaces are exactly the subsets of $V$ that are vector spaces under its operations.
> 2. If $W \leqslant U$ then $W \leqslant V$.

> [!proof]- Proof
> (1) Closure makes $+$ and scalar multiplication well-defined maps on $U$. Commutativity, associativity and the four scalar axioms are inherited from $V$; $0_V \in U$ by the subspace test; inverses: $-u = (-1)u \in U$.
> (2) Immediate. $\square$

> **Proposition 79 (Sums and intersections)**
> If $U, W \leqslant V$, then
> $$U + W = \{u + w : u \in U, w \in W\} \leqslant V \quad\text{and}\quad U \cap W \leqslant V.$$
> $U + W$ is the smallest subspace containing $U$ and $W$; $U \cap W$ is the largest contained in both.

> [!proof]- Proof (sum)
> $0_V = 0_V + 0_V \in U + W$. If $v_i = u_i + w_i$, then $\lambda v_1 + v_2 = (\lambda u_1 + u_2) + (\lambda w_1 + w_2) \in U + W$. Intersection: exercise. $\square$

## Further Examples

> [!example]- Example 80 (solutions of a homogeneous system)
> The solution set of $A\mathbf x = \mathbf 0$ ($A \in M_{m \times n}(\mathbb{R})$) is a subspace of $\mathbb{R}^n_{\text{col}}$: it contains $\mathbf 0$; if $A\mathbf v_1 = A\mathbf v_2 = \mathbf 0$ then $A(\mathbf v_1 + \mathbf v_2) = \mathbf 0$; and $A(\lambda\mathbf v) = \lambda A\mathbf v = \mathbf 0$.

> [!example]- Examples 81 – 84 (functions and polynomials)
> - **81** $\mathbb{R}[x]$, the real polynomials, is a subspace of $\mathbb{R}^\mathbb{R}$ (finite sums stay polynomials).
> - **82** Polynomials of degree $\leq n$ form a subspace of $\mathbb{R}[x]$.
> - **83** $\mathbb{R}^X = \{f : X \to \mathbb{R}\}$ for any set $X$, with pointwise operations.
> - **84** Solutions of $y'' + a(x)y' + b(x)y = 0$ (linear, homogeneous ODE): if $w = u + \lambda v$ with $u, v$ solutions, then
> $$w'' + aw' + bw = (u'' + au' + bu) + \lambda(v'' + av' + bv) = 0.$$
> So they form a subspace of $\mathbb{R}^\mathbb{R}$ (any order works the same way).

> [!example]- Example 85: the subspaces of $\mathbb{R}$
> If $U \neq \{0\}$, pick $u \neq 0$ in $U$; any $x = \frac xu\cdot u \in U$. So the only subspaces are $\{0\}$ and $\mathbb{R}$.

> [!example]- Example 86: the subspaces of $\mathbb{R}^2$
> Let $U \neq \{0\}$ contain $\mathbf u = (a, b) \neq 0$, so $\langle\mathbf u\rangle = \{\lambda\mathbf u\} \subseteq U$.
> - If $U = \langle\mathbf u\rangle$: it's the line $y = \frac ba x$ (or the $y$-axis if $a = 0$), a line through the origin.
> - Otherwise there's $\mathbf v = (c, d) \in U \setminus \langle\mathbf u\rangle$. EROs on $\begin{pmatrix} a & b \\ c & d \end{pmatrix}$ keep its rows in $U$, and its RRE form is $I_2$, so $(1, 0), (0, 1) \in U$ and $U = \mathbb{R}^2$.
> 
> So the subspaces are $\{\mathbf 0\}$, lines through the origin, and $\mathbb{R}^2$.
