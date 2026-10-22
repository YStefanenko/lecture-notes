Linear Algebra I, Chapter 7. Back to [[LA1]]. Builds on [[LA1 - Linear Transformations]].

**Linear maps are to matrices as vectors are to coordinate vectors.** Choose bases and a linear map becomes a matrix; change the bases and the matrix changes too.

## Representing Linear Maps with Matrices

> **Definition 169 (Matrix of a linear map)**
> Let $V$ have ordered basis $\mathcal V = (v_1, \dots, v_n)$ and $W$ have ordered basis $\mathcal W = (w_1, \dots, w_m)$. The **matrix for $T : V \to W$ with respect to $\mathcal V$ and $\mathcal W$** is the $m \times n$ matrix ${}_\mathcal{W}T_\mathcal{V} = (a_{ij})$ with
> $$T(v_i) = \sum_{k=1}^m a_{ki}w_k.$$
> It sends the coordinate vector of $v$ to the coordinate vector of $Tv$.

- **Remark 170:** well-defined, since each $T(v_i)$ has unique coordinates in $\mathcal W$.
- **Remark 171:** **column $i$ = coordinates of $T(v_i)$.** That's what matrices always do: $A\mathbf e_i^T$ is the $i$th column of $A$.
- **Remark 172:** identifying $V \cong \mathbb{F}^n_{\text{col}}$ and $W \cong \mathbb{F}^m_{\text{col}}$ via the bases turns $T$ into $L_A$.
- **Remark 173:** the bases are **ordered**: reordering them changes the matrix.
- **Remark 174:** for $T : V \to V$ with the same basis on both sides, we speak of **the matrix of $T$ with respect to this basis**.

> [!example]- Examples 175 – 176 ($T(x, y, z) = (0, x, y)$)
> **175** With the standard basis $\mathcal E = (\mathbf i, \mathbf j, \mathbf k)$: $T\mathbf i = \mathbf j$, $T\mathbf j = \mathbf k$, $T\mathbf k = \mathbf 0$, so
> $${}_\mathcal{E}T_\mathcal{E} = \begin{pmatrix} 0 & 0 & 0 \\ 1 & 0 & 0 \\ 0 & 1 & 0 \end{pmatrix}, \qquad ({}_\mathcal{E}T_\mathcal{E})^3 = 0 = {}_\mathcal{E}(T^3)_\mathcal{E}.$$
> **176** With $\mathcal F = (\mathbf f_1, \mathbf f_2, \mathbf f_3) = ((1,1,1), (1,1,0), (0,1,1))$:
> - $T\mathbf f_1 = T\mathbf f_2 = (0,1,1)$, $T\mathbf f_3 = (0,0,1)$, so ${}_\mathcal{E}T_\mathcal{F} = \begin{pmatrix} 0 & 0 & 0 \\ 1 & 1 & 0 \\ 1 & 1 & 1 \end{pmatrix}$.
> - $T\mathbf i = (0,1,0) = -\mathbf f_1 + \mathbf f_2 + \mathbf f_3$, $T\mathbf j = (0,0,1) = \mathbf f_1 - \mathbf f_2$, $T\mathbf k = \mathbf 0$, so ${}_\mathcal{F}T_\mathcal{E} = \begin{pmatrix} -1 & 1 & 0 \\ 1 & -1 & 0 \\ 1 & 0 & 0 \end{pmatrix}$.
> - $T\mathbf f_1 = T\mathbf f_2 = \mathbf f_3$, $T\mathbf f_3 = \mathbf f_1 - \mathbf f_2$, so ${}_\mathcal{F}T_\mathcal{F} = \begin{pmatrix} 0 & 0 & 1 \\ 0 & 0 & -1 \\ 1 & 1 & 0 \end{pmatrix}$.

> **Proposition 177**
> 1. ${}_\mathcal{W}0_\mathcal{V} = 0_{m \times n}$ for any bases.
> 2. ${}_\mathcal{V}\text{id}_\mathcal{V} = I_n$ for any basis $\mathcal V$.
> 3. ${}_\mathcal{W}(\alpha S + \beta T)_\mathcal{V} = \alpha\,{}_\mathcal{W}S_\mathcal{V} + \beta\,{}_\mathcal{W}T_\mathcal{V}$.
> 
> *(Exercises.)*

> **Theorem 178 (Composition ↔ product)**
> For $S : U \to V$ and $T : V \to W$ with ordered bases $\mathcal U, \mathcal V, \mathcal W$: if $A = {}_\mathcal{V}S_\mathcal{U}$ and $B = {}_\mathcal{W}T_\mathcal{V}$, then
> $$BA = {}_\mathcal{W}(TS)_\mathcal{U}.$$

> [!proof]- Proof
> $S(u_i) = \sum_j a_{ji}v_j$ and $T(v_j) = \sum_k b_{kj}w_k$, so
> $$(T \circ S)(u_i) = \sum_j a_{ji}T(v_j) = \sum_j a_{ji}\sum_k b_{kj}w_k = \sum_k\Big(\sum_j b_{kj}a_{ji}\Big)w_k = \sum_k(BA)_{ki}w_k. \ \square$$

**Remark 179:** this is *why* matrix multiplication is defined the way it is (see [[LA1 - Matrix Algebra]]).

> **Corollary 181 (Associativity, painlessly)**
> $A(BC) = (AB)C$ for $A \in M_{m \times n}$, $B \in M_{n \times p}$, $C \in M_{p \times q}$.

> [!proof]- Proof (Remark 180)
> With standard bases, $A, B, C$ are the matrices of $L_A, L_B, L_C$. By Theorem 178, $A(BC)$ and $(AB)C$ are the matrices of $L_A \circ (L_B \circ L_C)$ and $(L_A \circ L_B) \circ L_C$, which are equal because composition of functions is associative. $\square$

> **Corollary 182**
> If $T : V \to V$ is invertible with matrix $A$ (same basis both sides), then $A$ is invertible and $A^{-1}$ is the matrix of $T^{-1}$. *(Exercise.)*

## Change of Basis

**Question:** how are two matrices of the same map, with respect to different bases, related?

> [!example]- Example 183
> $T(x, y) = (2x + y, 3x - 2y)$. With the standard basis, ${}_\mathcal{E}T_\mathcal{E} = \begin{pmatrix} 2 & 1 \\ 3 & -2 \end{pmatrix}$.
> With $\mathcal F = (\mathbf f_1, \mathbf f_2) = ((1,-2), (-2,5))$: $T\mathbf f_1 = (0,7) = 14\mathbf f_1 + 7\mathbf f_2$ and $T\mathbf f_2 = (1,-16) = -27\mathbf f_1 - 14\mathbf f_2$, so ${}_\mathcal{F}T_\mathcal{F} = \begin{pmatrix} 14 & -27 \\ 7 & -14 \end{pmatrix}$.
> By Theorem 178, ${}_\mathcal{F}T_\mathcal{F} = ({}_\mathcal{F}I_\mathcal{E})({}_\mathcal{E}T_\mathcal{E})({}_\mathcal{E}I_\mathcal{F})$. The **change of basis matrix** ${}_\mathcal{E}I_\mathcal{F}$ represents the identity: it converts $\mathcal F$-coordinates into $\mathcal E$-coordinates of the *same* vector. Since $\mathbf f_1 = \mathbf e_1 - 2\mathbf e_2$ and $\mathbf f_2 = -2\mathbf e_1 + 5\mathbf e_2$,
> $${}_\mathcal{E}I_\mathcal{F} = \begin{pmatrix} 1 & -2 \\ -2 & 5 \end{pmatrix}, \qquad {}_\mathcal{F}I_\mathcal{E} = \begin{pmatrix} 1 & -2 \\ -2 & 5 \end{pmatrix}^{-1} = \begin{pmatrix} 5 & 2 \\ 2 & 1 \end{pmatrix},$$
> and indeed $\begin{pmatrix} 5 & 2 \\ 2 & 1 \end{pmatrix}\begin{pmatrix} 2 & 1 \\ 3 & -2 \end{pmatrix}\begin{pmatrix} 1 & -2 \\ -2 & 5 \end{pmatrix} = \begin{pmatrix} 16 & 1 \\ 7 & 0 \end{pmatrix}\begin{pmatrix} 1 & -2 \\ -2 & 5 \end{pmatrix} = \begin{pmatrix} 14 & -27 \\ 7 & -14 \end{pmatrix}$.

> **Corollary 184 (Change of basis theorem)**
> For $T : V \to W$, with ordered bases $\mathcal V, \mathcal V'$ of $V$ and $\mathcal W, \mathcal W'$ of $W$:
> $${}_{\mathcal W'}T_{\mathcal V'} = ({}_{\mathcal W'}I_\mathcal{W})({}_\mathcal{W}T_\mathcal{V})({}_\mathcal{V}I_{\mathcal V'}).$$
> *(Immediate from Theorem 178.)*

> **Corollary 185 (Change of basis, version 2)**
> For $T : V \to V$ with bases $\mathcal V, \mathcal V'$: ${}_{\mathcal V'}T_{\mathcal V'} = ({}_{\mathcal V'}I_\mathcal{V})({}_\mathcal{V}T_\mathcal{V})({}_\mathcal{V}I_{\mathcal V'})$. With $A = {}_{\mathcal V'}T_{\mathcal V'}$, $B = {}_\mathcal{V}T_\mathcal{V}$, $P = {}_\mathcal{V}I_{\mathcal V'}$:
> $$A = P^{-1}BP.$$

> **Definition 186 (Similar matrices)**
> $A, B \in M_{n \times n}(\mathbb{F})$ are **similar** if $A = P^{-1}BP$ for some invertible $P$. Similarity is an equivalence relation.

**Remark 187:** two matrices of the same $T : V \to V$ in different bases are similar.

**Properties of linear maps are basis-independent (Remark 188).** If $A = P^{-1}BP$:
- $A$ is invertible iff $B$ is;
- $\text{trace}\,A = \text{trace}\,B$ (since $\text{trace}(MN) = \text{trace}(NM)$);
- any polynomial identity (e.g. $A^2 = A$) holds for $A$ iff for $B$;
- $\det A = \det B$, and they have the same eigenvalues (Linear Algebra II).

So the invertibility, trace and determinant of a *linear map* make sense. Its **transpose** doesn't: $A^T \neq P^{-1}B^TP$ in general (it is true if $P$ is orthogonal; this is where adjoints come in, in second year).

## Matrices and Rank

**Remark 189:** $\text{Col}(A) = \text{Row}(A^T)$, so $\text{colrank}(A) = \text{rowrank}(A^T)$, and vice versa.

> **Lemma 190**
> $(A \mid \mathbf b)$ is consistent iff $\text{Col}(A \mid \mathbf b) = \text{Col}(A)$.

> [!proof]- Proof
> Consistent $\iff A\mathbf x = x_1\mathbf c_1 + \dots + x_n\mathbf c_n = \mathbf b$ for some $\mathbf x \iff \mathbf b \in \text{Col}(A) \iff \text{Col}(A|\mathbf b) = \text{Col}(A)$. $\square$

> **Theorem 191 (Row rank = column rank)**
> The column rank of a matrix equals its row rank.

> [!proof]- Proof (induction on the number of columns)
> $n = 1$: a non-zero column has both ranks $1$ (it reduces to $\mathbf e_1^T$); the zero column has both $0$.
> Step: view an $m \times (n+1)$ matrix as $(A \mid \mathbf b)$.
> - If consistent: $\text{colrank}(A|\mathbf b) = \text{colrank}(A) = \text{rowrank}(A) = \text{rowrank}(A|\mathbf b)$ (Lemma 190, induction, Remark 45).
> - If inconsistent: $\mathbf b \notin \text{Col}(A)$ adds one to the column rank, and the row $(0 \cdots 0 \mid 1)$ adds one to the row rank, so both go up by $1$. $\square$

> **Theorem 192 (Second proof, via factorisation)**
> Let $P = QR$ with $P$ $k \times l$, $Q$ $k \times m$, $R$ $m \times l$.
> 1. $\text{rowrank}(P) \leq m$.
> 2. If $p = \text{rowrank}(P)$, then $P$ is a product of a $k \times p$ and a $p \times l$ matrix.
> 3. Row rank = column rank.

> [!proof]- Proof
> (1) $\text{Row}(P) = \text{Row}(QR) \leqslant \text{Row}(R)$ (Prop 117(c)), so $\text{rowrank}(P) \leq \text{rowrank}(R) \leq m$.
> (2) $EP = \text{RRE}(P)$ with $E$ invertible, so $P = E^{-1}\text{RRE}(P)$. The last $k - p$ rows of $\text{RRE}(P)$ are zero, so $P = \tilde E\tilde P$ with $\tilde E$ the first $p$ columns of $E^{-1}$ and $\tilde P$ the first $p$ rows of $\text{RRE}(P)$.
> (3) By (1) and (2), $\text{rowrank}(P)$ is the least $p$ with $P = (k \times p)(p \times l)$. Transposing, $P^T = R^TQ^T$ is $(l \times p)(p \times k)$, so $\text{rowrank}(P^T) = p$ too, and $\text{rowrank}(P^T) = \text{colrank}(P)$. $\square$
