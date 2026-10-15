> **Simple Definition**
> 	Let X and Y be sets. A function from X to Y is an assignment of precisely one value in Y for each value in X.

> **Universal definition**
> 	Let X and Y be sets. A function f from X to Y is a subset of $X \times Y$ with the property that for each $x \in X$, there is exactly one value of $y \in Y$ such that (x,y) is in the subset.

## Function types
- **Injective**  -  one-to-one. More precisely, if $f(x_{1}) = f(x_{2})$,   $x_1 = x_2$.
- **Surjective**  -  image is codomain. More precisely, for every $y \in Y$ exists x such that $f(x) = y$.
- **Bijective**  -  injective and surjective.

## My take
- **Injective** - Unambiguous output BUT for inverse function.
- **Surjective** - well-defined (defined for all x) BUT for inverse function.
Also
	Surjectivity implies Y $\subseteq$ X
	Function definition implies X $\subseteq$ Y

> **Question**
> 	Does a bijective $f:\mathbb{N} \to \mathcal{P}(\mathbb{N})$ exist?
> **Answer**:
> 	No!
> **Proof:**
> 	Suppose for contradiction $f$ is surjective.
> 	Consider $R = \{n \in \mathbb{N}: n \notin f(n)\}$
> 	If $x \in R$, by definition of R, $x \notin R$
> 	If $x \notin R$, by definition of R, $x \in R$
> 	Thus contradiction.

> **Cardinality Definition 2.0**
> 	Sets S and T have the same cardinality, if and only if exists $f: S \to T$ that is bijective.

Always:
$|\mathcal{P}(A)| > |A|$


## Composition and Invertibility

**Definition 3.16 (Function composition)**
Given two functions $f : X \to Y$ and $g : Y \to Z$, the composition $g \circ f : X \to Z$ is defined by
$$(g \circ f)(x) = g(f(x)) \quad \text{for all } x \in X.$$
In general $f \circ g \neq g \circ f$ (composition is not commutative).

**Proposition 3.17 (Function composition is associative)**
Let $f : X \to Y$, $g : Y \to Z$, $h : Z \to W$ be three functions. Then
$$h \circ (g \circ f) = (h \circ g) \circ f.$$

**Proposition 3.18**
Let $f : X \to Y$ and $g : Y \to Z$ be functions.
1. If $f$ and $g$ are injective then so is $g \circ f$. Conversely, if $g \circ f$ is injective, then $f$ is injective, but $g$ need not be.
2. If $f$ and $g$ are surjective then so is $g \circ f$. Conversely, if $g \circ f$ is surjective, then $g$ is surjective, but $f$ need not be.

**Definition 3.19 (Invertible function, inverse function)**
A function $f : X \to Y$ is invertible if there exists a function $g : Y \to X$ such that $g \circ f = \text{id}_X$ and $f \circ g = \text{id}_Y$. The function $g$ is the inverse of $f$, and we write $g = f^{-1}$.
If $f$ is invertible then $f^{-1}$ is also invertible, and $(f^{-1})^{-1} = f$.

**Proposition 3.20**
If $f : X \to Y$ is invertible then its inverse is unique.

**Proposition 3.22**
Let $f : X \to Y$ and $g : Y \to Z$ be functions. If $f$ and $g$ are invertible, then $g \circ f$ is invertible, and
$$(g \circ f)^{-1} = f^{-1} \circ g^{-1}.$$

**Theorem 3.23**
A function $f : X \to Y$ is invertible if and only if it is bijective.

**Definition 3.24 (Left-invertible, right-invertible)**
A function $f : X \to Y$ is left-invertible if there exists a function $g : Y \to X$ such that $g \circ f = \text{id}_X$, and is right-invertible if there exists a function $h : Y \to X$ such that $f \circ h = \text{id}_Y$.

**Proposition 3.25**
1. A function $f : X \to Y$ is left-invertible if and only if it is injective.
2. A function $f : X \to Y$ is right-invertible if and only if it is surjective.