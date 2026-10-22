> **Simple Definition**
> Let X and Y be sets. A function from X to Y is an assignment of precisely one value in Y for each value in X.

> **Universal definition (Definition 3.1)**
> Let X and Y be sets. A function f from X to Y is a subset of $X \times Y$ with the property that for each $x \in X$, there is exactly one value of $y \in Y$ such that (x,y) is in the subset.
> In symbols (A.7): $\forall x \in X\ \exists!\, y \in Y$ s.t. $(x,y) \in f$.

> **Definition 3.2 (Domain, codomain)**
> For $f : X \to Y$, $X$ is the domain and $Y$ is the codomain.

> **Definition 3.3 (Equal functions)**
> $f : X \to Y$ and $g : X \to Y$ are equal ($f = g$) if and only if $f(x) = g(x)$ for every $x \in X$.

Functions must have the same domain *and* codomain to be equal.

**Well-defined:** a recipe is only a function if it assigns exactly one value to every input. $x \mapsto 1/x$ on $\mathbb{R}$ fails at 0; "$f(x) = y$ where $y^2 = x$" fails for $x < 0$ and is not unique for $x > 0$; $f(m/n) = n$ on $\mathbb{Q}$ fails because $f(2/3) = 3 \neq 6 = f(4/6)$.

> [!example]- Examples 3.4 – 3.6
> **3.4** Ceiling $\lceil \cdot \rceil : \mathbb{R} \to \mathbb{Z}$, the least integer $\geq x$. $\lceil 3.5 \rceil = 4$, $\lceil -4 \rceil = -4$; $\lceil 1.01 + 2.5i \rceil$ is undefined (not in the domain).
> 
> **3.5** $f : \mathbb{N} \to \mathbb{N}$, $n \mapsto n + 1$.
> 
> **3.6** Four *different* functions with the same formula $x^2$:
> $$f_1 : \mathbb{R} \to \mathbb{R},\quad f_2 : \mathbb{R} \to [0,\infty),\quad f_3 : [0,\infty) \to \mathbb{R},\quad f_4 : [0,\infty) \to [0,\infty).$$

> **Definition 3.7 (Image, range, pre-image)**
> Given $f : X \to Y$, the image (or range) of $f$ is $f(X) = \{f(x) : x \in X\} \subseteq Y$.
> For $A \subseteq X$, the image of $A$ is $f(A) = \{f(x) : x \in A\} \subseteq Y$.
> For $B \subseteq Y$, the pre-image of $B$ is $f^{-1}(B) = \{x : f(x) \in B\} \subseteq X$.

Careful: $f^{-1}(B)$ is a pre-image and exists even when $f$ has no inverse. Some authors say "range" for codomain.

> [!example]- Example 3.8
> $f_1$ (above): image $[0,\infty)$; $f_1([0,1]) = [0,1]$; $f_1^{-1}([0,1]) = [-1,1]$; $f_1^{-1}((-\infty,0]) = \{0\}$.
> $f_4$: image $[0,\infty)$; $f_4^{-1}([0,1]) = [0,1]$; $f_4^{-1}((-\infty,0])$ is undefined, as $(-\infty,0] \not\subseteq$ codomain.

> **Proposition 3.9**
> Let $f : X \to Y$.
> 1. For any $A \subseteq X$, $A \subseteq f^{-1}(f(A))$, but not equality in general.
> 2. For any $C \subseteq Y$, $f(f^{-1}(C)) \subseteq C$, but not equality in general.

> [!proof]- Proof
> (1) Elements of $A$ map into $f(A)$, so $A \subseteq f^{-1}(f(A))$. Counterexample to equality: $f(x) = x^2$ on $\mathbb{R}$, $A = \{1\}$: $f^{-1}(f(A)) = \{-1, 1\} \neq A$.
> 
> (2) $f$ maps $f^{-1}(C)$ into $C$ by definition. Counterexample: same $f$, $C = \{-1\}$: $f^{-1}(C) = \varnothing$, so $f(f^{-1}(C)) = \varnothing \neq C$. $\square$

> **Definition 3.10 (Restriction of a function)**
> Given $f : X \to Y$ and $A \subseteq X$, the restriction of $f$ to $A$ is $f|_A : A \to Y$, $f|_A(x) = f(x)$ for all $x \in A$.

> **Definition 3.11 (Identity function)**
> For a set $X$, $\text{id}_X : X \to X$ is defined by $\text{id}_X(x) = x$. Also written $1_X$, or just $\text{id}$.

## Function types
- **Injective**  -  one-to-one. More precisely, if $f(x_{1}) = f(x_{2})$,   $x_1 = x_2$.
- **Surjective**  -  image is codomain. More precisely, for every $y \in Y$ exists x such that $f(x) = y$.
- **Bijective**  -  injective and surjective.

(Definition 3.12. A bijective function is a *bijection*; similarly *injection*, *surjection*. In words: injective means each element of the image has a unique pre-image; bijective means each element of the codomain has a unique pre-image.)

In quantifiers (Example 4.8): injective is $\forall x_1, x_2 \in X,\ f(x_1) = f(x_2) \Rightarrow x_1 = x_2$; surjective is $\forall y \in Y\ \exists x \in X$ s.t. $f(x) = y$.

> [!example]- Examples 3.13, 3.14 & Lecture 0
> **3.13** Ceiling $\mathbb{R} \to \mathbb{Z}$ is surjective ($\lceil n \rceil = n$) but not injective ($\lceil n - \tfrac12 \rceil = n$ too).
> 
> **3.14** With the $f_i$ from Example 3.6:
> - $f_1$: not injective ($f(-1) = f(1)$), not surjective (nothing maps to $y < 0$).
> - $f_2$: surjective, not injective.
> - $f_3$: injective, not surjective.
> - $f_4$: bijective.
> 
> **Lecture 0:** $f : \mathcal{P}(\mathbb{N}) \to \mathbb{N}$ sending a non-empty subset to its least element and $\varnothing \mapsto 0$ is well-defined (by well-ordering). It is surjective ($f(\{n\}) = n$) but not injective ($f(\{n, n+1\}) = n$).

> [!mytake]- My take
> - **Injective** - Unambiguous output BUT for inverse function.
> - **Surjective** - well-defined (defined for all x) BUT for inverse function.
> 
> Also
> - Surjectivity implies Y $\subseteq$ X
> - Function definition implies X $\subseteq$ Y

> **Question**
> Does a bijective $f:\mathbb{N} \to \mathcal{P}(\mathbb{N})$ exist?
> **Answer**:
> No! (Not even a surjective one.)

> [!proof]- Proof
> Suppose for contradiction $f$ is surjective.
> Consider $R = \{n \in \mathbb{N}: n \notin f(n)\}$.
> Since $f$ is surjective, there is $x \in \mathbb{N}$ with $f(x) = R$.
> If $x \in R$, by definition of R, $x \notin f(x) = R$.
> If $x \notin R$, then $x \notin f(x)$, so by definition of R, $x \in R$.
> Thus contradiction. $\square$
> 
> Replacing $\mathbb{N}$ by any set $S$ shows $S$ and $\mathcal{P}(S)$ never have the same cardinality.

> **Cardinality Definition 2.0**
> Sets S and T have the same cardinality, if and only if exists $f: S \to T$ that is bijective.

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

> [!proof]- Proof
> For $x \in X$: $(h \circ (g \circ f))(x) = h(g(f(x))) = ((h \circ g) \circ f)(x)$. $\square$

> [!example]- Example: composition is not commutative
> $f(x) = x^2$, $g(x) = e^x$ on $\mathbb{R}$: $(f \circ g)(x) = e^{2x} \neq e^{x^2} = (g \circ f)(x)$.

**Proposition 3.18**
Let $f : X \to Y$ and $g : Y \to Z$ be functions.
1. If $f$ and $g$ are injective then so is $g \circ f$. Conversely, if $g \circ f$ is injective, then $f$ is injective, but $g$ need not be.
2. If $f$ and $g$ are surjective then so is $g \circ f$. Conversely, if $g \circ f$ is surjective, then $g$ is surjective, but $f$ need not be.

> [!proof]- Proof of (1) ((2) is an exercise)
> Suppose $(g \circ f)(x_1) = (g \circ f)(x_2)$. Injectivity of $g$ gives $f(x_1) = f(x_2)$, then injectivity of $f$ gives $x_1 = x_2$. So $g \circ f$ is injective.
> 
> Now suppose $g \circ f$ is injective and $f(x_1) = f(x_2)$. Applying $g$: $g(f(x_1)) = g(f(x_2))$, so $x_1 = x_2$. So $f$ is injective.
> 
> $g$ need not be injective: $X = Z = \{0\}$, $Y = \mathbb{R}$, $f(0) = 0$, $g(y) = 0$ for all $y$. Then $g \circ f$ is injective but $g$ is not. $\square$

**Definition 3.19 (Invertible function, inverse function)**
A function $f : X \to Y$ is invertible if there exists a function $g : Y \to X$ such that $g \circ f = \text{id}_X$ and $f \circ g = \text{id}_Y$. The function $g$ is the inverse of $f$, and we write $g = f^{-1}$.
If $f$ is invertible then $f^{-1}$ is also invertible, and $(f^{-1})^{-1} = f$.

**Proposition 3.20**
If $f : X \to Y$ is invertible then its inverse is unique.

> [!proof]- Proof
> Let $g_1, g_2$ both satisfy $g_i \circ f = \text{id}_X$, $f \circ g_i = \text{id}_Y$. By associativity,
> $$g_1 = g_1 \circ \text{id}_Y = g_1 \circ (f \circ g_2) = (g_1 \circ f) \circ g_2 = \text{id}_X \circ g_2 = g_2. \quad \square$$

> [!example]- Example 3.21
> Let $F$ be the set of invertible functions $X \to Y$. Then $T : F \to F$, $T(f) = f^{-1}$ is a function, and $T \circ T = \text{id}_F$ (it is its own inverse).

**Proposition 3.22**
Let $f : X \to Y$ and $g : Y \to Z$ be functions. If $f$ and $g$ are invertible, then $g \circ f$ is invertible, and
$$(g \circ f)^{-1} = f^{-1} \circ g^{-1}.$$

> [!proof]- Proof
> Using associativity:
> $$(f^{-1} \circ g^{-1}) \circ (g \circ f) = f^{-1} \circ (g^{-1} \circ g) \circ f = f^{-1} \circ \text{id}_Y \circ f = f^{-1} \circ f = \text{id}_X,$$
> $$(g \circ f) \circ (f^{-1} \circ g^{-1}) = g \circ (f \circ f^{-1}) \circ g^{-1} = g \circ \text{id}_Y \circ g^{-1} = g \circ g^{-1} = \text{id}_Z.$$
> So $f^{-1} \circ g^{-1}$ is the inverse of $g \circ f$. $\square$

**Theorem 3.23**
A function $f : X \to Y$ is invertible if and only if it is bijective.

> [!proof]- Proof
> ($\Rightarrow$) *Injective:* if $f(x_1) = f(x_2)$, apply $f^{-1}$: $x_1 = f^{-1}(f(x_1)) = f^{-1}(f(x_2)) = x_2$. *Surjective:* for $y \in Y$, $f(f^{-1}(y)) = y$.
> 
> ($\Leftarrow$) For each $y \in Y$, surjectivity gives some $x$ with $f(x) = y$, and injectivity makes it unique. Define $g(y) = $ that $x$. This is well-defined, and $g(f(x)) = x$, $f(g(y)) = y$. So $g = f^{-1}$. $\square$

**Definition 3.24 (Left-invertible, right-invertible)**
A function $f : X \to Y$ is left-invertible if there exists a function $g : Y \to X$ such that $g \circ f = \text{id}_X$, and is right-invertible if there exists a function $h : Y \to X$ such that $f \circ h = \text{id}_Y$.

**Proposition 3.25**
1. A function $f : X \to Y$ is left-invertible if and only if it is injective.
2. A function $f : X \to Y$ is right-invertible if and only if it is surjective.

(Proof left as an exercise in the notes.)

## Images and pre-images of intersections

> [!example]- Example 4.17
> Let $f : X \to Y$, $A, B \subseteq X$, $C, D \subseteq Y$.
> 
> **(i) $f(A \cap B) = f(A) \cap f(B)$: false.** Counterexample: $f(x) = 3$ on $\mathbb{R}$, $A = \{0\}$, $B = \{1\}$. Then $f(A \cap B) = \varnothing$ but $f(A) \cap f(B) = \{3\}$. (What *is* true: $f(A \cap B) \subseteq f(A) \cap f(B)$.)
> 
> **(ii) $f^{-1}(C \cap D) = f^{-1}(C) \cap f^{-1}(D)$: true.**
> *Proof.* $x \in f^{-1}(C \cap D) \iff f(x) \in C$ and $f(x) \in D \iff x \in f^{-1}(C)$ and $x \in f^{-1}(D)$. $\square$
> 
> Tip: try extreme cases first (disjoint sets, constant functions).
