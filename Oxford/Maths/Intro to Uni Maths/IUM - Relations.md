13/10/26: ""

## Relations

>**Definition 2.1 (Relation)**
> A relation $R$ on a set $S$ is a subset of $S \times S$.
> If $(a, b) \in R$, we write $aRb$.

> [!example]- Examples 2.2 – 2.4
> **2.2**
> 1. $\leq$ on $\mathbb{R}$ is $\{(x,y) \in \mathbb{R}^2 : x \leq y\}$.
> 2. "Divides" on $\mathbb{N}$ is $\{(m,n) \in \mathbb{N}^2 : m | n\}$.
> 3. $\subseteq$ on $\mathcal{P}(S)$ is $\{(A,B) \in \mathcal{P}(S)^2 : A \subseteq B\}$.
> 
> **2.3 (trivial relations on any $S$)**
> 1. Everything's related: $xRy$ for all $x, y$ (i.e. $R = S \times S$).
> 2. Nothing's related: $R = \varnothing$.
> 3. Everything's related only to itself: $xRy \iff x = y$.
> 
> If $S = \varnothing$ these are all the same relation.
> 
> **2.4** On the set of chess players, $aRb$ iff $a$ has ever beaten $b$. $aRb$ and $bRa$ can both hold, or neither.

>**Definition 2.5 (Reflexive, symmetric, anti-symmetric, transitive)**
> Let $S$ be a set, $R$ a relation on $S$ and $x, y, z \in S$. We say that
> 1. $R$ is reflexive if $xRx$ for all $x$ in $S$,
> 2. $R$ is symmetric if whenever $xRy$ then $yRx$,
> 3. $R$ is anti-symmetric if whenever $xRy$ and $yRx$ then $x = y$,
> 4. $R$ is transitive if whenever $xRy$ and $yRz$ then $xRz$.

> [!example]- Example 2.6 (which properties hold?)
> | Relation on $\mathbb{R}$ | Reflexive | Symmetric | Anti-symmetric | Transitive |
> |---|---|---|---|---|
> | $\leq$ | ✓ | ✗ | ✓ | ✓ |
> | $<$ | ✗ | ✗ | ✓ | ✓ |
> | $\neq$ | ✗ | ✓ | ✗ | ✗ |
> | $=$ | ✓ | ✓ | ✓ | ✓ |
> 
> The chess relation (2.4) has none of these properties. Exercise: check the trivial relations of 2.3.

> [!example]- Example 2.7 (congruence mod $n$)
> Let $n \geq 2$ and define $R$ on $\mathbb{Z}$ by $aRb \iff a - b$ is a multiple of $n$. Then $R$ is reflexive, symmetric and transitive.
> 
> *Proof.*
> - Reflexive: $a - a = 0$ is a multiple of $n$.
> - Symmetric: if $a - b = kn$ then $b - a = (-k)n$.
> - Transitive: if $a - b = kn$ and $b - c = ln$ then $a - c = (k+l)n$. $\square$

## Equivalence Relations

>**Definition 2.8 (Equivalence relation)**
> A relation $R$ on a set $S$ is an equivalence relation if it is reflexive, symmetric and transitive.
> If $R$ is an equivalence relation, we denote it by $\sim$ (other symbols, including $\equiv$, are sometimes used).

> [!example]- Example 2.9 & A.10 (equivalence relations)
> 1. On $\mathbb{C}$: $z \sim w \iff |z| = |w|$.
> 2. On polygons in $\mathbb{R}^2$: congruence.
> 3. On differentiable functions $\mathbb{R} \to \mathbb{R}$: $f \sim g \iff f'(x) = g'(x)$ for all $x$.
> 4. Congruence mod $n$ on $\mathbb{Z}$ (Example 2.7), written $a \equiv b \pmod n$.
> 5. (A.10) On $\mathbb{R}$: $x \sim y \iff x - y \in \mathbb{Z}$.

>**Definition 2.10 (Equivalence class)**
> Given an equivalence relation $\sim$ on a set $S$, and given $x \in S$, the equivalence class of $x$, denoted $\bar{x}$ (or sometimes $[x]$), is the subset
$$\bar{x} = \{y \in S : y \sim x\}.$$

If $x \sim y$ then $[x] = [y]$ (prove it from the definition of an equivalence relation).
E.g. for congruence mod $n$: $\bar{1} = \{\dots, -n+1, 1, n+1, 2n+1, \dots\}$.

>**Definition 2.11 (Quotient set)**
> Given an equivalence relation $\sim$ on a set $S$, the set of equivalence classes is called the quotient set and is denoted $S/\sim$. We have
> $$S/\sim \; = \{\bar{x} : x \in S\}$$


$S/\sim$ is a set of sets.


>**Definition 2.12 (Partition)**
> A partition of a set $S$ is a collection of subsets $\{A_i \subseteq S : i \in I\}$, where $I$ is an indexing set, with the property that
> 1. $A_i \neq \emptyset$ for all $i \in I$ (all the subsets are non-empty),
> 2. $\bigcup_{i \in I} A_i = S$ (every member of $S$ lies in one of the subsets),
> 3. $A_i \cap A_j = \emptyset$ for every $i \neq j$ (the subsets are disjoint).

The subsets are called the parts of the partition.

Quotient set is a partition.

Conversely, any partition defines an equivalence relation: $x \sim y \iff x$ and $y$ lie in the same part. So equivalence relations and partitions correspond. (The proof that equivalence classes form a partition comes in Groups and Group Action.)

> [!example]- Example 2.13 (partition by college)
> Oxford students are partitioned by college: no college is empty, every student has a college, nobody is at two. The induced relation is $x \sim y \iff$ same college. "Equivalent" does not mean "equal".

> [!example]- Example A.14 ($\mathbb{R}/\mathbb{Z}$)
> With $x \sim y \iff x - y \in \mathbb{Z}$, the quotient $\mathbb{R}/\sim$ is written $\mathbb{R}/\mathbb{Z}$. Each class is $[x]$ for a unique $x \in [0,1)$.
> - $[x] \oplus [y] = [x + y]$ is well-defined.
> - $[x] \otimes [y] = [xy]$ is **not**: $[0.1] \otimes [0.1] = [0.01]$ but $[1.1] \otimes [0.1] = [0.11]$, although $[1.1] = [0.1]$.
> 
> See also [[IUM - Constructing Z from N]] and [[IUM - Bijective function for anything]].

> [!example]- Example 4.18 (modular arithmetic, $\mathbb{Z}_n$)
> Let $n \geq 2$ and $\mathbb{Z}_n = \{\bar 0, \bar 1, \dots, \overline{n-1}\}$ (classes of congruence mod $n$).
> 
> **(i)** $\bar x \otimes \bar y = \overline{x \times y}$ is well-defined.
> *Proof.* Suppose $\bar x_1 = \bar x_2$, $\bar y_1 = \bar y_2$, so $x_2 = x_1 + kn$, $y_2 = y_1 + ln$. Then
> $$x_2 y_2 = x_1 y_1 + (x_1 l + y_1 k + kln)n,$$
> so $\overline{x_2 y_2} = \overline{x_1 y_1}$. $\square$
> 
> **(ii)** Does every $\bar x \neq \bar 0$ have a multiplicative inverse ($\bar x \otimes \bar y = \bar 1$)?
> - Not in general: in $\mathbb{Z}_4$, $\bar 2$ has no inverse.
> - Yes if $n$ is prime: for $0 < x < n$, $x$ and $n$ are coprime, so by Bézout $xk + nl = 1$ for some integers $k, l$. Hence $\bar x \otimes \bar k = \bar 1$.
> 
> So $\mathbb{Z}_p$ is (part way to being) a finite field.



