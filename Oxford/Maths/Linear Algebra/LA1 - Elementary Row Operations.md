Linear Algebra I, Chapter 1.1 and 1.3. Back to [[LA1]]. Matrix algebra itself is in [[LA1 - Matrix Algebra]].

## Linear Systems

> **Definition 1 (Linear system)**
> A **linear system** is $m$ simultaneous equations in $n$ real variables:
> $$a_{11}x_1 + \dots + a_{1n}x_n = b_1, \quad \dots, \quad a_{m1}x_1 + \dots + a_{mn}x_n = b_m. \tag{1.1}$$
> A vector $(x_1, \dots, x_n)$ satisfying all of them is a **solution**; the system is **consistent** if it has a solution. The **general solution** describes all solutions. We write the system as the **augmented matrix** $(A \mid \mathbf b)$ with $A = (a_{ij})$ and $\mathbf b = (b_i)$.

A linear system has **no, one, or infinitely many** solutions (Proposition 44).

> [!example]- Example 2 (ad hoc substitution)
> $3x + y - 2z = -2$, $x + y + z = 2$, $2x + 4y + z = 0$. Substituting $z = 2 - x - y$ gives $5x + 3y = 2$ and $x + 3y = -2$, so $x = 1$, $y = -1$, $z = 2$. Then check it really is a solution.
> 
> This doesn't scale to 1969 equations in 2021 unknowns, which is why we want a systematic method: **row reduction**.

> **Definition 3 (Elementary row operations, EROs)**
> 1. Swap two rows (equations).
> 2. Multiply a row by a **non-zero** scalar.
> 3. Add a multiple of one row to a **different** row.

> **Notation 4 (lecturer's own, not standard)**
> - $S_{ij}$: swap rows $i$ and $j$.
> - $M_i(\lambda)$: multiply row $i$ by $\lambda \neq 0$.
> - $A_{ij}(\lambda)$: add $\lambda \times$ row $i$ to row $j$ ($i \neq j$).

> [!example]- Example 5 (row-reducing Example 2)
> $$\left(\begin{array}{ccc|c} 3 & 1 & -2 & -2 \\ 1 & 1 & 1 & 2 \\ 2 & 4 & 1 & 0 \end{array}\right) \xrightarrow{S_{12}} \left(\begin{array}{ccc|c} 1 & 1 & 1 & 2 \\ 3 & 1 & -2 & -2 \\ 2 & 4 & 1 & 0 \end{array}\right) \xrightarrow[A_{13}(-2)]{A_{12}(-3)} \left(\begin{array}{ccc|c} 1 & 1 & 1 & 2 \\ 0 & -2 & -5 & -8 \\ 0 & 2 & -1 & -4 \end{array}\right)$$
> $$\xrightarrow{M_2(-1/2)} \left(\begin{array}{ccc|c} 1 & 1 & 1 & 2 \\ 0 & 1 & \frac52 & 4 \\ 0 & 2 & -1 & -4 \end{array}\right) \xrightarrow[A_{23}(-2)]{A_{21}(-1)} \left(\begin{array}{ccc|c} 1 & 0 & -\frac32 & -2 \\ 0 & 1 & \frac52 & 4 \\ 0 & 0 & -6 & -12 \end{array}\right)$$
> $$\xrightarrow{M_3(-1/6)} \left(\begin{array}{ccc|c} 1 & 0 & -\frac32 & -2 \\ 0 & 1 & \frac52 & 4 \\ 0 & 0 & 1 & 2 \end{array}\right) \xrightarrow[A_{31}(3/2)]{A_{32}(-5/2)} \left(\begin{array}{ccc|c} 1 & 0 & 0 & 1 \\ 0 & 1 & 0 & -1 \\ 0 & 0 & 1 & 2 \end{array}\right).$$
> So $x = 1$, $y = -1$, $z = 2$.
> 
> **Method (Remark 6):** column by column, get a leading 1 (swap or scale), then clear the rest of that column with $A_{ij}$ operations.

> [!example]- Example 7 (infinitely many / no solutions)
> **(a)** $x_1 - x_2 + x_3 + 3x_4 = 2$, $2x_1 - x_2 + x_3 + 2x_4 = 4$, $4x_1 - 3x_2 + 3x_3 + 8x_4 = 8$:
> $$\left(\begin{array}{cccc|c} 1 & -1 & 1 & 3 & 2 \\ 2 & -1 & 1 & 2 & 4 \\ 4 & -3 & 3 & 8 & 8 \end{array}\right) \to \left(\begin{array}{cccc|c} 1 & 0 & 0 & -1 & 2 \\ 0 & 1 & -1 & -4 & 0 \\ 0 & 0 & 0 & 0 & 0 \end{array}\right).$$
> The zero row means a redundant equation. Columns 3 and 4 have no leading entry, so set $x_3 = s$, $x_4 = t$:
> $$(x_1, x_2, x_3, x_4) = (2, 0, 0, 0) + s(0, 1, 1, 0) + t(1, 4, 0, 1),$$
> a plane in $\mathbb{R}^4$.
> 
> **(b)** $x_1 + x_2 + x_3 + x_4 = 4$, $2x_1 + 3x_2 - 2x_3 - 3x_4 = 1$, $x_1 + 5x_3 + 6x_4 = 1$ reduces to a row $(0\ 0\ 0\ 0 \mid -10)$, i.e. $0 = -10$. **No solutions.**

> [!example]- Example 8 (a parameter $\alpha$: all three cases)
> $x + z = -5$, $2x + \alpha y + 3z = -9$, $-x - \alpha y + \alpha z = \alpha^2$ reduces to
> $$\left(\begin{array}{ccc|c} 1 & 0 & 1 & -5 \\ 0 & \alpha & 1 & 1 \\ 0 & 0 & \alpha + 2 & \alpha^2 - 4 \end{array}\right).$$
> - $\alpha \neq 0, -2$: unique solution $x = -\alpha - 3$, $y = 3/\alpha - 1$, $z = \alpha - 2$.
> - $\alpha = 0$: a row reduces to $(0\ 0\ 0 \mid 1)$, so **inconsistent**.
> - $\alpha = -2$: infinitely many solutions $x = -5 - t$, $y = (t - 1)/2$, $z = t$.
> 
> Which EROs are allowed (dividing by $\alpha$ or $\alpha + 2$) depends on the parameter, so treat the special values separately.

## Elementary Matrices

> **Proposition 37 (Elementary matrices)**
> Applying $S_{IJ}$, $M_I(\lambda)$ or $A_{IJ}(\lambda)$ to $A$ is the same as premultiplying $A$ by the **elementary matrix** obtained by doing that ERO to the identity:
> - $S_{IJ}$: the identity with rows $I$ and $J$ swapped;
> - $M_I(\lambda)$: the identity with $(I, I)$ entry $\lambda$;
> - $A_{IJ}(\lambda)$: the identity with an extra $\lambda$ in the $(J, I)$ entry.
> 
> *(Proof: exercise.)*

> [!example]- Example 38 ($m = 3$)
> $$S_{21} = \begin{pmatrix} 0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{pmatrix}, \quad M_3(7) = \begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 7 \end{pmatrix}, \quad A_{31}(-2) = \begin{pmatrix} 1 & 0 & -2 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix}.$$

> **Proposition 39** Elementary matrices are invertible:
> $$S_{ij}^{-1} = S_{ij}, \qquad A_{ij}(\lambda)^{-1} = A_{ij}(-\lambda), \qquad M_i(\lambda)^{-1} = M_i(\lambda^{-1}).$$

> **Corollary 40 (EROs don't change the solutions)**
> If $E$ is an elementary matrix, $\mathbf x$ solves $(A \mid \mathbf b)$ iff it solves $(EA \mid E\mathbf b)$.

> [!proof]- Proof
> $A\mathbf x = \mathbf b \Rightarrow EA\mathbf x = E\mathbf b$ (premultiply by $E$), and conversely premultiply by $E^{-1}$. The key point is that $E$ is invertible. $\square$

## Reduced Row Echelon Form

> **Definition 41 (RRE form)**
> $A$ is in **reduced row echelon form** if
> 1. the first non-zero entry of each non-zero row is $1$ (a **leading 1**);
> 2. a column containing a leading 1 has all other entries $0$;
> 3. each leading 1 is to the right of the leading 1s in the rows above;
> 4. zero rows are at the bottom.

> **Definition 42 (Row reduction)**
> Using EROs to reach RRE form is **row reduction**, also called **Gauss–Jordan elimination**.

> [!example]- Example 43 (which are RRE?)
> In RRE form:
> $$\begin{pmatrix} 0 & 1 & 2 & 0 & -4 \\ 0 & 0 & 0 & 1 & \pi \\ 0 & 0 & 0 & 0 & 0 \end{pmatrix}, \quad \begin{pmatrix} 1 & 0 & \sqrt2 & 0 \\ 0 & 1 & 2 & 0 \\ 0 & 0 & 0 & 1 \end{pmatrix}, \quad \begin{pmatrix} 1 & 0 \\ 0 & 1 \\ 0 & 0 \end{pmatrix}.$$
> Not RRE: $\begin{pmatrix} 1 & 2 \\ 0 & 1 \\ 0 & 0 \end{pmatrix}$ (column 2 has a leading 1 but also a $2$) and $\begin{pmatrix} 1 & 0 & 0 & \sqrt3 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & 2 & 1 \end{pmatrix}$ (row 3's leading entry isn't 1).

> **Proposition 44 (Solving systems in RRE form)**
> Let $(A \mid \mathbf b)$ be in RRE form, a system of $m$ equations in $n$ variables.
> 1. **No solutions** iff the last non-zero row of $(A \mid \mathbf b)$ is $(0\ \cdots\ 0 \mid 1)$.
> 2. **Unique solution** iff the non-zero rows of $A$ form $I_n$ (so needs $m \geq n$).
> 3. **Infinitely many solutions** iff $(A \mid \mathbf b)$ has as many non-zero rows as $A$, and not every column of $A$ has a leading 1. The solutions need $k$ parameters, where $k$ is the number of columns without a leading 1.

> [!proof]- Proof
> A row $(0 \cdots 0 \mid 1)$ means $0 = 1$: inconsistent. In RRE form that's the only way $(A \mid \mathbf b)$ can have more non-zero rows than $A$.
> 
> Otherwise both have $r$ non-zero rows, so there are $r$ leading 1s and $k = n - r$ columns without one. Renumbering variables so the leading 1s are in the first $r$ columns, the system reads
> $$x_1 + a_{1(r+1)}x_{r+1} + \dots + a_{1n}x_n = b_1, \quad \dots, \quad x_r + a_{r(r+1)}x_{r+1} + \dots + a_{rn}x_n = b_r.$$
> Assign parameters to $x_{r+1}, \dots, x_n$ and read off $x_1, \dots, x_r$: every choice gives a solution, and every solution arises this way. So there's a $k$-parameter family if $n > r$, and a unique solution if $r = n$ (then the non-zero rows of $A$ are $I_n$). $\square$

**Remark 45:** an RRE system is consistent iff $(A \mid \mathbf b)$ has as many non-zero rows as $A$; then assign parameters to the columns without leading 1s.

> [!example]- Example 46 (reading off solutions)
> $$\left(\begin{array}{cccc|c} 1 & -2 & 0 & 2 & 3 \\ 0 & 0 & 1 & 1 & -2 \\ 0 & 0 & 0 & 0 & 1 \end{array}\right) \text{ none}, \qquad \left(\begin{array}{ccc|c} 1 & 0 & 0 & 2 \\ 0 & 1 & 0 & -1 \\ 0 & 0 & 1 & 3 \\ 0 & 0 & 0 & 0 \end{array}\right) \text{ unique},$$
> $$\left(\begin{array}{cccc|c} 1 & 2 & 0 & 0 & 3 \\ 0 & 0 & 1 & 0 & 2 \\ 0 & 0 & 0 & 1 & 1 \end{array}\right) \text{ gives } (3 - 2s, s, 2, 1), \qquad \left(\begin{array}{cccc|c} 1 & -2 & 0 & 2 & 3 \\ 0 & 0 & 1 & 1 & -2 \\ 0 & 0 & 0 & 0 & 0 \end{array}\right) \text{ gives } (3 + 2s - 2t, s, -2 - t, t).$$

> **Theorem 47 (Existence of RRE form)**
> Every $m \times n$ matrix can be reduced by EROs to RRE form.

> [!proof]- Proof (induction on rows)
> A $1 \times n$ matrix is zero or becomes RRE after dividing by its leading entry. Suppose it's true for fewer than $m$ rows. If $A \neq 0$, take the first column $\mathbf c_j$ with a non-zero entry $\alpha$; swap that row to the top and divide by $\alpha$, making the $(1, j)$ entry $1$. Clear the rest of column $j$ with $A_{1i}(-\tilde a_{ij})$, so $\mathbf c_j = \mathbf e_1^T$. The bottom-right $(m-1) \times (n-j)$ block $B$ can be put into RRE form by induction (same EROs on the bottom $m - 1$ rows). Finally clear any entries of row 1 above leading 1s of $\text{RRE}(B)$ using $A_{l1}(-\tilde a_{1k})$. $\square$

RRE form is also **unique**: see Theorem 122 in [[LA1 - Span, Independence and Bases]].
