A set is a collections of objects. For each element, $x$, $x \in S$ denotes that $S$ contains $x$.

## Definitions

> **Definition 1.1 (Equal sets)**
> Two sets S and T are equal if and only if they contain the same elements, and in that case we can write S = T.

> **Definition 1.2 (Empty set)**
> The empty set is the set with no elements and is denoted by $\varnothing$.

> **Definition 1.3 (Subset)**
> A set A is said to be a subset of a set S if every element of A is an element of S. 
> We write A $\subseteq$ S.

> **Definition 1.4 (Proper subset)**
> If A $\subseteq$ S and A $\neq$ S, we call A a proper subset of S (A $\subset$ S).

Careful: many authors use $\subset$ to mean the same as $\subseteq$. $A \subsetneq S$ is the unambiguous "proper subset".

> [!example]- Examples 1.5 & 1.6 (set-builder notation, sets of sets)
> **1.5**
> 1. Even naturals: $\{n \in \mathbb{N} : n \text{ is divisible by } 2\}$.
> 2. $\{n \in \mathbb{N} : n^2 < 0\} = \varnothing$.
> 3. $\{n \in \mathbb{N} : 3|n,\ 5|n,\ 7|n\} = \{n \in \mathbb{N} : 105|n\}$ (commas mean all conditions hold).
> 
> **1.6** Each of these has exactly two elements:
> $$A = \{\mathbb{N}, 3\}, \quad B = \{\{1,2\},\{1,3\},\{1,2\}\}, \quad C = \{\varnothing, \{\varnothing\}\}.$$
> $\mathbb{N} \in A$ but $\mathbb{N} \not\subseteq A$. $1 \notin B$. $\varnothing \in C$ and also $\varnothing \subseteq C$ (indeed $\varnothing \subseteq S$ for every $S$).
> 
> Don't confuse $a$ with $\{a\}$.

> **Definition 1.7 (Intervals)**
> Given $a, b \in \mathbb{R}$ with $a \leq b$, the bounded intervals are
> $$(a,b) = \{x : a < x < b\},\quad [a,b] = \{x : a \leq x \leq b\},\quad [a,b) = \{x : a \leq x < b\},\quad (a,b] = \{x : a < x \leq b\},$$
> and the unbounded intervals are
> $$(a,\infty) = \{x : a < x\},\quad [a,\infty) = \{x : a \leq x\},\quad (-\infty,a) = \{x : x < a\},\quad (-\infty,a] = \{x : x \leq a\}$$
> (all $x \in \mathbb{R}$).
> **Open:** $(a,b)$, $(a,\infty)$, $(-\infty,a)$. **Closed:** $[a,b]$, $[a,\infty)$, $(-\infty,a]$.

Open and closed are not opposites: $(a,b]$ is neither. If $a = b$, $[a,a] = \{a\}$ and the others are $\varnothing$. Also $\infty \notin \mathbb{R}$.

> **Definition 1.8 (Power set)**
> The power set of a set A, denoted $\mathcal{P} (A)$, is the set of all subsets of A.

> [!example]- Example 1.9
> 1. $A = \{0,1\}$: $\mathcal{P}(A) = \{\varnothing, \{0\}, \{1\}, \{0,1\}\}$.
> 2. $\mathcal{P}(\mathbb{N})$ contains the evens, $\{0,1\}$, the primes $p$ with $p+2$ prime, $\varnothing$, …

Ordered pairs: $(a_1,b_1) = (a_2,b_2) \iff a_1 = a_2$ and $b_1 = b_2$. Order matters, unlike in sets.

> **Definition 1.10 (Cartesian product)**
> Given sets A and B, the Cartesian product, denoted A $\times$ B, is the set of all ordered pairs with the first element of the pair coming from A and the second from B. That is, 
> $A \times B = \{(a,b) : a \in A  \text{ and }  b \in B\}$

Notation: $A \times A = A^2$. E.g. $\mathbb{R}^2$ is the plane (Example 1.11).

> **Definition 1.12 (Cartesian product of n sets)**
> We define $A_{1} \times A_{2} \times \dots \times A_{n}$ to be the set of all ordered n-tuples $(a_{1},a_{2},...,a_{n})$, where
> $a_{i} \in A_{i}$ for $1\leq i\leq n$. If all the Ai are copies of A, we might write this Cartesian product as $A^n$.

> [!example]- Remark: Russell's paradox
> Let $H = \{\text{sets } S : S \notin S\}$. Is $H \in H$?
> - If $H \notin H$, then $H$ meets the criterion, so $H \in H$.
> - If $H \in H$, then by the criterion $H \notin H$.
> 
> Either way we get a contradiction. Resolution: $H$ is not a set. Our naive notion of "collection" is too loose (axiomatic set theory, ZF, rules it out).


> **Definition 1.13 (Union, intersection, complement, set difference)**
> Given subsets $A$ and $B$ of a set $S$, the union $A \cup B$ is the set consisting of those elements that are in $A$ or $B$ (or both), that is: $$A \cup B = \{x \in S : x \in A \text{ or } x \in B\}.$$The intersection $A \cap B$ is the set consisting of those elements that are in both $A$ and $B$, that is:  $$A \cap B = \{x \in S : x \in A \text{ and } x \in B\}.$$The complement of $A$, written $A^c$ or sometimes $A'$, is the subset consisting of those elements that are not in $A$, that is:
> $$A^c = \{x \in S : x \notin A\}.$$The set difference, or complement of $B$ in $A$, written $A \setminus B$, is the subset of $A$ consisting of those elements that are not in $B$, that is:
> $$A \setminus B = \{x \in A : x \notin B\}.$$Note that $A \setminus B = A \cap B^c$.

> **Definition 1.14 (Disjoint sets)**
> Two sets $A$ and $B$ are disjoint if $A \cap B = \varnothing$, that is, they have no element in common.

**Indexed unions and intersections.** For a family of subsets $\{A_i : i \in I\}$ ($I$ an indexing set, possibly infinite):
$$\bigcap_{i \in I} A_i = \{x \in S : x \in A_i \text{ for all } i \in I\}, \qquad \bigcup_{i \in I} A_i = \{x \in S : x \in A_i \text{ for at least one } i \in I\}.$$

> [!example]- Examples 1.15 – 1.17
> **1.15** $S$ = Oxford students, $A$ = maths students, $B$ = students at your college. $A \cap B$ = maths students at your college; $A \cup B$ = at your college or doing maths; $B^c$ = students at other colleges; $A \setminus B$ = maths students at other colleges.
> 
> **1.16** The irrationals are $\mathbb{R} \setminus \mathbb{Q}$.
> 
> **1.17** Some authors' $\mathbb{N}$ is our $\mathbb{N} \setminus \{0\}$. Note the braces: $A \setminus B$ needs $B$ to be a set.


## Theorems

> **Proposition 1.18 (Double Inclusion)**
> Let A and B be two subsets of a set S. Then $A=B$ if and only if $A \subseteq B$ and $B \subseteq A$.

> [!proof]- Proof
> ($\Rightarrow$) If $A = B$, every element of $A$ is in $B$, so $A \subseteq B$; similarly $B \subseteq A$.
> 
> ($\Leftarrow$) Suppose $A \subseteq B$ and $B \subseteq A$. For any $x \in S$: if $x \in A$ then $x \in B$ (as $A \subseteq B$); if $x \notin A$ then $x \notin B$ (as $B \subseteq A$). So $x \in A \iff x \in B$, i.e. $A = B$. $\square$
> 
> *Symbolic version (Example 4.11):*
> $$\begin{aligned} A = B &\iff \forall x \in S\ (x \in A \Leftrightarrow x \in B) \\ &\iff \forall x \in S\ (x \in A \Rightarrow x \in B \text{ and } x \in B \Rightarrow x \in A) \\ &\iff \forall x \in S\ (x \in A \Rightarrow x \in B) \text{ and } \forall x \in S\ (x \in B \Rightarrow x \in A) \\ &\iff A \subseteq B \text{ and } B \subseteq A. \end{aligned}$$

>  **Proposition 1.19 (Distributive Laws)**
> Let $A, B, C$ be subsets of a set $S$. Then:
> 1. $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
> 2. $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$

> [!proof]- Proof of (1) by double inclusion
> (LHS $\subseteq$ RHS) Let $x \in A \cup (B \cap C)$. If $x \in A$ then $x \in A \cup B$ and $x \in A \cup C$. If $x \in B \cap C$ then $x \in B \subseteq A \cup B$ and $x \in C \subseteq A \cup C$. Either way $x \in$ RHS.
> 
> (RHS $\subseteq$ LHS) Let $x \in (A \cup B) \cap (A \cup C)$. If $x \in A$, then $x \in$ LHS. If $x \notin A$, then $x \in A \cup B$ forces $x \in B$, and $x \in A \cup C$ forces $x \in C$, so $x \in B \cap C \subseteq$ LHS.
> 
> By double inclusion the sets are equal. (2) is similar (exercise). $\square$

> **Proposition 1.20 (De Morgan's Laws)**
> Let $A$ and $B$ be subsets of a set $S$. Then:
> $(A \cup B)^c = A^c \cap B^c \quad \text{and} \quad (A \cap B)^c = A^c \cup B^c.$

> [!proof]- Proof (first law, by double inclusion)
> If $x \in (A \cup B)^c$, then $x$ is in neither $A$ nor $B$, so $x \in A^c$ and $x \in B^c$, i.e. $x \in A^c \cap B^c$.
> Conversely if $x \in A^c \cap B^c$ then $x \notin A$ and $x \notin B$, so $x \notin A \cup B$, i.e. $x \in (A \cup B)^c$.
> By double inclusion they are equal. The second law is similar (exercise). $\square$

> [!proof]- Proof (both laws, by truth table)
> Rows: whether $x \in A$, $x \in B$.
> 
> | $A$ | $B$ | $A\cap B$ | $(A\cap B)^c$ | $A \cup B$ | $(A\cup B)^c$ | $A^c$ | $B^c$ | $A^c \cup B^c$ | $A^c \cap B^c$ |
> |---|---|---|---|---|---|---|---|---|---|
> | F | F | F | T | F | T | T | T | T | T |
> | F | T | F | T | T | F | T | F | T | F |
> | T | F | F | T | T | F | F | T | T | F |
> | T | T | T | F | T | F | F | F | F | F |
> 
> The $(A\cap B)^c$ and $A^c \cup B^c$ columns agree, as do $(A\cup B)^c$ and $A^c \cap B^c$. $\square$

De Morgan generalises to any family $\{A_i : i \in I\}$:
$$\Big(\bigcap_{i \in I} A_i\Big)^c = \bigcup_{i \in I} A_i^c, \qquad \Big(\bigcup_{i \in I} A_i\Big)^c = \bigcap_{i \in I} A_i^c.$$


## Cardinality

> **Definition 1.21 (Finite set (recursive definition))**
> A set $S$ is finite if either
> 1. it is the empty set  $\varnothing$, or
> 2.  there exists $s \in S$ such that $S \setminus \{s\}$ is finite.
> 
> Any set that is not finite is infinite.

> **Definition 1.22 (Cardinality of a finite set (recursive definition))**
> The cardinality of a finite set $S$, written $|S|$, is a natural number defined as follows;
> 1. if $S = \varnothing$  then $|S| = 0$.
> 2. if $S$ is not empty, then by definition of finiteness there exists $s \in S$ such that $S \setminus \{s\}$ is finite. If $|S \setminus \{s\}| = n$ then we define $|S| = n + 1$.

> **Proposition 1.23 (Cardinality of a union)**
> Let $A$ and $B$ be finite sets. Then $|A \cup B| = |A| + |B| - |A \cap B|$.
> The proof is left as an exercise (see problem sheet).

> **Proposition 1.24 (Subsets of a finite set)**
> If a set $A$ is finite with $|A| = n$, then its power set is finite and has $|\mathcal{P}(A)| = 2^n$.

> [!proof]- Proof (induction on $n$)
> $n = 0$: $A = \varnothing$ has one subset, $\varnothing$, so $|\mathcal{P}(A)| = 1 = 2^0$.
> 
> Suppose $|\mathcal{P}(S)| = 2^n$ whenever $|S| = n$, and let $|A| = n+1$. Then there is $a \in A$ with $A' = A \setminus \{a\}$, $|A'| = n$. Every subset of $A$ either contains $a$ or not, so
> $$\mathcal{P}(A) = \mathcal{P}(A') \cup \{S \cup \{a\} : S \in \mathcal{P}(A')\}.$$
> These are disjoint, each of size $2^n$, so by Prop 1.23 $|\mathcal{P}(A)| = 2^n + 2^n = 2^{n+1}$. $\square$
> 
> *Intuition:* building a subset = $|A|$ independent yes/no choices, giving $2^{|A|}$ subsets.

> **Definition 3.15 (Finite set, cardinality of a set (with bijections))**
> The empty set is finite with $|\varnothing| = 0$. A non-empty set $S$ is finite with $|S| = n \in \mathbb{N}$ if and only if there is a bijection from $S$ to $\{1, 2, \dots, n\}$.

For finite $X, Y$ and $f : X \to Y$: injective $\Rightarrow |Y| \geq |X|$ (pigeonhole principle); surjective $\Rightarrow |Y| \leq |X|$; so bijective $\Rightarrow |X| = |Y|$.

[[IUM - Functions]]
> **Cardinality Definition 2.0 (Works for infinite sets)** 
> Sets S and T have the same cardinality, if and only if exists $f: S \to T$ that is bijective.

Always:
$|\mathcal{P}(A)| > |A|$

Named cardinalities: $|\varnothing| = 0$; $|\{1,\dots,n\}| = n$; $|\mathbb{N}| = \aleph_0$ (also $|\mathbb{Z}| = |\mathbb{Q}| = \aleph_0$); $|\mathcal{P}(\mathbb{N})| = \mathfrak{c} = |\mathbb{R}|$ (proof in Analysis).
$\mathbb{N}, \mathcal{P}(\mathbb{N}), \mathcal{P}(\mathcal{P}(\mathbb{N})), \dots$ are infinitely many infinite sets, no two with the same cardinality.

