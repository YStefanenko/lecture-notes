Analysis I, Chapter 7.2. Back to [[A1]]. Builds on [[A1 - Power Series]].

Rigorous definitions of exponentials, logarithms, general powers, and trig and hyperbolic functions. Some steps use Hilary Term results (IVT, differentiability of inverses, Theorem 7.13).

## Exponential

> **Definition 7.18 (Exponential function)**
> $$\exp : \mathbb{C} \to \mathbb{C}, \qquad \exp(z) = \sum_{n=0}^\infty \frac{z^n}{n!}.$$

**Properties of exp:**
1. Converges for all $z$ (ratio test, Example 6.26): $R = \infty$.
2. $\exp(0) = 1$.
3. $\exp(1) = e$.
4. $\exp'(z) = \exp(z)$.
5. $\exp(x + y) = \exp(x)\exp(y)$.
6. $\exp(z) \neq 0$ (in fact the image of $\exp$ is $\mathbb{C} \setminus \{0\}$).
7. $\exp(q) = e^q$ for rational $q$.

> [!proof]- Proofs of 4–7
> **(4)** Term-by-term (Theorem 7.13): $\frac{d}{dz}\sum \frac{z^n}{n!} = \sum_0^\infty \frac{(n+1)z^n}{(n+1)!} = \sum \frac{z^n}{n!}$.
> 
> **(5)** Example 6.19 (Cauchy product). Alternatively, for fixed $c$ let $F(z) = \exp(z + c)\exp(-z)$. By the product rule $F'(z) = \exp(z + c)\exp(-z) - \exp(z+c)\exp(-z) = 0$, so $F$ is constant (Remark 7.14), equal to $F(0) = \exp(c)$. Put $c = x + y$, $z = -y$.
> 
> **(6)** $\exp(z)\exp(-z) = \exp(0) = 1$.
> 
> **(7)** For $q = m/n$: $(\exp(m/n))^n = \exp(m) = (\exp 1)^m = e^m$. By uniqueness of positive $n$th roots, $\exp(m/n) = \sqrt[n]{e^m} = e^q$. $\square$

**Real exponential.** For real $x \geq 0$, $\exp x > 0$ from the series; for $x < 0$, $\exp x = 1/\exp(-x) > 0$. So $\exp(\mathbb{R}) \subseteq (0, \infty)$. Since $\exp' = \exp > 0$, $\exp$ is increasing and so injective. Also $\exp x > x$ for $x > 0$ and $\exp(-x) = 1/\exp x$, so it takes arbitrarily large and arbitrarily small positive values. By the IVT (Hilary Term), $\exp : \mathbb{R} \to (0, \infty)$ is a bijection, with a differentiable inverse.

## Logarithm and General Powers

> **Definition 7.19 (Natural logarithm)**
> $\log x$ (or $\ln x$) is the inverse of the real exponential $\exp : \mathbb{R} \to (0, \infty)$.

> **Proposition 7.20** For $x > 0$, $\log' x = \dfrac1x$.

> [!proof]- Proof
> Differentiate $\exp(\log x) = x$ with the chain rule: $\log'(x)\exp(\log x) = 1$. $\square$

> [!example]- Example 7.21: the image of $\exp : \mathbb{C} \to \mathbb{C}$ is $\mathbb{C} \setminus \{0\}$
> $0$ isn't in the image (property 6). For $z = re^{i\theta} \neq 0$, take $w = \log r + i\theta$: then $\exp(w) = e^{\log r}e^{i\theta} = z$. $\square$

> **Definition 7.22 (General exponents)**
> For $a > 0$ and $x \in \mathbb{R}$: $a^x = \exp(x \log a)$. In particular $e^x = \exp x$.

> **Proposition 7.23** For $a, b > 0$ and $x \in \mathbb{R}$:
> $$\log(ab) = \log a + \log b, \qquad \log(a^x) = x\log a.$$

> [!proof]- Proof
> $\exp(\log a + \log b) = \exp(\log a)\exp(\log b) = ab = \exp(\log(ab))$; take logs. And $\log(a^x) = \log(\exp(x\log a)) = x\log a$. $\square$

> **Proposition 7.24** For $a > 0$ and $x, y \in \mathbb{R}$:
> $$a^{x+y} = a^x a^y, \qquad (a^x)^y = a^{xy}.$$

> [!proof]- Proof
> $a^{x+y} = \exp((x+y)\log a) = \exp(x\log a)\exp(y\log a) = a^x a^y$.
> $\log((a^x)^y) = y\log(a^x) = y x\log a = \log(a^{xy})$; apply $\exp$. $\square$

> **Proposition 7.25** For $x > 0$ and real $a$, $\dfrac{d}{dx}(x^a) = a x^{a-1}$.

> [!proof]- Proof
> $\frac{d}{dx}\exp(a\log x) = \frac ax \exp(a\log x) = a x^{-1}x^a = a x^{a-1}$. $\square$

## Trigonometric and Hyperbolic Functions

> **Definition 7.26 (Trigonometric and hyperbolic functions)**
> For $z \in \mathbb{C}$:
> $$\cos z = \frac{\exp(iz) + \exp(-iz)}{2}, \qquad \sin z = \frac{\exp(iz) - \exp(-iz)}{2i},$$
> $$\cosh z = \frac{\exp(z) + \exp(-z)}{2}, \qquad \sinh z = \frac{\exp(z) - \exp(-z)}{2},$$
> $$\sec x = \frac{1}{\cos x}, \quad \csc x = \frac{1}{\sin x}, \quad \tan x = \frac{\sin x}{\cos x}, \quad \cot x = \frac{\cos x}{\sin x}.$$

**Properties:**
1. Power series (all converge for every $z$):
$$\cos z = \sum_0^\infty \frac{(-1)^n z^{2n}}{(2n)!}, \quad \sin z = \sum_0^\infty \frac{(-1)^n z^{2n+1}}{(2n+1)!}, \quad \cosh z = \sum_0^\infty \frac{z^{2n}}{(2n)!}, \quad \sinh z = \sum_0^\infty \frac{z^{2n+1}}{(2n+1)!}.$$
2. $\cos 0 = 1$, $\sin 0 = 0$.
3. $\exp(iz) = \cos z + i\sin z$.
4. $\cos$ is even and $\sin$ is odd (only even/odd powers in their series).
5. $\cos' z = -\sin z$, $\sin' z = \cos z$.
6. $\sin(z + w) = \sin z\cos w + \cos z\sin w$ and $\cos(z + w) = \cos z\cos w - \sin z\sin w$.
7. $\cos^2 z + \sin^2 z = 1$.
8. $\pi/2$ is **defined** as the smallest positive root of $\cos$ (it exists by Hilary Term results, since $\cos 0 = 1 > 0 > \cos 2$).
9. $\exp$ has period $2\pi i$; $\cos$ and $\sin$ have period $2\pi$.
10. Hyperbolic relations: $\cos iz = \cosh z$, $\cosh iz = \cos z$, $\sin iz = i\sinh z$, $\sinh iz = i\sin z$, $\cosh(-z) = \cosh z$, $\sinh(-z) = -\sinh z$, $\cosh' = \sinh$, $\sinh' = \cosh$, $\cosh^2 z - \sinh^2 z = 1$,
$$\sin(x + iy) = \sin x\cosh y + i\cos x\sinh y, \qquad \cos(x + iy) = \cos x\cosh y - i\sin x\sinh y.$$

> [!proof]- Proofs of the trig properties
> **(1)** $\frac{\exp(iz) + \exp(-iz)}{2} = \frac12\sum \frac{i^n + (-i)^n}{n!}z^n$. Odd terms cancel; for $n = 2k$, $i^{2k} + (-i)^{2k} = 2(-1)^k$, giving $\sum \frac{(-1)^k z^{2k}}{(2k)!}$. Similarly $\frac{1}{2i}\sum \frac{i^n - (-i)^n}{n!}z^n$ keeps only odd $n = 2k+1$, where $i^{2k+1} - (-i)^{2k+1} = 2i(-1)^k$.
> 
> **(3)** $\cos z + i\sin z = \frac{e^{iz} + e^{-iz}}{2} + \frac{e^{iz} - e^{-iz}}{2} = \exp(iz)$.
> 
> **(5)** $\frac{d}{dz}\frac{e^{iz} + e^{-iz}}{2} = \frac{ie^{iz} - ie^{-iz}}{2} = -\sin z$; $\frac{d}{dz}\frac{e^{iz} - e^{-iz}}{2i} = \frac{e^{iz} + e^{-iz}}{2} = \cos z$. (Or differentiate the series.)
> 
> **(6)** Expand $\sin z\cos w + \cos z\sin w$ in exponentials:
> $$\frac{1}{4i}\left[2e^{iz}e^{iw} - 2e^{-iz}e^{-iw}\right] = \frac{e^{i(z+w)} - e^{-i(z+w)}}{2i} = \sin(z + w).$$
> The cosine formula is similar, or differentiate in $z$.
> 
> **(7)** Put $w = -z$ in the cosine addition formula. Or: $\frac{d}{dz}(\cos^2 + \sin^2) = 0$, so it's constant $= 1$. Or: $(\cos z + i\sin z)(\cos z - i\sin z) = e^{iz}e^{-iz} = 1$.
> 
> **(8)** $\cos 2 = 1 - 2 + \frac23 - \frac{2^6}{6!}\left(1 - \frac{2^2}{7 \times 8}\right) - \frac{2^{10}}{10!}\left(1 - \frac{2^2}{11 \times 12}\right) - \dots < 0$, since $1 - 2 + \frac23 < 0$ and every bracket after it is positive.
> 
> **(9)** From (7), $\sin(\pi/2) = \pm 1$ (in fact $1$), so $\exp(\pi i/2) = \pm i$. Then $\exp(z + 2\pi i) = \exp z\,(\exp(\pi i/2))^4 = \exp z\,(\pm i)^4 = \exp z$. $\square$

> [!example]- Example 7.27: power series of $\tan z$ up to $z^5$
> $\tan$ is odd, so only $z, z^3, z^5$ appear (Prop 7.17). With $\sin z = z - \frac{z^3}{6} + \frac{z^5}{120} + O(z^7)$ and $\cos z = 1 - \frac{z^2}{2} + \frac{z^4}{24} + O(z^6)$, use $(1 - y)^{-1} = 1 + y + y^2 + \dots$:
> $$\left(1 - \left(\tfrac{z^2}{2} - \tfrac{z^4}{24} + O(z^6)\right)\right)^{-1} = 1 + \tfrac{z^2}{2} - \tfrac{z^4}{24} + \tfrac{z^4}{4} + O(z^6) = 1 + \frac{z^2}{2} + \frac{5z^4}{24} + O(z^6).$$
> Multiply by the sine series:
> $$\tan z = z + \left(\tfrac12 - \tfrac16\right)z^3 + \left(\tfrac{1}{120} - \tfrac{1}{12} + \tfrac{5}{24}\right)z^5 + O(z^7) = z + \frac13 z^3 + \frac{2}{15}z^5 + O(z^7). \quad \square$$

> [!note]- Remark 7.28 (complex sin and cos are unbounded)
> $\cos^2 z + \sin^2 z = 1$ does **not** mean $|\cos z|, |\sin z| \leq 1$: $\cos, \sin : \mathbb{C} \to \mathbb{C}$ are onto. For $w \in \mathbb{C}$,
> $$\sin z = w \iff \exp(iz)^2 - 2iw\exp(iz) - 1 = 0 \iff \exp(iz) = i \pm \sqrt{1 - w^2},$$
> which has a solution because $\exp$ takes every non-zero value. (If $w^2 = 1$, $\exp(iz) = i$ works.) Also $\cos z = \operatorname{Re}(\exp(iz))$ is generally false for non-real $z$.

> [!example]- Example 7.29: all solutions of $\sin z = 2$
> With $z = x + iy$: $\sin x\cosh y = 2$ and $\cos x\sinh y = 0$. If $y = 0$, $\sin x = 2$ is impossible. So $\cos x = 0$, $x = (2n+1)\frac\pi2$, and $2 = (-1)^n\cosh y$. So $n$ is even and $y = \pm\cosh^{-1}2$:
> $$z = (2n+1)\frac\pi2 \pm i\cosh^{-1}2 \quad (n \text{ even}). \quad \square$$

> [!example]- Example 7.30: $\cos z = \operatorname{Re}(\exp(iz))$ iff $z$ is real
> True for real $z$. With $z = x + iy$: $\cos z = \cos x\cosh y - i\sin x\sinh y$ and $\operatorname{Re}(\exp(iz)) = \operatorname{Re}(e^{-y + ix}) = e^{-y}\cos x$. Comparing: $e^{-y}\cos x = \cos x\cosh y$ and $\sin x\sinh y = 0$. If $y \neq 0$ then $\sin x = 0$, $x = n\pi$, $\cos x = (-1)^n \neq 0$, so $\cosh y = e^{-y} \iff e^{2y} = 1 \iff y = 0$, a contradiction. $\square$

> [!example]- Example 7.31: $|\exp(iz)| = 1$ iff $z$ is real
> $|\exp(iz)| = |e^{-y + ix}| = e^{-y} = 1 \iff y = 0$. $\square$

## Logarithmic and Binomial Series

> **Definition 7.32 (Logarithmic series)**
> $$\lambda(z) = \sum_{n=1}^\infty \frac{z^n}{n}, \qquad R = 1.$$

For $-1 < x < 1$: $\lambda'(x) = \sum x^{n-1} = \frac{1}{1-x}$ (Theorem 7.13). Let $\mu(x) = (1 - x)\exp(\lambda(x))$. Then $\mu'(x) = -\exp\lambda(x) + (1 - x)\lambda'(x)\exp\lambda(x) = 0$, so $\mu \equiv \mu(0) = 1$, and
$$\lambda(x) = \log\left(\frac{1}{1-x}\right) = -\log(1 - x).$$
In terms of a branch $L$ of the complex logarithm, $\lambda(z) = -L(1 - z)$ for $|z| < 1$.

> [!example]- Example 7.33: the binomial series for a general exponent
> For $\alpha, z \in \mathbb{C}$, $|z| < 1$, let $B(z, \alpha) = (1 + z)^\alpha = \exp(\alpha L(1 + z))$. It's analytic (a composition of analytic functions, not proved here), so write $B = \sum a_n z^n$. The chain rule gives
> $$B'(z, \alpha) = \frac{\alpha B(z, \alpha)}{1 + z}, \qquad \text{so} \quad (1 + z)B' = \alpha B.$$
> Comparing $z^n$ coefficients: $(n+1)a_{n+1} + na_n = \alpha a_n$, with $a_0 = 1$. So $a_{n+1} = \frac{\alpha - n}{n+1}a_n$ and
> $$a_n = \frac{\alpha(\alpha - 1)\cdots(\alpha - n + 1)}{n!} =: \binom{\alpha}{n}, \qquad (1 + z)^\alpha = \sum_{n=0}^\infty \binom{\alpha}{n} z^n.$$
> For $\alpha \in \mathbb{N}$ the sum is finite; otherwise it's an infinite series converging for $|z| < 1$. $\square$
