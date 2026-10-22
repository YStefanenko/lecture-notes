Analysis I, Chapter 1.4 (recap, not lectured). Back to [[A1]]. See also [[Complex Numbers]].

Define $\mathbb{C} = \mathbb{R}^2$ with
$$(a_1, b_1) + (a_2, b_2) = (a_1 + a_2, b_1 + b_2), \qquad (a_1, b_1)(a_2, b_2) = (a_1 a_2 - b_1 b_2,\ a_2 b_1 + a_1 b_2).$$
Write $i = (0, 1)$ and $a + bi = (a, b)$; then $i^2 = -1$, and $r \leftrightarrow r + 0i$ embeds $\mathbb{R}$ in $\mathbb{C}$. $\mathbb{C}$ satisfies all the field axioms.

> **Proposition 1.80**
> There is no subset $\mathbb{P} \subseteq \mathbb{C}$ satisfying the order axioms P1–P3. ($\mathbb{C}$ is not an ordered field.)

> [!proof]- Proof
> By P3 exactly one of $i \in \mathbb{P}$, $i = 0$, $-i \in \mathbb{P}$.
> - $i = 0$ gives $1 = i^4 = 0$, contradicting Z.
> - $i \in \mathbb{P}$ gives $-i = i^3 \in \mathbb{P}$ by P2, so $\pm i \in \mathbb{P}$, contradicting P3.
> - $-i \in \mathbb{P}$: the same contradiction. $\square$

Throughout, $z = x + yi$ with $x = \operatorname{Re} z$, $y = \operatorname{Im} z$.

> **Definition 1.81 (Modulus)** $|z| = \sqrt{x^2 + y^2}$.

> **Definition 1.82 (Conjugate)** $\bar z = x - yi$ (also written $z^*$).

**Properties** (algebra, easy to check):
1. If $z$ is real, $|z|$ agrees with the real modulus.
2. $|z| = |\bar z|$
3. $|z|^2 = z \bar z$
4. $|\operatorname{Re} z| \leq |z|$, $|\operatorname{Im} z| \leq |z|$
5. $z + \bar z = 2 \operatorname{Re} z$
6. $z - \bar z = 2i \operatorname{Im} z$
7. $\overline{z_1 + z_2} = \bar z_1 + \bar z_2$
8. $\overline{z_1 z_2} = \bar z_1 \, \bar z_2$

> **Theorem 1.83** For $z, w \in \mathbb{C}$, $|zw| = |z||w|$.

> [!proof]- Proof
> With $z = x + yi$, $w = u + vi$: $(xv + yu)^2 + (xu - yv)^2 = (x^2 + y^2)(u^2 + v^2)$, then take unique non-negative square roots. $\square$

> **Theorem 1.84 (Triangle Inequality)** For $z, w \in \mathbb{C}$, $|z + w| \leq |z| + |w|$.

> [!proof]- Proof
> $$\begin{aligned} |z + w|^2 &= (z + w)(\bar z + \bar w) = z\bar z + (z\bar w + \bar z w) + w \bar w \\ &= z \bar z + 2\operatorname{Re}(z \bar w) + w \bar w \leq z\bar z + 2|z \bar w| + w \bar w \\ &= |z|^2 + 2|z||w| + |w|^2 = (|z| + |w|)^2. \quad \square \end{aligned}$$

> [!note]- Remark 1.85 (why "triangle")
> In the triangle with vertices $0$, $z$, $z + w$, the sides have lengths $|z|$, $|w|$, $|z + w|$. One side is at most the sum of the other two.
