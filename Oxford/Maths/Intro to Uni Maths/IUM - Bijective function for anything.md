**Example A.15 (Equivalence relation induced by a function)**
For any function $f : X \to Y$, we can define an equivalence relation on $X$ by
$$x \sim y \iff f(x) = f(y).$$
- **Reflexive:** $\forall x$, $x \sim x$ because $f(x) = f(x)$.
- **Symmetric:** $\forall x, y$, if $x \sim y$ then $f(x) = f(y)$, so $f(y) = f(x)$, which means $y \sim x$.
- **Transitive:** $\forall x, y, z$, if $x \sim y$ and $y \sim z$ then $f(x) = f(y)$ and $f(y) = f(z)$, so $f(x) = f(z)$, which means $x \sim z$.

For this equivalence relation, define a new function $F : X/\sim \; \to f(X)$ by
$$F([x]) = f(x).$$
$F$ is well-defined because every representative of $[x]$ has the same value of $f$.

**Claim:** $F$ is a bijection.

*Proof.*
(Injective): If $F([x]) = F([y])$ then $f(x) = f(y)$, so $x \sim y$ and therefore $[x] = [y]$.
(Surjective): The codomain was changed from $Y$ to $f(X)$, and every function is surjective onto its image. $\square$

**Specific example:** Let $X = \mathbb{R}$, $Y = \mathbb{C}$, with $f(x) = e^{2\pi i x}$.
The induced equivalence relation on $\mathbb{R}$ is $x \sim y \iff x - y \in \mathbb{Z}$ (as in Example A.10).
So $F : \mathbb{R}/\sim \; \to f(\mathbb{R})$ is a bijection, where $f(\mathbb{R})$ is the unit circle and $\mathbb{R}/\sim$ is usually written $\mathbb{R}/\mathbb{Z}$.

Therefore $\mathbb{R}/\mathbb{Z}$ is in bijection with the unit circle.

*When a function isn't injective, quotient the problem away.*