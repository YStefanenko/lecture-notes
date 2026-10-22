Linear Algebra I, Chapter 5. Back to [[LA1]]. Builds on [[LA1 - Span, Independence and Bases]].

We've seen with coordinates that in $\mathbb{R}^n$ independent sets have $\leq n$ elements and spanning sets have $\geq n$. This chapter proves it **without coordinates**, for any vector space.

## Steinitz Exchange and Dimension

> **Theorem 127 (Steinitz Exchange Lemma)**
> Let $X = \{v_1, \dots, v_n\} \subseteq V$. If $u \in \langle X\rangle$ but $u \notin \langle X \setminus \{v_i\}\rangle$, then with $Y = (X \setminus \{v_i\}) \cup \{u\}$ ("exchange $u$ for $v_i$"),
> $$\langle Y\rangle = \langle X\rangle.$$

> [!proof]- Proof
> Write $u = \alpha_1v_1 + \dots + \alpha_nv_n$ and take $i = n$. Since $u \notin \langle v_1, \dots, v_{n-1}\rangle$, $\alpha_n \neq 0$, so
> $$v_n = \frac{1}{\alpha_n}(u - \alpha_1v_1 - \dots - \alpha_{n-1}v_{n-1}).$$
> Anything in $\langle Y\rangle$: substitute for $u$ to get a combination of $X$. Anything in $\langle X\rangle$: substitute for $v_n$ to get a combination of $Y$. $\square$

It's called a lemma, but it is what makes dimension well-defined.

> **Theorem 128 (Independent ≤ spanning)**
> If $S, T \subseteq V$ are finite, $S$ is linearly independent and $T$ spans $V$, then $|S| \leq |T|$.

> [!proof]- Proof
> Let $S = \{u_1, \dots, u_m\}$, $T = \{v_1, \dots, v_n\}$. Since $\langle T\rangle = V$, $u_1 \in \langle v_1, \dots, v_i\rangle$ for some minimal $i$, so $u_1 \notin \langle v_1, \dots, v_{i-1}\rangle$. Steinitz gives $\langle v_1, \dots, v_i\rangle = \langle u_1, v_1, \dots, v_{i-1}\rangle$, and hence
> $$V = \langle u_1, v_1, \dots, v_{i-1}, v_{i+1}, \dots, v_n\rangle.$$
> Relabel so $u_1$ replaced $v_1$: $T_1 = \{u_1, v_2, \dots, v_n\}$ spans $V$. Inductively $T_k = \{u_1, \dots, u_k, v_{k+1}, \dots, v_n\}$ spans $V$. At each stage $u_{k+1} \in \langle T_k\rangle$ but $u_{k+1} \notin \langle u_1, \dots, u_k\rangle$ (independence), so it replaces some $v_j$. The process only stops when $S$ is used up, so $m \leq n$. $\square$

> **Corollary 129**
> In a finite-dimensional space, all bases are finite and have the same size.

> [!proof]- Proof
> Let $B$ be a finite basis. Any finite subset of another basis $S$ is independent, so has size $\leq |B|$ (Theorem 128); hence $S$ is finite and $|S| \leq |B|$. Swapping roles, $|B| \leq |S|$. $\square$

> **Definition 130 (Dimension)**
> The **dimension** $\dim V$ of a finite-dimensional space is the size of any basis.

> **Definition 131 (Row rank, again)**
> The **row rank** of a matrix is $\dim \text{Row}(A)$. The non-zero rows of its RRE form are a basis of the row space (independent by Prop 117(a), same row space by 117(e)), so this agrees with Definition 123.

## Subspaces and Dimension

The four facts proved here:
- a spanning set contains a basis;
- an independent set extends to a basis;
- a basis is a **maximal** independent set;
- a basis is a **minimal** spanning set.

> **Proposition 132**
> A finite spanning set $S$ contains a basis.

> [!proof]- Proof
> Take a largest independent $T \subseteq S$. If $\langle T\rangle \neq V = \langle S\rangle$, there's $v \in S \setminus \langle T\rangle$, and $T \cup \{v\} \subseteq S$ is independent (Lemma 102) and bigger. Contradiction. $\square$

**Remark 133:** so a space with a finite spanning set has a basis. What happens without one is a question for Part B Set Theory (Axiom of Choice).

> **Proposition 134**
> If $U \leqslant V$ and $V$ is finite-dimensional, then $U$ is finite-dimensional, $\dim U \leq \dim V$, and $\dim U = \dim V \implies U = V$.

> [!proof]- Proof
> Independent subsets of $V$ have size $\leq n = \dim V$. Take a largest independent $S \subseteq U$; if $u \in U \setminus \langle S\rangle$, then $S \cup \{u\}$ is a bigger independent set (Lemma 102). So $S$ is a basis of $U$ and $|S| \leq n$.
> If $\dim U = \dim V$ but $v \in V \setminus U$, adding $v$ to a basis of $U$ gives $\dim V + 1$ independent vectors in $V$. Contradiction. $\square$

> **Proposition 135 (Extending to a basis)**
> In a finite-dimensional $V$, any independent $S$ is contained in a basis.

> [!proof]- Proof
> If $\langle S\rangle \neq V$, add $u_1 \notin \langle S\rangle$: still independent (Lemma 102). Repeat. This must stop, since independent sets have at most $\dim V$ elements, and it stops exactly when the set spans. $\square$

> **Corollary 136** A maximal linearly independent subset of a finite-dimensional space is a basis.

> **Corollary 137** A minimal spanning subset of a finite-dimensional space is a basis.

> [!proof]- Proofs
> **136** If $\langle S\rangle \neq V$, adding a vector outside keeps $S$ independent (Lemma 102), contradicting maximality.
> **137** If $S$ is dependent, some $v \in S$ is a combination of $S \setminus \{v\}$, so $S \setminus \{v\}$ still spans, contradicting minimality. $\square$

**How to find a basis of $\langle S\rangle$ for $S \subseteq \mathbb{R}^n$:** put the vectors as rows of a matrix and row-reduce; the non-zero rows of the RRE form are a basis.

> [!example]- Example 138
> $S = \{(0,1,2,3), (1,2,3,4), (2,3,4,5)\}$:
> $$A = \begin{pmatrix} 0 & 1 & 2 & 3 \\ 1 & 2 & 3 & 4 \\ 2 & 3 & 4 & 5 \end{pmatrix} \xrightarrow{\text{RRE}} \begin{pmatrix} 1 & 0 & -1 & -2 \\ 0 & 1 & 2 & 3 \\ 0 & 0 & 0 & 0 \end{pmatrix},$$
> so $\{(1,0,-1,-2), (0,1,2,3)\}$ is a basis of $\langle S\rangle$, and $\dim\langle S\rangle = 2$.

## The Dimension Formula

> **Theorem 139 (Dimension formula)**
> For subspaces $U, W$ of a finite-dimensional $V$:
> $$\dim(U + W) + \dim(U \cap W) = \dim U + \dim W.$$

> [!proof]- Proof
> Take a basis $v_1, \dots, v_m$ of $U \cap W$. Extend it (Prop 135) to bases $v_1, \dots, v_m, u_1, \dots, u_p$ of $U$ and $v_1, \dots, v_m, w_1, \dots, w_q$ of $W$. It suffices to show $S = \{v_i, u_j, w_k\}$ (with $m + p + q$ elements) is a basis of $U + W$.
> *Spanning:* $x = u + w$, and writing $u$, $w$ in their bases gives $x \in \langle S\rangle$.
> *Independent:* if $\sum\alpha_iv_i + \sum\beta_ju_j + \sum\gamma_kw_k = 0$, then $\sum\alpha_iv_i + \sum\beta_ju_j = -\sum\gamma_kw_k$ lies in $U \cap W$, so equals some $\sum\lambda_iv_i$. Then $\sum\gamma_kw_k + \sum\lambda_iv_i = 0$, and independence of $W$'s basis gives all $\gamma_k = 0$. Then independence of $U$'s basis gives all $\alpha_i, \beta_j = 0$. $\square$

Start from $U \cap W$, the smallest space involved: a basis of $V$ generally won't contain a basis of a subspace, but bases always extend upwards.

> [!example]- Example 140
> $\dim V = 10$, $\dim X = \dim Y = 6$. Since $\dim(X + Y) \leq 10$,
> $$\dim(X \cap Y) = 6 + 6 - \dim(X + Y) \geq 2,$$
> and every value $2 \leq \dim(X \cap Y) \leq 6$ is possible (exercise).

> **Definition 141 (Direct sum)**
> If $U \cap W = \{0_V\}$ and $U + W = V$, then $V$ is the **direct sum** of $U$ and $W$: $V = U \oplus W$.

> **Proposition 142 (Characterisations of direct sums)**
> For $U, W \leqslant V$ ($V$ finite-dimensional), these are equivalent:
> 1. $V = U \oplus W$;
> 2. every $v \in V$ is **uniquely** $u + w$ with $u \in U$, $w \in W$;
> 3. $\dim V = \dim U + \dim W$ and $V = U + W$;
> 4. $\dim V = \dim U + \dim W$ and $U \cap W = \{0_V\}$;
> 5. a basis of $U$ together with a basis of $W$ is a basis of $V$.

> [!proof]- Proof (hint)
> Exercise. (1) ⇔ (2) is straight from the definition; use the dimension formula to link (1)/(2) with (3)/(4)/(5).

> [!note]- Remark 143 (more on direct sums)
> - $V = X_1 \oplus \dots \oplus X_k$ if every $v$ is uniquely $x_1 + \dots + x_k$ with $x_i \in X_i$; this generalises (2).
> - That is an **internal** direct sum. The **external direct sum** $V_1 \oplus \dots \oplus V_k$ of arbitrary spaces is the Cartesian product $V_1 \times \dots \times V_k$ with componentwise operations:
> $$(v_1, \dots, v_k) + (w_1, \dots, w_k) = (v_1 + w_1, \dots, v_k + w_k), \qquad \alpha(v_1, \dots, v_k) = (\alpha v_1, \dots, \alpha v_k).$$
