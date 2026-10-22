Linear Algebra I, Chapter 2. Back to [[LA1]]. Builds on [[LA1 - Matrix Algebra]].

> **Definition 48 (Square, diagonal)**
> A **square** matrix has as many rows as columns. Its **diagonal** is $a_{11}, \dots, a_{nn}$. A **diagonal** matrix is square with all off-diagonal entries zero; $\text{diag}(c_1, \dots, c_n)$ has $(i, i)$ entry $c_i$.

> **Definition 49 (Transpose)**
> For $m \times n$ $A$, the **transpose** $A^T$ is the $n \times m$ matrix with $(A^T)_{ij} = a_{ji}$.

> **Proposition 50 (Properties of transpose)**
> 1. $(A + B)^T = A^T + B^T$ and $(\lambda A)^T = \lambda A^T$.
> 2. **Product rule:** $(AB)^T = B^TA^T$.
> 3. **Involution:** $(A^T)^T = A$.
> 4. **Inverse rule:** $A$ is invertible iff $A^T$ is, and $(A^T)^{-1} = (A^{-1})^T$.
> 
> *(Sheet 2, Ex 3.)*

> **Definition 51 (Special square matrices)**
> $A$ is
> - **symmetric** if $A^T = A$;
> - **skew-symmetric** (antisymmetric) if $A^T = -A$;
> - **upper triangular** if $a_{ij} = 0$ for $i > j$ (zero below the diagonal); **strictly** if also zero on it ($i \geq j$);
> - **lower triangular** if $a_{ij} = 0$ for $i < j$ (zero above); **strictly** if $i \leq j$;
> - **triangular** if upper or lower triangular.

> [!example]- Example 52
> $A = \begin{pmatrix} 1 & 2 \\ 0 & 3 \end{pmatrix}$ is upper triangular, so $A^T = \begin{pmatrix} 1 & 0 \\ 2 & 3 \end{pmatrix}$ is lower triangular. $C = \begin{pmatrix} 0 & 1 \\ -1 & 0 \end{pmatrix}$ and $C^T$ are skew-symmetric. $D = \text{diag}(1, 2, 3)$ is diagonal, hence symmetric and both upper and lower triangular. For $B = \begin{pmatrix} 1 & 0 \\ 2 & -1 \\ 1 & -1 \end{pmatrix}$, $B^T = \begin{pmatrix} 1 & 2 & 1 \\ 0 & -1 & -1 \end{pmatrix}$.

## Finding Inverses with EROs

> **Algorithm 53 (Determining invertibility)**
> Row-reduce the $n \times 2n$ matrix $(A \mid I_n)$, applying each ERO to both halves, until it becomes $(R \mid P)$ with $R$ in RRE form.
> - If $R = I_n$, then $A$ is invertible and $A^{-1} = P$.
> - If $R \neq I_n$, then $A$ is singular. (As soon as a zero row appears in the left half, $A$ is singular.)

> [!proof]- Proof
> If $E_1, \dots, E_k$ are the elementary matrices used, then $(R \mid P) = (E_k\cdots E_1A \mid E_k\cdots E_1)$, so $R = PA$. If $R = I_n$ then $PA = I$, and $P$ is invertible (a product of invertible matrices), so $A^{-1} = P$.
> If $R \neq I_n$, the square RRE matrix $R$ has a zero row, so $(1, 0, \dots, 0)(PA) = \mathbf 0$ for a suitable ordering of rows. If $A$ were invertible, postmultiplying by $A^{-1}P^{-1}$ would give $(1, 0, \dots, 0) = \mathbf 0$. Contradiction. $\square$

> [!example]- Example 54
> $$A = \begin{pmatrix} 1 & 2 & 1 \\ 2 & 1 & 0 \\ 1 & 3 & 1 \end{pmatrix}: \quad (A \mid I_3) \to \left(I_3 \;\middle|\; \begin{matrix} 1/2 & 1/2 & -1/2 \\ -1 & 0 & 1 \\ 5/2 & -1/2 & -3/2 \end{matrix}\right), \quad \text{so } A^{-1} = \begin{pmatrix} \frac12 & \frac12 & -\frac12 \\ -1 & 0 & 1 \\ \frac52 & -\frac12 & -\frac32 \end{pmatrix}.$$
> (EROs: $A_{12}(-2), A_{13}(-1)$, then $A_{31}(-2), A_{32}(3), S_{23}$, then $M_3(-1/2), A_{31}(-1)$.)
> 
> $$B = \begin{pmatrix} 1 & 3 & -1 & 0 \\ 0 & 2 & 1 & 1 \\ 3 & 1 & 2 & 1 \\ 0 & 1 & 5 & 3 \end{pmatrix}$$
> reduces (via $A_{13}(-3), S_{24}, A_{23}(8), A_{24}(-2), A_{34}(1/5)$) to a left half with a zero row, so $B$ is **singular**.

> [!note]- Remark 55 (computational cost)
> Multiplying two $n \times n$ matrices the naive way takes $n^3$ multiplications and $n^2(n-1)$ additions. Strassen (1969) found faster algorithms; how fast it can be done is an open problem in **computational complexity**.

## Orthogonal Matrices

> **Definition 56 (Orthogonal matrix)**
> An $n \times n$ matrix $A$ is **orthogonal** if $A^T = A^{-1}$.

> **Proposition 57**
> If $A, B$ are orthogonal $n \times n$ matrices:
> 1. $AB$ and $A^{-1}$ are orthogonal, so the orthogonal matrices form a group $O(n)$.
> 2. $A$ is orthogonal iff its columns (or rows) are $n$ mutually perpendicular unit vectors.
> 3. $A$ preserves the dot product: $A\mathbf x \cdot A\mathbf y = \mathbf x \cdot \mathbf y$.

> [!proof]- Proof of (1)
> $(AB)^T = B^TA^T = B^{-1}A^{-1} = (AB)^{-1}$, and $(A^{-1})^T = (A^T)^{-1} = (A^{-1})^{-1}$. $\square$

> **Proposition 58**
> $A$ is orthogonal iff $A\mathbf x \cdot A\mathbf y = \mathbf x \cdot \mathbf y$ for all $\mathbf x, \mathbf y \in \mathbb{R}^n_{\text{col}}$.

> [!proof]- Proof
> $\mathbf x \cdot \mathbf y = \mathbf x^T\mathbf y$, so the condition reads $\mathbf x^TA^TA\mathbf y = \mathbf x^T\mathbf y$. If $A^TA = I$ this holds. Conversely, with $\mathbf x = \mathbf e_i$, $\mathbf y = \mathbf e_j$: $(A^TA)_{ij} = \delta_{ij}$, so $A^TA = I_n$. $\square$

That's why orthogonal matrices matter in geometry: they are exactly the matrices that preserve lengths and angles. See [[LA1 - Inner Product Spaces]] for the general version.
