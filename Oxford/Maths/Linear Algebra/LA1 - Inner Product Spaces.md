Linear Algebra I, Chapter 8. Back to [[LA1]].

$\mathbb{R}^n$ has far more structure than a bare vector space: a canonical basis, and lengths and angles via the dot product. An **inner product** is the abstract version of the dot product, giving length and angle in any (real) vector space. Key uses: Fourier series and quantum theory.

## Bilinear Forms

> **Definition 193 (Bilinear form)**
> A **bilinear form** on $V$ is $B : V \times V \to \mathbb{F}$ that is linear in each variable:
> 1. $B(\alpha_1v_1 + \alpha_2v_2, v_3) = \alpha_1B(v_1, v_3) + \alpha_2B(v_2, v_3)$;
> 2. $B(v_1, \alpha_2v_2 + \alpha_3v_3) = \alpha_2B(v_1, v_2) + \alpha_3B(v_1, v_3)$.

> [!example]- Examples 194 – 195
> **194** $B(\mathbf x, \mathbf y) = x_1y_1 + \dots + x_ny_n$ on $\mathbb{F}^n$: on $\mathbb{R}^n$ this is the dot product $\mathbf x \cdot \mathbf y$.
> **195** For any $A \in M_{n \times n}(\mathbb{F})$, $B(\mathbf x, \mathbf y) = \mathbf xA\mathbf y^T$ on row vectors (or $\mathbf x^TA\mathbf y$ on columns) is bilinear. The dot product is the case $A = I_n$ (identifying $1 \times 1$ matrices with scalars).

> **Definition 196 (Gram matrix)**
> The **Gram matrix** of $B$ with respect to $v_1, \dots, v_n$ is $(B(v_i, v_j)) \in M_{n \times n}(\mathbb{F})$.

> **Proposition 197**
> If $v_1, \dots, v_n$ is a basis with Gram matrix $A$, and $X = \sum x_iv_i$, $Y = \sum y_jv_j$, then
> $$B(X, Y) = \mathbf xA\mathbf y^T.$$

> [!proof]- Proof
> $B\left(\sum_i x_iv_i, \sum_j y_jv_j\right) = \sum_i x_i\sum_j y_jB(v_i, v_j) = \sum_{i,j}x_ia_{ij}y_j = \mathbf xA\mathbf y^T$, by linearity in each slot. $\square$

**Remark 198:** so Example 195 describes **every** bilinear form on a finite-dimensional space. Changing basis changes the Gram matrix to $P^TAP$ with $P$ invertible (compare $P^{-1}AP$ for linear maps).

> **Definition 199 (Symmetric)**
> $B$ is **symmetric** if $B(v_1, v_2) = B(v_2, v_1)$ for all $v_1, v_2$; equivalently, its Gram matrices are symmetric.

## Inner Product Spaces

> **Definition 200 (Positive definite)**
> A bilinear form $B$ on a **real** space is **positive definite** if $B(v, v) \geq 0$ for all $v$, with equality iff $v = 0$. ("$\geq 0$" makes no sense over a general field.)

> **Definition 201 (Inner product)**
> An **inner product** on a real vector space is a positive definite, symmetric bilinear form, written $\langle x, y\rangle$. A real vector space with one is an **inner product space**.

> [!example]- Examples 202 – 203
> **202** The dot product on $\mathbb{R}^n$: symmetric, bilinear, and $\mathbf x \cdot \mathbf x = x_1^2 + \dots + x_n^2 > 0$ for $\mathbf x \neq \mathbf 0$. $\mathbb{R}^n$ with it is $n$-dimensional **Euclidean space**.
> **203** On $\mathbb{R}_n[x]$ (or $C[a, b]$), $\langle f, g\rangle = \int_a^b f(x)g(x)\,dx$ ($a < b$). It's bilinear (integration is linear) and symmetric. If $f \neq 0$ is a polynomial, it vanishes at only finitely many points, so $\langle f, f\rangle = \int_a^b f^2 > 0$.

> **Definition 204 (Norm, distance)**
> $\|v\| = \sqrt{\langle v, v\rangle}$ is the **norm** (magnitude, length). The **distance** is $d(v, w) = \|v - w\|$.

> **Proposition 205 (Norm properties)**
> 1. $\|v\| \geq 0$, with equality iff $v = 0_V$.
> 2. $\|\alpha v\| = |\alpha|\,\|v\|$.
> 3. **Triangle inequality:** $\|v + w\| \leq \|v\| + \|w\|$.

> **Proposition 206 (Cauchy–Schwarz inequality)**
> $$|\langle v, w\rangle| \leq \|v\|\,\|w\|,$$
> with equality iff $v, w$ are linearly dependent.

> [!proof]- Proof of Cauchy–Schwarz
> Trivial if $w = 0$. Otherwise, for all $t \in \mathbb{R}$,
> $$0 \leq \|v + tw\|^2 = \|v\|^2 + 2t\langle v, w\rangle + t^2\|w\|^2.$$
> A quadratic in $t$ that is never negative has discriminant $\leq 0$: $4\langle v, w\rangle^2 - 4\|v\|^2\|w\|^2 \leq 0$.
> Equality means a repeated root $t_0$, so $\|v + t_0w\| = 0$, i.e. $v + t_0w = 0$: dependent. The converse is immediate. $\square$

> [!proof]- Proof of Proposition 205
> (1), (2) are straightforward. For (3):
> $$\|v + w\|^2 = \|v\|^2 + 2\langle v, w\rangle + \|w\|^2 \leq \|v\|^2 + 2\|v\|\|w\| + \|w\|^2 = (\|v\| + \|w\|)^2. \ \square$$

> **Proposition 207 ($d$ is a metric)**
> 1. $d(v, w) \geq 0$, with equality iff $v = w$;
> 2. $d(v, w) = d(w, v)$;
> 3. $d(u, w) \leq d(u, v) + d(v, w)$.
> 
> *(From the norm properties.)*

**Angles:** in $\mathbb{R}^2, \mathbb{R}^3$, $\mathbf x \cdot \mathbf y = \|\mathbf x\|\|\mathbf y\|\cos\theta$. So in any inner product space define the **angle** between non-zero $x, y$ as
$$\cos^{-1}\left(\frac{\langle x, y\rangle}{\|x\|\|y\|}\right),$$
which is well-defined because Cauchy–Schwarz gives $\left|\frac{\langle x, y\rangle}{\|x\|\|y\|}\right| \leq 1$.

> [!example]- Example 208 (sines and cosines are orthogonal)
> In $C[-\pi, \pi]$ with $\langle f, g\rangle = \int_{-\pi}^\pi fg$:
> - $\langle\sin mx, \cos nx\rangle = 0$, since the integrand is odd.
> - For $m \neq n$, using $\cos mx\cos nx = \frac12[\cos(m+n)x + \cos(m-n)x]$:
> $$\langle\cos mx, \cos nx\rangle = \frac12\left[\frac{\sin(m+n)x}{m+n} + \frac{\sin(m-n)x}{m-n}\right]_{-\pi}^{\pi} = 0.$$
> - $\|\cos mx\|^2 = \frac12\int_{-\pi}^\pi(\cos 2mx + 1)\,dx = \pi$ for $m \neq 0$, and $\|1\|^2 = 2\pi$.

> [!note]- Remark 209 (Fourier series)
> If $f(x) = \frac12a_0 + \sum_{k \geq 1}(a_k\cos kx + b_k\sin kx)$ on $(-\pi, \pi)$, and integrals and sums can be swapped, then the orthogonality relations give
> $$\int_{-\pi}^\pi f(x)\sin lx\,dx = \pi b_l,$$
> so the **Fourier coefficients** are
> $$a_l = \frac1\pi\int_{-\pi}^\pi f(x)\cos lx\,dx \ (l \geq 0), \qquad b_l = \frac1\pi\int_{-\pi}^\pi f(x)\sin lx\,dx \ (l \geq 1).$$
> Justifying the convergence and the swap is hard analysis.

## Orthogonal Maps

> **Definition 210 (Orthogonal map)**
> A linear $\alpha : V \to V$ on an inner product space is **orthogonal** if $\langle\alpha(v), \alpha(w)\rangle = \langle v, w\rangle$ for all $v, w$.

> **Proposition 211**
> A linear $\alpha : \mathbb{R}^n_{\text{col}} \to \mathbb{R}^n_{\text{col}}$ is orthogonal (for the dot product) iff its matrix $A$ in the standard basis is an orthogonal matrix.

> [!proof]- Proof
> (⇒) $\delta_{ij} = \mathbf e_i \cdot \mathbf e_j = \alpha(\mathbf e_i) \cdot \alpha(\mathbf e_j) = \mathbf e_i^TA^TA\mathbf e_j = (A^TA)_{ij}$, so $A^TA = I_n$.
> (⇐) Reverse to get $\alpha(\mathbf e_i) \cdot \alpha(\mathbf e_j) = \delta_{ij}$; then by linearity
> $$\alpha\Big(\sum u_i\mathbf e_i\Big) \cdot \alpha\Big(\sum v_j\mathbf e_j\Big) = \sum_{i,j}u_iv_j\delta_{ij} = \sum u_iv_i. \ \square$$

> **Proposition 212** An orthogonal map is an **isometry** (preserves distance).

> [!proof]- Proof
> $d(\alpha v, \alpha w)^2 = \langle\alpha(v - w), \alpha(v - w)\rangle = \langle v - w, v - w\rangle = d(v, w)^2$. (Conversely every linear isometry of a finite-dimensional space is orthogonal; see Geometry for $\mathbb{R}^n$.) $\square$

> **Definition 213 (Orthonormal set)**
> $\{v_1, \dots, v_k\}$ is **orthonormal** if $\langle v_i, v_j\rangle = \delta_{ij}$: unit vectors, mutually perpendicular.

> **Lemma 214** An orthonormal set is linearly independent.

> [!proof]- Proof
> If $\sum\alpha_jv_j = 0$, take the inner product with $v_i$: $0 = \sum_j\alpha_j\langle v_j, v_i\rangle = \alpha_i$. $\square$

**Remark 215:** so $n$ orthonormal vectors in an $n$-dimensional space form an **orthonormal basis**. Every finite-dimensional inner product space has one (Linear Algebra II, Gram–Schmidt).

> **Proposition 216 (Orthogonal matrices)**
> For $X \in M_{n \times n}(\mathbb{R})$ with the dot product, these are equivalent:
> 1. $XX^T = I_n$;
> 2. $X^TX = I_n$;
> 3. the rows of $X$ form an orthonormal basis of $\mathbb{R}^n$;
> 4. the columns of $X$ form an orthonormal basis of $\mathbb{R}^n_{\text{col}}$;
> 5. $X\mathbf x \cdot X\mathbf y = \mathbf x \cdot \mathbf y$ for all $\mathbf x, \mathbf y$.

> [!proof]- Proof
> (1 ⇔ 2) $AB = I \iff BA = I$ for square matrices (Cor 164).
> (1 ⇔ 3) $(XX^T)_{ij} = \mathbf x_i \cdot \mathbf x_j$ for rows $\mathbf x_i$; $n$ orthonormal rows form a basis.
> (2 ⇔ 4) The same with columns: $(X^TX)_{ij} = \mathbf y_i \cdot \mathbf y_j$.
> (2 ⇒ 5) $(X\mathbf x) \cdot (X\mathbf y) = \mathbf x^TX^TX\mathbf y = \mathbf x^T\mathbf y$.
> (5 ⇒ 4) $\delta_{ij} = \mathbf e_i \cdot \mathbf e_j = X\mathbf e_i \cdot X\mathbf e_j$, and $X\mathbf e_i$ are the columns. $\square$

**Remark 217:** (5) says $\mathbf x \mapsto X\mathbf x$ preserves the inner product, hence lengths and angles: it's an **isometry** of Euclidean space. So **$X$ is orthogonal iff it gives an isometry.** Compare [[LA1 - Inverses, Transposes and Orthogonal Matrices]].

## Complex Inner Product Spaces

The plain dot product fails on $\mathbb{C}^n$: $\|(1, i)\|^2 = 1^2 + i^2 = 0$. The fix is to conjugate the second slot:
$$(z_1, \dots, z_n) \cdot (w_1, \dots, w_n) = \sum_{i=1}^n z_i\overline{w_i}, \qquad \text{so } \mathbf z \cdot \mathbf z = \sum|z_i|^2 \geq 0.$$
This is linear in the first variable and **conjugate symmetric**: $\langle v_1, v_2\rangle = \overline{\langle v_2, v_1\rangle}$.

> **Definition 218 (Sesquilinear form, complex inner product space)**
> On a complex vector space, $\langle -, -\rangle : V \times V \to \mathbb{C}$ is **sesquilinear** if
> 1. $\langle\alpha_1v_1 + \alpha_2v_2, v_3\rangle = \alpha_1\langle v_1, v_3\rangle + \alpha_2\langle v_2, v_3\rangle$, and
> 2. $\langle v_1, v_2\rangle = \overline{\langle v_2, v_1\rangle}$.
> 
> Then $\langle v, v\rangle \in \mathbb{R}$, and the form is **positive definite** if $\langle v, v\rangle \geq 0$ with equality iff $v = 0$. A positive definite sesquilinear form is a (complex) inner product, and a complex vector space with one is a **complex inner product space**.

> [!note]- Remarks 219 – 220
> **219** "Sesqui-" means $1\frac12$ (a sesquicentenary is 150 years): linear in one slot, conjugate-linear in the other.
> **220** The complex analogue of orthogonal maps are **unitary** maps: $\langle Ux, Uy\rangle = \langle x, y\rangle$. A **unitary matrix** has $UU^* = I = U^*U$, where $U^* = \overline{U}^T$.
> In quantum theory, a wavefunction $\psi$ is complex-valued and $\|\psi\|^2 = \psi\overline\psi$ is a probability density. More in Linear Algebra II and Part A.
