Linear Algebra I, Chapter 1.2. Back to [[LA1]].

> **Definitions 9 & 11 (Matrix, entries)**
> An **$m \times n$ matrix** is an array of real numbers in $m$ **rows** and $n$ **columns**. Its **entries** are $a_{ij}$ (row $i$, column $j$). The $i$th row is $(a_{i1}, \dots, a_{in})$ and the $j$th column is $(a_{1j}, \dots, a_{mj})^T$.

**Notation 12:** $M_{mn}$ is the set of real $m \times n$ matrices. Row vectors: $M_{1n} = \mathbb{R}^n$. Column vectors: $M_{n1} = \mathbb{R}^n_{\text{col}}$.

> [!example]- Examples 10 & 13
> For $A = \begin{pmatrix} 1 & 2 & -3 \\ \sqrt2 & \pi & 0 \end{pmatrix}$: second row $(\sqrt2\ \ \pi\ \ 0)$, third column $\begin{pmatrix} -3 \\ 0 \end{pmatrix}$, $a_{23} = 0$, $a_{12} = 2$.

## Addition and Scalar Multiplication

> **Definition 14 (Addition)**
> Only for matrices of the **same size**: $(A + B)_{ij} = a_{ij} + b_{ij}$.

> **Definition 17 (Zero matrix)** $0_{mn}$ is the $m \times n$ matrix of zeros; $A + 0_{mn} = A$.

> **Definition 18 (Scalar multiplication)** $(kA)_{ij} = k\,a_{ij}$.

> [!example]- Examples 15 & 19
> **15** With $A = \begin{pmatrix} 1 & 2 \\ -1 & 0 \end{pmatrix}$, $B = \begin{pmatrix} 1 & 2 & 3 \\ 3 & 2 & 1 \end{pmatrix}$, $C = \begin{pmatrix} 1 & -1 \\ 1 & -1 \end{pmatrix}$, only $A + C = C + A = \begin{pmatrix} 2 & 1 \\ 0 & -1 \end{pmatrix}$ makes sense ($B$ is a different size).
> **19** $A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \end{pmatrix}$, $B = \begin{pmatrix} 0 & -2 \\ 5 & 1 \end{pmatrix}$: $2(A + B) = \begin{pmatrix} 2 & 0 \\ 16 & 10 \end{pmatrix} = 2A + 2B$ (the distributive law).

**Remarks 16 & 20:** addition is commutative and associative, and
$$A + 0 = A,\quad A + (-A) = 0,\quad 0A = 0,\quad 1A = A,\quad (\lambda + \mu)A = \lambda A + \mu A,\quad \lambda(A + B) = \lambda A + \lambda B,\quad \lambda(\mu A) = (\lambda\mu)A.$$
So $M_{mn}$ is a real vector space.

## Matrix Multiplication

> **Definition 21 (Matrix multiplication)**
> For $A$ ($m \times n$) and $B$ ($n \times q$; **columns of $A$ = rows of $B$**), $C = AB$ is $m \times q$ with
> $$c_{ij} = \sum_{k=1}^n a_{ik}b_{kj}. \tag{1.12}$$
> Equivalently, the $(i, j)$ entry of $AB$ is (row $i$ of $A$) $\cdot$ (column $j$ of $B$).

**Why this rule? (Remark 22)** $A$ gives a map $L_A : \mathbb{R}^n_{\text{col}} \to \mathbb{R}^m_{\text{col}}$, $\mathbf v \mapsto A\mathbf v$, and $L_{AB} = L_A \circ L_B$. **Matrix multiplication is composition** of linear maps: do $L_B$ first, then $L_A$. See Theorem 178 in [[LA1 - Matrices of Linear Maps]].

> [!example]- Example 23 (products of $A$, $B$, $C$ above)
> $$AC = \begin{pmatrix} 3 & -3 \\ -1 & 1 \end{pmatrix}, \quad AA = \begin{pmatrix} -1 & 2 \\ -1 & -2 \end{pmatrix}, \quad AB = \begin{pmatrix} 7 & 6 & 5 \\ -1 & -2 & -3 \end{pmatrix},$$
> $$CA = \begin{pmatrix} 2 & 2 \\ 2 & 2 \end{pmatrix}, \quad CB = \begin{pmatrix} -2 & 0 & 2 \\ -2 & 0 & 2 \end{pmatrix}, \quad CC = \begin{pmatrix} 0 & 0 \\ 0 & 0 \end{pmatrix}.$$
> Note $AC \neq CA$, and $CC = 0$ although $C \neq 0$.

> **Definition 24 (Identity matrix, Kronecker delta)**
> $I_n$ is the $n \times n$ matrix with entries $\delta_{ij} = 1$ if $i = j$ and $0$ otherwise (the **Kronecker delta**).

**Remark 25 (Sifting property):** $\sum_{i=1}^n x_i\delta_{ik} = x_k$.

> **Proposition 26 (Properties of matrix multiplication)**
> 1. $A0_{np} = 0_{mp}$, $0_{lm}A = 0_{ln}$, $AI_n = A$, $I_mA = A$.
> 2. **Not commutative:** $AB \neq BA$ in general (even when both exist and are the same size).
> 3. **Associative:** $A(BC) = (AB)C$.
> 4. **Distributive:** $A(B + C) = AB + AC$ and $(A + B)C = AC + BC$.
> 5. $MN = 0$ does **not** imply $M = 0$ or $N = 0$ (e.g. $CC = 0$).

> [!proof]- Proof
> (1) Zero rows/columns give zero dot products; by sifting, $(AI_n)_{ij} = \sum_k a_{ik}\delta_{kj} = a_{ij}$, and similarly for $I_mA$.
> (2) $AC \neq CA$ above; and if $A$ is $m \times n$ and $B$ is $n \times p$, $BA$ needn't even exist.
> (3) $((AB)C)_{ij} = \sum_r\left(\sum_s a_{is}b_{sr}\right)c_{rj}$ and $(A(BC))_{ij} = \sum_s a_{is}\left(\sum_r b_{sr}c_{rj}\right)$, equal since finite sums can be swapped.
> (4) Exercise. $\square$

> **Definition 27 (Pre- and postmultiplication)**
> To **premultiply** $M$ by $A$ means $AM$ (on the left); to **postmultiply** means $MA$ (on the right).

**Notation 28:** for square $A$: $A^n = A\cdots A$, $A^0 = I$, $A^mA^n = A^{m+n}$, and for $p(x) = \sum a_k x^k$, $p(A) = \sum a_k A^k$ (constant term $a_0 I$).

> [!example]- Example 29 (square roots of matrices are complicated)
> $A = \begin{pmatrix} \cos\alpha & \sin\alpha \\ \sin\alpha & -\cos\alpha \end{pmatrix}$ satisfies $A^2 = I_2$ for every $\alpha$: infinitely many square roots of $I_2$.
> $B = \begin{pmatrix} 0 & 1 \\ 0 & 0 \end{pmatrix}$ has **no** square root: if $\begin{pmatrix} a & b \\ c & d \end{pmatrix}^2 = \begin{pmatrix} a^2 + bc & b(a+d) \\ c(a+d) & bc + d^2 \end{pmatrix} = B$, then $b(a + d) = 1$ forces $a + d \neq 0$, so $c = 0$; then $a = d = 0$, contradiction.

## Inverses

$ax + by = e$, $cx + dy = f$ typically has the unique solution
$$\begin{pmatrix} x \\ y \end{pmatrix} = \frac{1}{ad - bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}\begin{pmatrix} e \\ f \end{pmatrix},$$
which fails when $ad - bc = 0$ (the two lines are parallel). Note $\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}\begin{pmatrix} a & b \\ c & d \end{pmatrix} = (ad - bc)I_2$.

> **Definition 30 (Inverse)**
> For square $A$, $B$ is an **inverse** if $BA = AB = I$. $A$ is **invertible** if it has one, otherwise **singular**.

> **Proposition 31 (Properties of inverses)**
> 1. **Uniqueness:** an inverse is unique; write $A^{-1}$.
> 2. **Product rule:** $(AB)^{-1} = B^{-1}A^{-1}$.
> 3. **Involution:** $(A^{-1})^{-1} = A$.

> [!proof]- Proof
> (1) If $B, C$ are both inverses: $C = IC = (BA)C = B(AC) = BI = B$.
> (2) Sheet 1, S3.
> (3) $A^{-1}A = AA^{-1} = I$, so $A$ is the inverse of $A^{-1}$. $\square$

> **Definition 32 (Left / right inverse)**
> For $m \times n$ $A$: $B$ is a **left inverse** if $BA = I_n$; $C$ is a **right inverse** if $AC = I_m$.

- If $m \neq n$, $A$ can't have both (proved later).
- For square matrices, $BA = I_n$ already implies $AB = I_n$ (Corollary 168).

> **Proposition 33 ($2 \times 2$ inverse)**
> $A = \begin{pmatrix} a & b \\ c & d \end{pmatrix}$ is invertible iff $ad - bc \neq 0$, and then
> $$A^{-1} = \frac{1}{ad - bc}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}.$$

> [!proof]- Proof
> If $ad - bc \neq 0$, check $AA^{-1} = A^{-1}A = I$. If $ad - bc = 0$, then $B = \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$ has $BA = 0$. If $C = A^{-1}$ existed, $0 = 0C = (BA)C = B(AC) = B$, so $a = b = c = d = 0$ and $A = 0$, contradicting $AC = I$. $\square$

$ad - bc = \det A$, the **determinant**. In general, $A$ is invertible iff $\det A \neq 0$ (Linear Algebra II, Remark 34).

**Notation 35 (standard basis of $M_{mn}$):** $E_{IJ}$ has a $1$ in entry $(I, J)$ and $0$ elsewhere; its $(i, j)$ entry is $\delta_{Ii}\delta_{Jj}$.

> **Theorem 36**
> If $A$ ($n \times n$) commutes with every $n \times n$ matrix, then $A = \lambda I_n$ for some $\lambda$.

> [!proof]- Proof
> $A$ commutes with every $E_{IJ}$. By sifting, $(AE_{IJ})_{ij} = a_{iI}\delta_{Jj}$ and $(E_{IJ}A)_{ij} = \delta_{Ii}a_{Jj}$, so
> $$a_{iI}\delta_{Jj} = \delta_{Ii}a_{Jj} \quad \text{for all } I, J, i, j.$$
> For $i \neq j$, take $I = J = i$: $0 = a_{ij}$, so off-diagonal entries vanish. Take $I = i$, $J = j$: $a_{ii} = a_{jj}$, so all diagonal entries equal some $\lambda$. Conversely $\lambda I$ commutes with everything. $\square$
