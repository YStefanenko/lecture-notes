Linear Algebra I, Chapter 6. Back to [[LA1]].

Vector spaces are objects with structure; linear maps are the **structure-preserving maps** between them. (The same idea recurs throughout maths; abstracting it is Category Theory.)

## What Is a Linear Transformation?

> **Definition 144 (Linear map)**
> $T : V \to W$ (both over $\mathbb{F}$) is **linear** (a **linear transformation / linear map**) if
> 1. $T(v_1 + v_2) = T(v_1) + T(v_2)$, and
> 2. $T(\lambda v) = \lambda T(v)$
> 
> for all $v_1, v_2, v \in V$ and $\lambda \in \mathbb{F}$.

> **Proposition 145** A linear map sends $0_V$ to $0_W$.

> [!proof]- Proof
> $T(0_V) + T(0_V) = T(0_V + 0_V) = T(0_V)$, so $T(0_V) = 0_W$. $\square$

> **Proposition 146 (Equivalent forms of linearity)**
> These are equivalent:
> 1. $T$ is linear;
> 2. $T(\alpha v_1 + \beta v_2) = \alpha T(v_1) + \beta T(v_2)$;
> 3. $T(\alpha_1v_1 + \dots + \alpha_nv_n) = \alpha_1T(v_1) + \dots + \alpha_nT(v_n)$ for every $n \geq 1$.
> 
> *(Proof: exercise.)*

> [!example]- Example 147 (linear maps)
> - **Identity** $\text{id}_V(v) = v$ and the **zero map** $0(v) = 0_W$.
> - **Left / right multiplication** by $A \in M_{m \times n}(\mathbb{R})$: $L_A : \mathbb{R}^n_{\text{col}} \to \mathbb{R}^m_{\text{col}}$, $\mathbf v \mapsto A\mathbf v$; $R_A : \mathbb{R}^m \to \mathbb{R}^n$, $\mathbf v \mapsto \mathbf vA$. Also $X \mapsto AX$ on $M_{n \times p}$.
> - **Projection** (Proposition 148 below).
> - **Trace:** $\text{trace}(A) = a_{11} + \dots + a_{nn}$, a linear map $M_{n \times n}(\mathbb{R}) \to \mathbb{R}$.
> - **Differentiation** $D : \mathbb{R}_n[x] \to \mathbb{R}_n[x]$ (or $\to \mathbb{R}_{n-1}[x]$), $D(a_nx^n + \dots + a_0) = na_nx^{n-1} + \dots + a_1$; also $D : C^1(\mathbb{R}) \to \mathbb{R}^\mathbb{R}$ and $D : C^\infty(\mathbb{R}) \to C^\infty(\mathbb{R})$.
> - **Evaluation** $E_a : \mathbb{R}^X \to \mathbb{R}$, $f \mapsto f(a)$.

> **Proposition 148 (Projection)**
> If $V = U \oplus W$, write each $v$ uniquely as $u + w$ and set $P(v) = w$. Then $P$ is linear: the **projection of $V$ onto $W$ along $U$**.

> [!proof]- Proof
> With $v_i = u_i + w_i$: $\alpha_1v_1 + \alpha_2v_2 = (\alpha_1u_1 + \alpha_2u_2) + (\alpha_1w_1 + \alpha_2w_2)$ with the brackets in $U$ and $W$. By uniqueness, $P(\alpha_1v_1 + \alpha_2v_2) = \alpha_1w_1 + \alpha_2w_2 = \alpha_1P(v_1) + \alpha_2P(v_2)$. $\square$

## Combining Linear Transformations

> **Proposition 149 ($\text{Hom}(V, W)$)**
> With pointwise $(S + T)(v) = S(v) + T(v)$ and $(\lambda S)(v) = \lambda S(v)$, and the zero map, the linear maps $V \to W$ form a vector space $\text{Hom}(V, W)$.

> [!proof]- Proof
> $S + T$ is linear:
> $$(S + T)(\alpha_1v_1 + \alpha_2v_2) = \alpha_1S(v_1) + \alpha_2S(v_2) + \alpha_1T(v_1) + \alpha_2T(v_2) = \alpha_1(S + T)(v_1) + \alpha_2(S + T)(v_2).$$
> ($\lambda S$: exercise.) The axioms (commutativity, associativity, $S + 0 = S$, $(-S)(v) = -(S(v))$, and the scalar laws) all follow from the same laws in $W$, since everything is defined pointwise. $\square$

> **Proposition 150 (Composition)**
> If $S : U \to V$ and $T : V \to W$ are linear, so is $T \circ S$.

> [!proof]- Proof
> $(T \circ S)(\lambda_1u_1 + \lambda_2u_2) = T(\lambda_1S(u_1) + \lambda_2S(u_2)) = \lambda_1(T \circ S)(u_1) + \lambda_2(T \circ S)(u_2)$. $\square$

**Remark 151:** $T \circ S$ is often written $TS$ (apply $S$ first).

> **Definition 152 (Invertible, isomorphism)**
> Linear $T : V \to W$ is **invertible** if there is a linear $S : W \to V$ with $ST = \text{id}_V$ and $TS = \text{id}_W$. Then $S = T^{-1}$ is **the inverse** (unique, Remark 153), and $T$ is an **isomorphism**.

> **Proposition 154**
> A linear map is invertible iff it is bijective.

> [!proof]- Proof
> (⇒) Invertible functions are bijective.
> (⇐) The inverse function $S$ exists; we check it's linear. With $v_i = S(w_i)$, so $T(v_i) = w_i$:
> $$S(\lambda_1w_1 + \lambda_2w_2) = S(T(\lambda_1v_1 + \lambda_2v_2)) = \lambda_1v_1 + \lambda_2v_2 = \lambda_1S(w_1) + \lambda_2S(w_2). \ \square$$

> **Proposition 155** If $S : U \to V$ and $T : V \to W$ are invertible, so is $TS$, with $(TS)^{-1} = S^{-1}T^{-1}$. *(Exercise.)*

> **Proposition 156 (Isomorphic ⇔ same dimension)**
> 1. If $V$ is finite-dimensional and $T : V \to W$ is invertible, then $\dim V = \dim W$.
> 2. If $\dim V = \dim W$ (finite), there is an invertible linear $T : V \to W$.
> 
> So finite-dimensional $V \cong W$ iff $\dim V = \dim W$.

> [!proof]- Proof
> (1) If $v_1, \dots, v_n$ is a basis of $V$, then $Tv_1, \dots, Tv_n$ is a basis of $W$ (exercise).
> (2) With bases $v_i$ of $V$ and $w_i$ of $W$, $T\left(\sum\alpha_iv_i\right) = \sum\alpha_iw_i$ is a well-defined invertible linear map (exercise). $\square$

> [!example]- Example 157 ($\mathbb{R}[x]$ and sequences are not isomorphic)
> Both are infinite-dimensional: $\{1, x, x^2, \dots\}$ is a (countable) basis of $\mathbb{R}[x]$, and the sequences $(\delta_{in})_n$ are independent in the sequence space $W$.
> But $S = \{(t^n)_{n \geq 0} : t \in \mathbb{R}\}$ is an **uncountable** independent subset of $W$: if $\alpha_1(t_1^n) + \dots + \alpha_k(t_k^n) = 0$ with distinct $t_i$, the equations for $0 \leq n < k$ read
> $$\begin{pmatrix} 1 & \cdots & 1 \\ t_1 & \cdots & t_k \\ \vdots & & \vdots \\ t_1^{k-1} & \cdots & t_k^{k-1} \end{pmatrix}\begin{pmatrix} \alpha_1 \\ \vdots \\ \alpha_k \end{pmatrix} = \mathbf 0,$$
> and this (Vandermonde) matrix is invertible for distinct $t_i$ (Linear Algebra II), so all $\alpha_i = 0$. $\mathbb{R}[x]$ has no uncountable independent set, so $V \not\cong W$.

## Rank and Nullity

> **Definition 158 (Kernel, image)**
> For linear $T : V \to W$:
> $$\ker T = \{v \in V : T(v) = 0_W\} \ (\text{the **null space**}), \qquad \text{Im}\,T = \{T(v) : v \in V\}.$$

> **Proposition 159**
> 1. $\ker T \leqslant V$ and $\text{Im}\,T \leqslant W$.
> 2. $T$ is injective iff $\ker T = \{0_V\}$.
> 3. If $A$ spans $V$, then $T(A)$ spans $\text{Im}\,T$.
> 4. If $V$ is finite-dimensional, so are $\ker T$ and $\text{Im}\,T$.

> [!proof]- Proof
> (1) Subspace test. $0_V \in \ker T$ and $T(\lambda v_1 + v_2) = \lambda 0 + 0 = 0$. $0_W = T(0_V) \in \text{Im}\,T$ and $\lambda T(v_1) + T(v_2) = T(\lambda v_1 + v_2)$.
> (2) If $T$ is injective and $T(v) = 0 = T(0_V)$, then $v = 0_V$. Conversely, if $Tv_1 = Tv_2$ then $T(v_1 - v_2) = 0$, so $v_1 = v_2$.
> (3) $w = T(\sum\alpha_iv_i) = \sum\alpha_iT(v_i)$ with $v_i \in A$.
> (4) $\ker T \leqslant V$ (Prop 134); $\text{Im}\,T$ by (3). $\square$

> **Corollary 160**
> $\text{Im}\,L_A = \text{Col}(A)$ and $\text{Im}\,R_A = \text{Row}(A)$.

> [!proof]- Proof
> The rows of $A$ are $\mathbf e_iA = R_A(\mathbf e_i)$, so they span $\text{Im}\,R_A$ (Prop 159(3)), and conversely $\sum\alpha_i\mathbf r_i = (\sum\alpha_i\mathbf e_i)A \in \text{Im}\,R_A$. Likewise for $L_A$. $\square$

> **Definition 161 (Rank, nullity)**
> For finite-dimensional $V$: $\text{nullity}(T) = \dim\ker T$ and $\text{rank}(T) = \dim\text{Im}\,T$. So $\text{rank}(L_A)$ is the column rank of $A$ and $\text{rank}(R_A)$ its row rank.

> **Theorem 162 (Rank–Nullity)**
> For linear $T : V \to W$ with $V$ finite-dimensional,
> $$\dim V = \text{rank}(T) + \text{nullity}(T).$$

> [!proof]- Proof
> Take a basis $v_1, \dots, v_n$ of $\ker T$ and extend it to a basis $v_1, \dots, v_n, v_1', \dots, v_r'$ of $V$. Claim: $Tv_1', \dots, Tv_r'$ is a basis of $\text{Im}\,T$.
> *Spans:* the images of a basis span $\text{Im}\,T$ (Prop 159(3)), and $Tv_i = 0$.
> *Independent:* if $\sum\alpha_iT(v_i') = 0$, then $\sum\alpha_iv_i' \in \ker T$, so $\sum\alpha_iv_i' = \sum\beta_jv_j$. Independence of the basis of $V$ gives all $\alpha_i = \beta_j = 0$.
> So $\dim V = n + r = \text{nullity}(T) + \text{rank}(T)$. $\square$

> **Corollary 163**
> For linear $T : V \to V$ ($V$ finite-dimensional), these are equivalent:
> 1. $T$ is invertible;
> 2. $\text{rank}\,T = \dim V$;
> 3. $\text{nullity}\,T = 0$.

> [!proof]- Proof
> (1 ⇒ 2) Bijective, so surjective, so $\text{Im}\,T = V$.
> (2 ⇒ 3) Rank–Nullity.
> (3 ⇒ 1) $\ker T = \{0\}$, so $T$ is injective; by Rank–Nullity $\text{rank}\,T = \dim V$, so $\text{Im}\,T = V$ (Prop 134) and $T$ is surjective. $\square$

> **Corollary 164 (One-sided inverses are two-sided)**
> For linear $T : V \to V$ ($V$ finite-dimensional), any one-sided inverse of $T$ is a two-sided inverse, and so is unique.

> [!proof]- Proof
> If $T \circ S = \text{id}_V$, then $T$ is surjective, so invertible by Cor 163, with inverse $S'$. Then $S' = S' \circ (T \circ S) = (S' \circ T) \circ S = S$.
> If $S \circ T = \text{id}_V$, then $T$ is injective, so $\text{nullity}\,T = 0$, and argue the same way. $\square$

> **Corollary 165** If $A, B$ are square and $AB$ is invertible, then $A$ and $B$ are invertible. *(Cor 164 in matrix form.)*

> **Lemma 166**
> For linear $T : V \to W$ ($V$ finite-dimensional) and $U \leqslant V$:
> $$\dim U - \text{nullity}\,T \leq \dim T(U) \leq \dim U.$$
> In particular, if $T$ is injective then $\dim T(U) = \dim U$.

> [!proof]- Proof
> Let $S = T|_U$. Then $\ker S \leqslant \ker T$ and $\text{Im}\,S = T(U)$. By Rank–Nullity, $\dim T(U) = \dim U - \text{nullity}\,S$, and $0 \leq \text{nullity}\,S \leq \text{nullity}\,T$. $\square$

**Rank–Nullity with matrices (Remark 167):** in $\text{RRE}(A)$:
- row rank = number of leading 1s;
- nullity = number of columns without a leading 1 (each gets a parameter).

So $n = \text{rank} + \text{nullity}$ is just "every column either has a leading 1 or doesn't".

> **Corollary 168 (Criteria for invertibility)**
> For $A$ ($n \times n$), these are equivalent:
> 1. $A$ is invertible;
> 2. $A$ has a left inverse;
> 3. $A$ has a right inverse;
> 4. $\text{Row}(A) = \mathbb{R}^n$;
> 5. the columns of $A$ are linearly independent;
> 6. the rows of $A$ are linearly independent;
> 7. $A\mathbf x = \mathbf 0$ only has the solution $\mathbf x = \mathbf 0$;
> 8. the row rank of $A$ is $n$;
> 9. $\text{RRE}(A) = I_n$.
> 
> *(Proofs: exercises; several have been done already.)*
