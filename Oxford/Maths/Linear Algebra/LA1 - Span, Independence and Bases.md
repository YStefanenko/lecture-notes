Linear Algebra I, Chapter 4. Back to [[LA1]]. Builds on [[LA1 - Vector Spaces and Subspaces]].

The goal of this chapter is a sensible notion of **dimension**. That needs spans, linear independence and bases first.

## Spans and Spanning Sets

> **Lemma 87**
> For $S = \{u_1, \dots, u_m\} \subseteq V$, the set $U = \{\alpha_1u_1 + \dots + \alpha_mu_m : \alpha_i \in \mathbb{F}\}$ is a subspace of $V$.

> [!proof]- Proof
> Subspace test: $0_V = 0u_1 + \dots + 0u_m \in U$, and for $v_1 = \sum\alpha_iu_i$, $v_2 = \sum\beta_iu_i$, we get $\lambda v_1 + v_2 = \sum(\lambda\alpha_i + \beta_i)u_i \in U$. $\square$

> **Definition 88 (Linear combination, span)**
> A **linear combination** of $u_1, \dots, u_m$ is a vector $\alpha_1u_1 + \dots + \alpha_mu_m$. Their **span** is
> $$\langle u_1, \dots, u_m\rangle = \{\alpha_1u_1 + \dots + \alpha_mu_m : \alpha_i \in \mathbb{F}\},$$
> the **smallest subspace containing** $u_1, \dots, u_m$. For any $S \subseteq V$ (even infinite), $\langle S\rangle$ is the set of all **finite** linear combinations of elements of $S$. By convention $\langle\emptyset\rangle = \{0_V\}$.

A vector space has no notion of infinite sums, so linear combinations are always finite.

> **Definition 89 (Spanning set)**
> $S$ **spans** $V$ (is a **spanning set**) if $\langle S\rangle = V$.

> [!example]- Examples 90 – 92
> - **90** $\{(1,1), (2,-1)\}$ spans $\mathbb{R}^2$: $(x, y) = \frac{x+2y}{3}(1,1) + \frac{x-y}{3}(2,-1)$. But $\langle(2,2), (-1,-1)\rangle$ is only the line $y = x$.
> - **91** $\{(1,1,2), (2,-1,3)\}$ spans the plane $\mathbf r = \alpha(1,1,2) + \beta(2,-1,3)$; eliminating $\alpha, \beta$ gives $5x + y - 3z = 0$.
> - **92** Adding $(3,0,5) = (1,1,2) + (2,-1,3)$ gives the same plane, but now points have many expressions, e.g.
> $$(0,3,1) = 2(1,1,2) - (2,-1,3) + 0(3,0,5) = (1,1,2) - 2(2,-1,3) + (3,0,5).$$
> The set is redundant: it isn't linearly independent.

> **Definition 93 (Row space, column space)**
> For $A \in M_{m \times n}$: $\text{Row}(A) \leqslant \mathbb{R}^n$ is the span of its rows; $\text{Col}(A) \leqslant \mathbb{R}^m_{\text{col}}$ is the span of its columns.

> [!example]- Example 94 (EROs keep row space, not column space)
> The matrix of Example 7 and its RRE form
> $$\left(\begin{array}{cccc|c} 1 & -1 & 1 & 3 & 2 \\ 2 & -1 & 1 & 2 & 4 \\ 4 & -3 & 3 & 8 & 8 \end{array}\right), \qquad \left(\begin{array}{cccc|c} 1 & 0 & 0 & -1 & 2 \\ 0 & 1 & -1 & -4 & 0 \\ 0 & 0 & 0 & 0 & 0 \end{array}\right)$$
> have the same row space (Proposition 117), but $(1, 2, 4)^T$ is in the column space of the first and not the second.

## Linear Independence

> **Definition 95 (Linear independence)**
> $v_1, \dots, v_m$ are **linearly independent** if
> $$\alpha_1v_1 + \dots + \alpha_mv_m = 0_V \implies \alpha_1 = \dots = \alpha_m = 0.$$
> Otherwise they're **linearly dependent**: some non-trivial combination is $0_V$. An infinite $S$ is independent if every finite subset is.

> [!example]- Examples 96 – 98
> - **96** $\{(1,1,2), (2,-1,3)\}$ is independent: the first two coordinates of $\alpha(1,1,2) + \beta(2,-1,3) = \mathbf 0$ give $\alpha + 2\beta = 0$ and $\alpha - \beta = 0$, so $\alpha = \beta = 0$. (It doesn't span $\mathbb{R}^3$.)
> - **97** $\{(1,1,2), (2,-1,3), (3,0,5)\}$ is dependent: $1(1,1,2) + 1(2,-1,3) - 1(3,0,5) = \mathbf 0$.
> - **98** $\{\sin x, \cos x, \sin 2x\}$ is independent in the differentiable functions: from $\alpha\sin x + \beta\cos x + \gamma\sin 2x = 0$, put $x = 0$ to get $\beta = 0$, then $x = \pi/2$ to get $\alpha = 0$, so $\gamma = 0$.

> **Proposition 99 (Comparing coefficients)**
> If $\{v_1, \dots, v_m\}$ is independent, then $\sum\alpha_iv_i = \sum\beta_iv_i$ iff $\alpha_i = \beta_i$ for all $i$.

> [!proof]- Proof
> Rearrange to $\sum(\alpha_i - \beta_i)v_i = 0_V$ and use independence. $\square$

> [!example]- Examples 100 – 101
> - **100** In $\mathbb{C}$ as a real space, $\{1, i\}$ is independent, so "comparing real and imaginary parts" is valid.
> - **101** In $\mathbb{R}[x]$, $\{1, x, x^2, \dots\}$ is independent: if $\sum_{k \leq n} a_kx^k$ is the zero function, put $x = 0$ to get $a_0 = 0$, differentiate and put $x = 0$ to get $a_1 = 0$, and so on.

> **Lemma 102 (Extending an independent set)**
> If $v_1, \dots, v_m$ are independent, then $v_1, \dots, v_m, v_{m+1}$ are independent iff $v_{m+1} \notin \langle v_1, \dots, v_m\rangle$.

> [!proof]- Proof
> (⇐) If $\sum_{i=1}^{m+1}\alpha_iv_i = 0$ with $\alpha_{m+1} \neq 0$, then $v_{m+1} = -\frac{1}{\alpha_{m+1}}\sum_{i \leq m}\alpha_iv_i \in \langle v_1, \dots, v_m\rangle$, a contradiction. So $\alpha_{m+1} = 0$, and the rest vanish by independence.
> (⇒) If $v_{m+1} = \sum\alpha_iv_i$, then $\sum\alpha_iv_i - v_{m+1} = 0$ is a non-trivial dependence. $\square$

## Bases

> **Definition 103 (Basis, finite-dimensional)**
> A **basis** of $V$ is a linearly independent spanning set. If $V$ has a finite basis, it is **finite-dimensional**.

- **Remark 104:** say "*a* basis", not "*the* basis". Most spaces have many, though some have a **standard** (canonical) one.
- **Remark 105:** $\mathbb{R}[x]$ and the space of real sequences have no finite basis. Infinite-dimensional spaces need extra analytic structure (to make sense of infinite sums), which is Functional Analysis.

> [!example]- Examples 106 – 110 (bases)
> - **106** The **standard / canonical basis** $\mathbf e_1, \dots, \mathbf e_n$ of $\mathbb{R}^n$: $(a_1, \dots, a_n) = \sum a_i\mathbf e_i$, and the $i$th entry shows independence.
> - **107** $\{E_{ij}\}$ is the standard basis of $M_{m \times n}(\mathbb{F})$: $A = \sum_{i,j}a_{ij}E_{ij}$ uniquely.
> - **108** $V = \{x + 2y + z = 0\} \leqslant \mathbb{R}^3$ has basis $\{(1,0,-1), (0,1,-2)\}$: parametrise by $x, y$, so $(x, y, -x-2y) = x(1,0,-1) + y(0,1,-2)$ uniquely. *(The notes print the second vector as $(0,2,-1)$, a typo: it isn't in $V$.)*
> - **109** The solutions in $\mathbb{R}^5$ of
> $$x_1 + x_2 - x_3 + x_5 = 0,\quad x_1 + 2x_2 + x_4 + 3x_5 = 0,\quad x_2 + x_3 + x_4 + 2x_5 = 0$$
> reduce to $\begin{pmatrix} 1 & 0 & -2 & -1 & -1 \\ 0 & 1 & 1 & 1 & 2 \\ 0 & 0 & 0 & 0 & 0 \end{pmatrix}$. With $x_3 = \alpha$, $x_4 = \beta$, $x_5 = \gamma$, a basis is
> $$\{(2,-1,1,0,0),\ (1,-1,0,1,0),\ (1,-2,0,0,1)\}.$$
> - **110** $\mathbb{F}[x]$ has standard basis $\{1, x, x^2, \dots\}$.

> **Proposition 111 (Basis ⇔ unique expressions)**
> $S = \{v_1, \dots, v_n\}$ is a basis of $V$ iff every $v \in V$ has a **unique** expression as a linear combination of elements of $S$.

> [!proof]- Proof
> (⇒) Spanning gives an expression; Proposition 99 gives uniqueness.
> (⇐) Every $v$ is a combination, so $S$ spans. If $\sum\alpha_iv_i = 0 = \sum 0v_i$, uniqueness gives $\alpha_i = 0$, so $S$ is independent. $\square$

> **Definition 112 (Coordinates)**
> Given a basis $\{v_1, \dots, v_n\}$, the unique scalars in $v = \alpha_1v_1 + \dots + \alpha_nv_n$ are the **coordinates** of $v$ with respect to that basis.

**Remark 113:** choosing a basis identifies $V$ with $\mathbb{R}^n$, $v \mapsto \mathbf v = (\alpha_1, \dots, \alpha_n)$. A vector space has an origin but no axes; a basis puts in axes. **A coordinate vector means nothing without its basis.**

> [!example]- Example 114 (same space, different coordinates)
> $V = \{f : f'' = 4f\}$ has bases $\{e^{2x}, e^{-2x}\}$ and $\{\sinh 2x, \cosh 2x\}$. The vector $e^{2x} = \sinh 2x + \cosh 2x$ has coordinates $(1, 0)$ in the first and $(1, 1)$ in the second; the coordinate vector $(1, 0)$ means $e^{2x}$ in the first but $\sinh 2x$ in the second.

> [!note]- Remarks 115 – 116
> **115** Is there a *best* basis? That question drives a lot of later linear algebra (diagonalisation, orthonormal bases).
> **116** Every vector space has a basis **if** you assume the Axiom of Choice. But a basis of $\ell^\infty$ must be uncountable, so for infinite-dimensional spaces bases are not very useful; that's functional analysis, where infinite sums make sense.

## Testing Independence and Spanning with RRE

> **Proposition 117**
> Let $A$ be $m \times n$, $B$ be $k \times m$, and $R$ an RRE form of $A$.
> 1. The non-zero rows of $R$ are independent.
> 2. The rows of $R$ are linear combinations of the rows of $A$.
> 3. $\text{Row}(BA) \subseteq \text{Row}(A)$.
> 4. If $k = m$ and $B$ is invertible, $\text{Row}(BA) = \text{Row}(A)$.
> 5. $\text{Row}(R) = \text{Row}(A)$: **EROs don't change the row space.**

> [!proof]- Proof
> (1) If $\sum c_i\mathbf r_i = \mathbf 0$, look at the column of the leading 1 of $\mathbf r_1$: every other row has $0$ there, so $c_1 = 0$. Repeat with $\mathbf r_2$, etc.
> (3) The $i$th row of $BA$ is
> $$\sum_{s=1}^m b_{is}(a_{s1}, \dots, a_{sn}) = \sum_s b_{is}(\text{row } s \text{ of } A), \tag{4.1}$$
> so every row of $BA$, and hence every combination of them, is in $\text{Row}(A)$.
> (2) $R = E_k\cdots E_1A$; apply (3).
> (4) $\text{Row}(BA) \subseteq \text{Row}(A) = \text{Row}(B^{-1}(BA)) \subseteq \text{Row}(BA)$.
> (5) (4) with $B = E_k\cdots E_1$, invertible. $\square$

> **Corollary 118 (Test for independence)**
> $\text{RRE}(A)$ has a zero row iff the rows of $A$ are dependent.

> [!proof]- Proof
> $\text{RRE}(A) = BA$ with $B$ invertible. If row $i$ of $BA$ is $\mathbf 0$, then by (4.1) $\mathbf 0 = \sum_s b_{is}(\text{row } s \text{ of } A)$, and the $b_{is}$ aren't all zero ($B$ is invertible), so the rows are dependent.
> Conversely, if $\mathbf r_m = \sum_{i<m}c_i\mathbf r_i$, the EROs $A_{im}(-c_i)$ make row $m$ zero; reduce the other rows to RRE form. By uniqueness of RRE form (Theorem 122) $\text{RRE}(A)$ has a zero row. $\square$

> **Corollary 119 (Test for a spanning set)**
> The rows of $A$ ($m \times n$) span $\mathbb{R}^n$ iff
> $$\text{RRE}(A) = \begin{pmatrix} I_n \\ 0_{(m-n)n} \end{pmatrix}.$$

> [!proof]- Proof
> Row space is invariant under EROs. If column $i$ of $\text{RRE}(A)$ had no leading 1, then $\mathbf e_i$ wouldn't be in the row space. So every column has a leading 1, which forces the form above. Conversely, the rows of that matrix span, hence so do the rows of $A$. $\square$

**Remark 120:** consequently, independent vectors in $\mathbb{R}^n$ number $k \leq n$, and spanning vectors number $k \geq n$. So **every basis of $\mathbb{R}^n$ has $n$ vectors**. This common size is the **dimension** (done coordinate-free in [[LA1 - Dimension]]).

> [!example]- Example 121
> (a) $\mathbf v_1 = (1,2,-1,0)$, $\mathbf v_2 = (2,1,0,3)$, $\mathbf v_3 = (0,1,1,1)$ are independent:
> $$\begin{pmatrix} 1 & 2 & -1 & 0 \\ 2 & 1 & 0 & 3 \\ 0 & 1 & 1 & 1 \end{pmatrix} \xrightarrow{\text{RRE}} \begin{pmatrix} 1 & 0 & 0 & 1.6 \\ 0 & 1 & 0 & -0.2 \\ 0 & 0 & 1 & 1.2 \end{pmatrix}$$
> has no zero row.
> (b) $\mathbf x = (x_1, x_2, x_3, x_4) \in \langle\mathbf v_1, \mathbf v_2, \mathbf v_3\rangle$ iff $8x_1 + 6x_3 = x_2 + 5x_4$: append $\mathbf x$ as a fourth row and reduce; the last row becomes $(0, 0, 0, x_4 - 1.6x_1 + 0.2x_2 - 1.2x_3)$, which must be zero.

## Addendum: Uniqueness of RRE Form and Rank

> **Theorem 122 (Uniqueness of RRE form)**
> The reduced row echelon form of an $m \times n$ matrix is unique. *(Proof off-syllabus; the result isn't.)*

> [!proof]- Proof (induction on the number of columns $n$)
> $n = 1$: the only RRE $m \times 1$ matrices are $\mathbf 0$ and $\mathbf e_1^T$, and a matrix reduces to the first iff it's zero.
> Inductive step: let $\tilde A$ be the first $n - 1$ columns of $A$. Any EROs reducing $A$ also reduce $\tilde A$, to the unique $\text{RRE}(\tilde A)$ with $r$ non-zero rows. Either:
> (i) $\mathbf e_n \in \text{Row}(A)$: any RRE form of $A$ has an extra row $\mathbf e_n$, so its last column is $\mathbf e_{r+1}^T$, and it is determined.
> (ii) otherwise: any two RRE forms $R_1, R_2$ have $r$ non-zero rows and $\text{Row}(R_1) = \text{Row}(A) = \text{Row}(R_2)$ (Prop 117(e)). So $\mathbf r_i(R_1) = \sum_k\lambda_k\mathbf r_k(R_2)$. Looking at the first $n - 1$ columns, $\mathbf r_i(\text{RRE}(\tilde A)) = \sum_k\lambda_k\mathbf r_k(\text{RRE}(\tilde A))$, and independence of these rows forces $\lambda_i = 1$, $\lambda_j = 0$ otherwise. So $R_1 = R_2$. $\square$

> **Definition 123 (Row rank)**
> The **row rank** (or **rank**) of $A$, $\text{rank}(A)$, is the number of non-zero rows in $\text{RRE}(A)$. It is well-defined by Theorem 122.

> **Corollary 124 (Consistency)**
> $A\mathbf x = \mathbf b$ is consistent iff $\text{rank}(A \mid \mathbf b) = \text{rank}(A)$.

> [!proof]- Proof
> True for RRE systems (proof of Proposition 44). With $\text{RRE}(A) = PA$ and $\text{rank}(EA) = \text{rank}(A)$ for elementary $E$:
> $\text{rank}(A|\mathbf b) = \text{rank}(A) \iff \text{rank}(PA|P\mathbf b) = \text{rank}(PA) \iff PA\mathbf x = P\mathbf b$ consistent $\iff A\mathbf x = \mathbf b$ consistent. $\square$

> **Proposition 125 (Solutions in terms of rank)**
> For $A$ ($m \times n$) and $\mathbf b \in \mathbb{R}^m_{\text{col}}$:
> 1. $A\mathbf x = \mathbf b$ has no solutions iff $(0\ \cdots\ 0 \mid 1) \in \text{Row}(A \mid \mathbf b)$.
> 
> If it is consistent:
> 2. the solution is unique iff $\text{rank}(A) = n$ (so $m \geq n$);
> 3. if $\text{rank}(A) < n$ there are infinitely many, an $(n - \text{rank}(A))$-parameter family.

> [!proof]- Proof
> EROs change neither the row space nor the solution set, so this is Proposition 44 restated. $\square$

**Remark 126:** **column rank** (via column operations) equals row rank (Theorem 191 in [[LA1 - Matrices of Linear Maps]]), so we just say "rank".
