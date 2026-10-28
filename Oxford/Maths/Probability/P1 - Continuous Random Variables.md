Prelims Probability, Chapter 5.1–5.4. Back to [[P1 - Basics]]. Next: [[P1 - Joint Continuous Distributions]].

Some quantities (lengths, weights, times) are naturally continuous, and continuous models also approximate huge discrete ones. A fair spinner's angle can't give each angle positive probability; instead $\mathbb{P}(X \in [a, b]) = \frac{b - a}{2\pi}$.

## Random Variables and C.d.f.s

> **Definition 5.1 (Random variable)**
> A **random variable** on $(\Omega, \mathcal{F}, \mathbb{P})$ is a function $X : \Omega \to \mathbb{R}$ with $\{\omega : X(\omega) \leq x\} \in \mathcal{F}$ for each $x \in \mathbb{R}$.

This includes discrete r.v.s: $\{X \leq x\} = \bigcup_{y \leq x,\ y \in \operatorname{Im}X}\{X = y\}$ is a countable union of events.

> **Definition 5.2 (Cumulative distribution function)**
> The **c.d.f.** of $X$ is $F_X : \mathbb{R} \to [0, 1]$, $F_X(x) = \mathbb{P}(X \leq x)$.

> [!example]- Examples 5.3 & 5.4
> **5.3** Heads in 3 fair tosses: a step function, $F_X = 0, \frac18, \frac12, \frac78, 1$ on $x < 0$, $[0,1)$, $[1,2)$, $[2,3)$, $x \geq 3$.
> **5.4** Spinner angle: $F_X(x) = 0$ for $x < 0$, $\frac{x}{2\pi}$ for $0 \leq x < 2\pi$, and $1$ for $x \geq 2\pi$.

> **Theorem 5.5 (Properties of c.d.f.s)**
> 1. $F_X$ is non-decreasing.
> 2. $\mathbb{P}(a < X \leq b) = F_X(b) - F_X(a)$ for $a < b$.
> 3. $F_X(x) \to 0$ as $x \to -\infty$.
> 4. $F_X(x) \to 1$ as $x \to \infty$.

> [!proof]- Proof
> 1. $a < b \Rightarrow \{X \leq a\} \subseteq \{X \leq b\}$.
> 2. $\mathbb{P}(\{X \leq b\} \setminus \{X \leq a\}) = F_X(b) - F_X(a)$.
> 3 & 4. (Sketch) Intuitively "$F_X(\mp\infty)$" should be $0$ and $1$; making this rigorous takes limits and countable additivity (P3). $\square$

Conversely, any $F$ with properties 1, 3, 4 that is right-continuous is the c.d.f. of some r.v. (not proved here). Discrete r.v.s have step-function c.d.f.s.

> **Definition 5.6 (Continuous random variable, p.d.f.)**
> $X$ is a **continuous random variable** if
> $$F_X(x) = \mathbb{P}(X \leq x) = \int_{-\infty}^x f_X(u)\,du$$
> for some $f_X : \mathbb{R} \to \mathbb{R}$ with (a) $f_X \geq 0$ and (b) $\int_{-\infty}^\infty f_X = 1$. $f_X$ is the **probability density function (p.d.f.)**, or density.

Assume $f_X$ has at most countably many jumps and is smooth elsewhere (Remark 5.7). By the Fundamental Theorem of Calculus, $F_X'(x) = f_X(x)$ wherever $f_X$ is continuous (Remark 5.8).

> [!example]- Example 5.9 (density with a jump)
> $F_X(x) = 1 - e^{-x}$ for $x \geq 0$ (else $0$) has density $f_X(x) = e^{-x}$ for $x \geq 0$ (else $0$). $f_X$ jumps at $0$, and $F_X$ isn't differentiable there (slopes $0$ from the left, $1$ from the right), but $F_X' = f_X$ everywhere else.

> [!example]- Example 5.10 (finding the constant)
> $f_X(x) = cx^2(1-x)$ on $[0, 1]$. Then $1 = c\left[\frac{x^3}{3} - \frac{x^4}{4}\right]_0^1 = \frac{c}{12}$, so $c = 12$, and $F_X(x) = 4x^3 - 3x^4$ on $[0, 1)$ ($0$ below, $1$ above).

> [!example]- Example 5.11 (phone calls)
> $f_X(x) = \frac16 e^{-x/6}$, $x \geq 0$. $\mathbb{P}(3 < X \leq 6) = \int_3^6 \frac16 e^{-x/6}dx = e^{-1/2} - e^{-1}$, and $\mathbb{P}(X > 6) = e^{-1}$.

**p.d.f. vs p.m.f.**

| Continuous (p.d.f.) | Discrete (p.m.f.) |
|---|---|
| $f_X(x) \geq 0$ | $p_X(x) \geq 0$ |
| $\int_{-\infty}^\infty f_X(x)\,dx = 1$ | $\sum_{x \in \operatorname{Im}X} p_X(x) = 1$ |
| $F_X(x) = \int_{-\infty}^x f_X(u)\,du$ | $F_X(x) = \sum_{u \leq x} p_X(u)$ |

**WARNING: $f_X(x)$ is NOT a probability** (it can exceed 1). For small $\epsilon$: $\mathbb{P}(x < X \leq x + \epsilon) \approx f_X(x)\,\epsilon$.

> **Theorem 5.12**
> For a continuous r.v., $\mathbb{P}(X = x) = 0$ for all $x$, and $\mathbb{P}(a \leq X \leq b) = \int_a^b f_X(x)\,dx$.

> [!proof]- Proof (non-examinable)
> If $p = \mathbb{P}(X = x) > 0$, then $F_X(x) - F_X(x - 1/n) = \mathbb{P}(x - 1/n < X \leq x) \geq p$ for all $n$, but $F_X$ is continuous at $x$, so the left side $\to 0$. Contradiction. Then $\mathbb{P}(a \leq X \leq b) = \mathbb{P}(X = a) + \mathbb{P}(a < X \leq b) = \int_a^b f_X$. $\square$

This doesn't break probability: $\{X \leq x\} = \bigcup_{y \leq x}\{X = y\}$ is an **uncountable** union of null events, and P3 only adds up countably many.

> [!note]- Remark 5.13 (neither discrete nor continuous)
> Flip a fair coin: heads gives $X \sim U[0, 1]$, tails gives $X = \frac12$. Then $\mathbb{P}(X \leq x) = \frac x2$ on $[0, \frac12)$ and $\frac{x+1}{2}$ on $[\frac12, 1]$: there's a jump, so no density, but uncountably many values, so not discrete either. The c.d.f. works for every r.v.

## Classical Continuous Distributions (5.2)

| Distribution | p.d.f. | Notes |
|---|---|---|
| **Uniform** $U[a, b]$ | $\frac{1}{b-a}$ on $[a, b]$ | |
| **Exponential** $\text{Exp}(\lambda)$ | $\lambda e^{-\lambda x}$, $x \geq 0$ | lifetimes, waiting times between random events |
| **Gamma** $\text{Gamma}(\alpha, \lambda)$ | $\frac{\lambda^\alpha}{\Gamma(\alpha)}x^{\alpha-1}e^{-\lambda x}$, $x \geq 0$ | generalises the exponential; $\chi^2_d = \text{Gamma}(\frac d2, \frac12)$ |
| **Normal** $N(\mu, \sigma^2)$ | $\frac{1}{\sqrt{2\pi\sigma^2}}\exp\left(-\frac{(x-\mu)^2}{2\sigma^2}\right)$ | standard normal $N(0, 1)$; key because of the CLT |

The **gamma function** is $\Gamma(\alpha) = \int_0^\infty u^{\alpha-1}e^{-u}\,du$ for $\alpha > 0$, with $\Gamma(n) = (n-1)!$ for positive integers $n$.

**Exercise 5.14** For uniform and exponential: check they're p.d.f.s and find their c.d.f.s.

> [!example]- Example 5.15: the normal density integrates to 1
> Substitute $z = (x - \mu)/\sigma$: $I = \int \frac{1}{\sqrt{2\pi}}e^{-z^2/2}dz$. Then
> $$I^2 = \iint \frac{1}{2\pi}e^{-(x^2 + y^2)/2}\,dx\,dy = \int_0^{2\pi}\!\!\int_0^\infty \frac{1}{2\pi}r e^{-r^2/2}\,dr\,d\theta = \left[-e^{-r^2/2}\right]_0^\infty = 1$$
> (polar coordinates, Jacobian $r$). As $I \geq 0$, $I = 1$. $\square$

The standard normal c.d.f. $\Phi(x) = \int_{-\infty}^x \frac{1}{\sqrt{2\pi}}e^{-u^2/2}du$ has no closed form; it's tabulated numerically.

## Expectation (5.3)

> **Definition 5.16 (Expectation)**
> $$\mathbb{E}[X] = \int_{-\infty}^\infty x\,f_X(x)\,dx \tag{5.3}$$
> whenever $\int |x| f_X(x)\,dx < \infty$ (otherwise undefined, or $\mathbb{E}[X] = \infty$ if only the positive tail diverges).

(Heuristic: $\sum (n\delta)f_X(n\delta)\delta \to \int x f_X$ as $\delta \to 0$.)

> **Theorem 5.17 (Expectation of a function)**
> $$\mathbb{E}[h(X)] = \int_{-\infty}^\infty h(x)\,f_X(x)\,dx \tag{5.4}$$
> whenever $\int |h(x)| f_X(x)\,dx < \infty$.

> [!proof]- Proof idea (non-examinable)
> For non-negative $X$, swap the order of integration:
> $$\mathbb{E}[X] = \int_0^\infty\!\!\int_0^x f_X(x)\,dy\,dx = \int_0^\infty\!\!\int_y^\infty f_X(x)\,dx\,dy = \int_0^\infty \mathbb{P}(X > y)\,dy.$$
> If $h(X) \geq 0$:
> $$\mathbb{E}[h(X)] = \int_0^\infty \mathbb{P}(h(X) > y)\,dy = \int_0^\infty\!\!\int_{h(x) > y} f_X(x)\,dx\,dy = \int f_X(x)\int_{y < h(x)}dy\,dx = \int h(x)f_X(x)\,dx. \quad \square$$

**Variance** is defined as before: $\operatorname{var}(X) = \mathbb{E}[(X - \mathbb{E}[X])^2] = \mathbb{E}[X^2] - (\mathbb{E}[X])^2$.

> **Theorem 5.18**
> $\mathbb{E}[aX + b] = a\,\mathbb{E}[X] + b$ and $\operatorname{var}(aX + b) = a^2\operatorname{var}(X)$.

> [!proof]- Proof
> $\int(ax + b)f_X = a\int x f_X + b\int f_X = a\mathbb{E}[X] + b$. Then $\operatorname{var}(aX + b) = \mathbb{E}[a^2(X - \mathbb{E}X)^2] = a^2\operatorname{var}(X)$. $\square$

> [!example]- Example 5.19: properties of $N(\mu, \sigma^2)$
> If $X \sim N(\mu, \sigma^2)$ then $X \overset{d}{=} \mu + \sigma Z$ with $Z \sim N(0, 1)$, $F_X(x) = \Phi\left(\frac{x - \mu}{\sigma}\right)$, $\mathbb{E}[X] = \mu$, $\operatorname{var}(X) = \sigma^2$.
> 
> - For $Z$: $\mathbb{E}[Z] = 0$ (odd integrand). Integrating by parts, $\mathbb{E}[Z^2] = \int x\cdot\frac{xe^{-x^2/2}}{\sqrt{2\pi}}dx = \left[-x\frac{e^{-x^2/2}}{\sqrt{2\pi}}\right] + \int \frac{e^{-x^2/2}}{\sqrt{2\pi}} = 1$.
> - $\mathbb{P}(\mu + \sigma Z \leq x) = \Phi((x - \mu)/\sigma)$; differentiating gives $\frac1\sigma\varphi\left(\frac{x-\mu}{\sigma}\right)$, the $N(\mu, \sigma^2)$ density.
> - Then $\mathbb{E}[X] = \mu + \sigma\cdot 0$ and $\operatorname{var}(X) = \sigma^2\operatorname{var}(Z) = \sigma^2$ by Theorem 5.18. $\square$

**Exercise 5.20** $X \sim U[a, b]$: $\mathbb{E}[X] = \frac{a+b}{2}$, $\operatorname{var}(X) = \frac{(b-a)^2}{12}$. $Y \sim \text{Exp}(\lambda)$: $\mathbb{E}[Y] = \frac1\lambda$, $\operatorname{var}(Y) = \frac{1}{\lambda^2}$. (The exponential parameter is the reciprocal of the mean.)

> [!example]- Example 5.21: $X \sim \text{Gamma}(2, 2)$, so $f_X(x) = 4xe^{-2x}$
> $\mathbb{E}[X] = \int x\cdot 4xe^{-2x}dx = \int \frac{2^3}{2!}x^{3-1}e^{-2x}dx = 1$, recognising the $\text{Gamma}(3, 2)$ density.
> $\mathbb{E}[1/X] = \int \frac1x 4xe^{-2x}dx = 2\int 2e^{-2x}dx = 2$, recognising $\text{Exp}(2)$.
> 
> **WARNING: in general $\mathbb{E}[1/X] \neq 1/\mathbb{E}[X]$.** (Trick: spot a known density inside the integral.)

## Functions of Continuous Random Variables (5.4)

> [!example]- Example 5.22 (tree-free area in a forest)
> $R$ = distance to the nearest tree, $f_R(r) = re^{-r^2/2}$ for $r \geq 0$ (the **Rayleigh** distribution). Then $F_R(r) = 1 - e^{-r^2/2}$, and for $A = \pi R^2$:
> $$F_A(a) = \mathbb{P}\left(R \leq \sqrt{a/\pi}\right) = 1 - e^{-a/(2\pi)}, \qquad f_A(a) = \frac{1}{2\pi}e^{-a/(2\pi)}.$$
> So $A \sim \text{Exp}\left(\frac{1}{2\pi}\right)$. **Method: go via the c.d.f.**
> 
> (Remark 5.23: the distance from the origin of a point with independent $N(0,1)$ coordinates is Rayleigh; Part A.)

> **Theorem 5.24 (Change of variables, increasing $h$)**
> If $h$ is differentiable with $h' > 0$, then $Y = h(X)$ is continuous with
> $$f_Y(y) = f_X(h^{-1}(y))\,\frac{d}{dy}h^{-1}(y).$$

> [!proof]- Proof
> $h$ is strictly increasing, so $h(X) \leq y \iff X \leq h^{-1}(y)$. So $F_Y(y) = F_X(h^{-1}(y))$; differentiate with the chain rule. $\square$
> 
> A similar result holds for strictly decreasing $h$. The proof is easier to remember than the formula.

If $h$ isn't one-to-one, work it out case by case through the c.d.f.:

> [!example]- Example 5.25: $x$-coordinate of a uniform point on the unit circle
> $\Theta \sim U[0, 2\pi)$ and $X = \cos\Theta$. Each $x \in (-1, 1)$ comes from two angles, so
> $$F_X(x) = \mathbb{P}(\arccos x \leq \Theta \leq 2\pi - \arccos x) = 1 - \frac{\arccos x}{\pi}, \qquad f_X(x) = \frac{1}{\pi\sqrt{1 - x^2}}, \quad -1 < x < 1.$$
> Note $f_X \to \infty$ at $\pm1$, yet it still integrates to 1.
