Prelims Probability, Chapter 5.5. Back to [[P1]]. Continuous analogue of [[P1 - Joint Discrete Distributions]].

The **joint c.d.f.** of any pair is $F_{X,Y}(x, y) = \mathbb{P}(X \leq x, Y \leq y)$. It is non-decreasing in each argument, tends to $0$ as $x, y \to -\infty$, and to $1$ as $x, y \to \infty$.

> **Definition 5.26 (Jointly continuous, joint density)**
> $X, Y$ are **jointly continuous** with **joint density** $f_{X,Y}$ if
> $$F_{X,Y}(x, y) = \int_{-\infty}^y\int_{-\infty}^x f_{X,Y}(u, v)\,du\,dv,$$
> where (a) $f_{X,Y} \geq 0$ and (b) $\iint f_{X,Y} = 1$.

Where smooth, $f_{X,Y}(x, y) = \frac{\partial^2}{\partial x\,\partial y}F_{X,Y}(x, y)$. For nice sets $B \subseteq \mathbb{R}^2$, $\mathbb{P}((X, Y) \in B) = \iint_B f_{X,Y}$. The course only proves this for rectangles:

> **Theorem 5.27 (Rectangles)**
> For $a < b$, $c < d$:
> $$\mathbb{P}(a < X \leq b,\ c < Y \leq d) = \int_c^d\int_a^b f_{X,Y}(x, y)\,dx\,dy.$$

> [!proof]- Proof
> By inclusion–exclusion on the corners:
> $$\mathbb{P}(a < X \leq b, c < Y \leq d) = F_{X,Y}(b, d) - F_{X,Y}(a, d) + F_{X,Y}(a, c) - F_{X,Y}(b, c) = \int_c^d\int_a^b f_{X,Y}. \quad \square$$

> **Theorem 5.28 (Marginal densities)**
> If $X, Y$ are jointly continuous, $X$ is continuous with density $f_X(x) = \int_{-\infty}^\infty f_{X,Y}(x, y)\,dy$, and likewise $f_Y(y) = \int f_{X,Y}(x, y)\,dx$.

> [!proof]- Proof
> $\int_{-\infty}^x f_X(u)\,du = \int_{-\infty}^x\int_{-\infty}^\infty f_{X,Y}(u, y)\,dy\,du = \mathbb{P}(X \leq x)$. $\square$

All of this extends to $n$ random variables.

> [!example]- Example 5.29: $f_{X,Y}(x, y) = \frac12(x + y)$ on $[0, 1] \times [1, 2]$
> **Valid density:** $\int_1^2\int_0^1 \frac12(x + y)\,dx\,dy = \int_1^2\left(\frac14 + \frac y2\right)dy = 1$.
> **Probability:** $\mathbb{P}(X \leq \frac12, Y \geq \frac32) = \int_{3/2}^2\left(\frac1{16} + \frac y4\right)dy = \frac14$.
> **Marginals:** $f_X(x) = \frac x2 + \frac34$ on $[0, 1]$; $f_Y(y) = \frac14 + \frac y2$ on $[1, 2]$.
> **Then:** $\mathbb{P}(X \geq \frac12) = \int_{1/2}^1\left(\frac x2 + \frac34\right)dx = \frac{9}{16}$.

> **Definition 5.30 (Independence)**
> Jointly continuous $X, Y$ are **independent** if $f_{X,Y}(x, y) = f_X(x)f_Y(y)$ for all $x, y$. Similarly for $X_1, \dots, X_n$: $f_{X_1,\dots,X_n} = \prod f_{X_i}$.

Then also $F_{X,Y}(x, y) = F_X(x)F_Y(y)$.

> [!example]- Example 5.31
> In Example 5.29, $\frac12(x + y) \neq \left(\frac x2 + \frac34\right)\left(\frac14 + \frac y2\right)$, so $X, Y$ are not independent.

## Expectation (5.5.1)

> **Theorem 5.32**
> $$\mathbb{E}[h(X, Y)] = \int_{-\infty}^\infty\int_{-\infty}^\infty h(x, y)\,f_{X,Y}(x, y)\,dx\,dy.$$
> (Proof is technical; compare the discrete formula (2.2).)

**Covariance:** $\operatorname{cov}(X, Y) = \mathbb{E}[(X - \mathbb{E}X)(Y - \mathbb{E}Y)] = \mathbb{E}[XY] - \mathbb{E}[X]\,\mathbb{E}[Y]$.

**Exercise 5.33:** $\mathbb{E}[aX + bY] = a\,\mathbb{E}[X] + b\,\mathbb{E}[Y]$ and $\operatorname{var}(X + Y) = \operatorname{var}(X) + \operatorname{var}(Y) + 2\operatorname{cov}(X, Y)$.

So the rules for expectation, variance and covariance are **identical** in the discrete and continuous cases. That's no coincidence: Part A Integration gives one definition of expectation covering both (Remark 5.34).

> [!example]- Example 5.35 (standard bivariate normal)
> For $-1 < \rho < 1$:
> $$f_{X,Y}(x, y) = \frac{1}{2\pi\sqrt{1 - \rho^2}}\exp\left(-\frac{x^2 - 2\rho xy + y^2}{2(1 - \rho^2)}\right).$$
> **Marginals:** complete the square, $x^2 - 2\rho xy + y^2 = (y - \rho x)^2 + x^2(1 - \rho^2)$:
> $$f_X(x) = \frac{1}{\sqrt{2\pi}}e^{-x^2/2}\int \frac{1}{\sqrt{2\pi(1-\rho^2)}}\exp\left(-\frac{(y - \rho x)^2}{2(1 - \rho^2)}\right)dy = \frac{1}{\sqrt{2\pi}}e^{-x^2/2},$$
> since the integrand is the $N(\rho x, 1 - \rho^2)$ density. So $X \sim N(0, 1)$, and by symmetry so is $Y$.
> 
> **Covariance:** both means are 0, and the inner $y$-integral is the mean of $N(\rho x, 1 - \rho^2)$, which is $\rho x$:
> $$\operatorname{cov}(X, Y) = \mathbb{E}[XY] = \int \frac{x}{\sqrt{2\pi}}e^{-x^2/2}\cdot\rho x\,dx = \rho\,\mathbb{E}[X^2] = \rho.$$
> 
> So bivariate normal $X, Y$ are independent **iff** $\operatorname{cov}(X, Y) = 0$ (i.e. $\rho = 0$). That's special to normals; false in general.
