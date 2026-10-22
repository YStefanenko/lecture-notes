## Define $i^2 = -1$

A complex number is a + bi where a, b are real. 
The set of complex numbers is denoted $\mathbb{C}$.
Real part, Re(z), is a and Imaginary part, Im(z), is b.

## Operations

- Addition: $(a + bi) + (c + di) = (a + c) + (b + d)i$
- Subtraction: $(a + bi) - (c + di) = (a - c) + (b - d)i$
- Multiplication: $(a + bi) \times (c + di) = (ac-bd) + (ad+bc)i$
- Division: $(a + bi) / (c + di) = \frac{(ac+bd) + (bc-ad)}{c^2+d^2}i$


**Definition:**   $\bar z$ stands for conjugate. $\bar z = a - bi$

**Proposition:** $z, w \in \mathbb{C}$
- $z \in \mathbb{R} \Leftrightarrow z=\bar z$
- $Re(z)=\frac{1}{2}(z+\bar z)$ and $\mathrm{Im}(z)=\frac{1}{2i}(z-\bar z)$
- $\overline {z \pm w} = \overline z \pm \overline w$
-  $\overline {z \times w} = \overline z \times \overline w$
- $\overline {z / w} = \overline z / \overline w$
- $z\times\overline z = (\mathrm{Re}(z))^2+(\mathrm{Im}(z))^2$


## Fundamental Theorem of Algebra

Given a polynomial $p(x) = a_{n}x^n+\dots+a_{1}x^1+a_{o}$ with $n\geq1$, and $a_n \in \mathbb{C}$, the roots of the equation $p(x) = 0$ are complex, denoted as $\{\gamma_{1}, \gamma_{2}, \dots \gamma_{n}\}$ where $p(x)=a_{n}(x-\gamma_{1})(x-\gamma_{2})\dots(x-\gamma_{n})$.


For polynomials with $a_{n} \in \mathbb{R}$, if $z_{0}$ is a root, $\overline{z_{0}}$ is also a root.

> [!proof]- Proof
> Given $z_{0}$ is a root, $p(z_{0}) = 0$.
> Consider $p(\overline{z_{0}}) = a_{n}\overline{z_{0}}^n+\dots+a_{1}\overline{z_{0}}^1+a_{o}$.
> Since $a_n \in \mathbb{R}$ , $a_{n} = \overline{a_{n}}$.
> Using properties of conjugates, find that $p(\overline{z_{0}}) = \overline{p(z_{0})} = 0$
> Thus $\overline{z_{0}}$ is also a root.

So, groups of $(x-z_{0})(x-\overline{z_{0}})$ can be combined to become quadratics with real coefficients.

Thus every polynomial can be expressed as $a_{n} \times$ a polynomial with real coefficients consisting of $(x-\alpha_{0})$ and $(x-z_{0})(x-\overline{z_{0}})$ (which has real coefficients when expanded). 


$z = a + bi = r(\cos(\theta)+ i \sin(\theta))$

**Definition:** 
$r$ is modulus. $|z|=r$
$\theta$ is argument. $arg(z) = \theta$

If $\theta \in [0, 2\pi]$, it is called the **principal argument**.

**Proposition**: $z=\cos(\theta)+i\sin(\theta)$ and  $w=\cos(\alpha)+i\sin(\alpha)$
- $z\times w=\cos(\theta + \alpha)+i\sin(\theta + \alpha)$ 
- $z \times \overline{z} = 1$


**Porposition:** For complex numbers z, w
- $|z \times w| = |z| \times |w|$
- $|z / w| = |z| / |w|$
- $arg(z \times w) = arg(z) +arg(w)$,   $z, w \neq 0$
- $arg(z / w) = arg(z) -arg(w)$,   $z, w \neq 0$
- $arg(\overline z) = -arg(z)$
- $z\times \overline z = |z^2|$
- $|\overline z| = |z|$
- $|z+w| \leq |z| + |w|$      -   triangle inequality
- $||z|-|w|| \leq |z-w|$    -   triangle inequality

**Theorem (De Moivre):**
For a real number $\theta$ and integer $n$:
$$(\cos\theta + i\sin\theta)^n = \cos(n\theta) + i\sin(n\theta)$$

**Proposition (Roots of Unity):**
The complex numbers that satisfy $z^n = 1$ are
$$z = \cos\left(\frac{2\pi k}{n}\right) + i\sin\left(\frac{2\pi k}{n}\right), \quad k = 0, 1, \dots, n-1$$

**Proof:**
$z$ satisfies $z^n = 1$ if and only if $|z^n| = 1$ and $\arg(z^n) = 2\pi k$ for some $k$.
This happens iff $|z|^n = 1$ and $n\arg(z) = 2\pi k$ for some $k$.
Thus $|z| = 1$ and $\arg(z) = \frac{2\pi k}{n}$.
Thus
$$z = 1 \times \left(\cos\left(\frac{2\pi k}{n}\right) + i\sin\left(\frac{2\pi k}{n}\right)\right)$$

## "Geometry" in $\mathbb{C}$

**Definition:** Given two complex numbers $z, w$, the distance between them is $|z - w|$.
Similarly, given three complex numbers $a, b, c$, the angle $\angle abc$ is
$$\arg(c - b) - \arg(a - b) = \arg\left(\frac{c - b}{a - b}\right)$$

**Functions $f: \mathbb{C} \to \mathbb{C}$**

* Translation: $z \mapsto z + a$
* Rotation: $z \mapsto z(\cos\theta + i\sin\theta)$
* Reflection: $z \mapsto \overline{z}$

These (and their compositions) are the only functions that preserve distances.

* Inversion and angle swap: $z \mapsto \frac{1}{z}$
* Rotation, expansion and overlap: $z \mapsto z^3$

## Exponents, Cosine and Sine

We define these functions on $\mathbb{C}$ by their power series expansions:
$$e^z = \exp(z) = \sum_{n=0}^{\infty} \frac{z^n}{n!}$$
$$\cos z = \sum_{n=0}^{\infty} \frac{(-1)^n z^{2n}}{(2n)!}$$
$$\sin z = \sum_{n=0}^{\infty} \frac{(-1)^n z^{2n+1}}{(2n+1)!}$$

**Euler's identity:** $\exp(iz) = \cos z + i\sin z$, proved by combining the expansions. In particular,
$$e^{i\theta} = \cos\theta + i\sin\theta$$

**Properties:**

* These are well-defined for all complex numbers
* $\exp'(z) = \exp(z)$, $\cos'(z) = -\sin(z)$, $\sin'(z) = \cos(z)$
* $\cos z$ is even, $\sin z$ is odd
* $\cos(z + 2\pi) = \cos z$ and $\sin(z + 2\pi) = \sin z$
* $\cos^2 z + \sin^2 z = 1$
* $\cos z$ and $\sin z$ are **not** bounded
* $\exp(z + w) = \exp(z)\exp(w)$

For $z = a + ib$:
$$\exp(z) = \exp(a)\exp(ib) = e^a(\cos b + i\sin b)$$

## Logarithm

$$\exp(\log z) = z$$
$$\log z = \log|z| + i\arg(z)$$
This is because the real part controls the modulus and the imaginary part controls the angle.