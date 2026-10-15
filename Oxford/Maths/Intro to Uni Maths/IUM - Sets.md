A set is a collections of objects. For each element, $x$, $x \in S$ denotes that $S$ contains $x$.

## Definitions

> **Definition 1.1 (Equal sets)**
> 	Two sets S and T are equal if and only if they contain the same elements, and in that case we can write S = T.

> **Definition 1.2 (Empty set)**
> 	The empty set is the set with no elements and is denoted by $\varnothing$.

> **Definition 1.3 (Subset)**
> 	A set A is said to be a subset of a set S if every element of A is an element of S. 
> 	We write A $\subseteq$ S.

> **Definition 1.4 (Proper subset)**
> 	If A $\subseteq$ S and A $\neq$ S, we call A a proper subset of S (A $\subset$ S).

> **Definition 1.5 (Power set)**
> 	The power set of a set A, denoted $\mathcal{P} (A)$, is the set of all subsets of A.

> **Definition 1.6 (Cartesian product)**
> 	Given sets A and B, the Cartesian product, denoted A $\times$ B, is the set of all ordered pairs with the first element of the pair coming from A and the second from B. That is, 
> 	$A \times B = \{(a,b) : a \in A  \text{ and }  b \in B\}$

> **Definition 1.7 (Cartesian product of n sets)**
> 	We define $A_{1} \times A_{2} \times \dots \times A_{n}$ to be the set of all ordered n-tuples $(a_{1},a_{2},...,a_{n})$, where
> 	$a_{i} \in A_{i}$ for $1\leq i\leq n$. If all the Ai are copies of A, we might write this Cartesian product as $A^n$.


> **Definition 1.13 (Union, intersection, complement, set difference)**
	Given subsets $A$ and $B$ of a set $S$, the union $A \cup B$ is the set consisting of those elements that are in $A$ or $B$ (or both), that is: $$A \cup B = \{x \in S : x \in A \text{ or } x \in B\}.$$The intersection $A \cap B$ is the set consisting of those elements that are in both $A$ and $B$, that is:  $$A \cap B = \{x \in S : x \in A \text{ and } x \in B\}.$$The complement of $A$, written $A^c$ or sometimes $A'$, is the subset consisting of those elements that are not in $A$, that is:
	$$A^c = \{x \in S : x \notin A\}.$$The set difference, or complement of $B$ in $A$, written $A \setminus B$, is the subset of $A$ consisting of those elements that are not in $B$, that is:
	$$A \setminus B = \{x \in A : x \notin B\}.$$Note that $A \setminus B = A \cap B^c$.


## Theorems

> **Theorem 1.18 (Double Inclusion)**
> 	Let A and B be two subsets of a set S. Then $A=B$ if and only if $A \subseteq B$ and $B \subseteq A$.

>  **Theorem 1.19 (Distributive Laws)**
> 	 Let $A, B, C$ be subsets of a set $S$. Then:
> 	 1. $A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$
> 	 2. $A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$

> **Proposition 1.20 (De Morgan's Laws)**
> 	Let $A$ and $B$ be subsets of a set $S$. Then:
> 	$(A \cup B)^c = A^c \cap B^c \quad \text{and} \quad (A \cap B)^c = A^c \cup B^c.$


## Cardinality

> **Definition (Finite set (recursive definition))**
> 	A set $S$ is finite if either
> 	1. it is the empty set  $\varnothing$, or
> 	2.  there exists $s \in S$ such that $S \setminus \{s\}$ is finite.

> **Definition (Cardinality of a finite set (recursive definition))**
> 	The cardinality of a finite set $S$, written $|S|$, is a natural number defined as follows;
> 	1. if $S = \varnothing$  then $|S| = 0$.
> 	2. if $S$ is not empty, then by definition of finiteness there exists $s \in S$ such that $S \setminus \{s\}$ is finite. If $|S \setminus \{s\}| = n$ then we define $|S| = n + 1$.

> **Theorem (Cardinality of a union)**
> 	Let $A$ and $B$ be finite sets. Then $|A \cup B| = |A| + |B| - |A \cap B|$.
> 	The proof is left as an exercise (see problem sheet).

> **Theorem (Subsets of a finite set)**
> 	If a set $A$ is finite with $|A| = n$, then its power set is finite and has $|\mathcal{P}(A)| = 2^n$.

[[IUM - Functions]]
> **Cardinality Definition 2.0 (Works for infinite sets)** 
> 	Sets S and T have the same cardinality, if and only if exists $f: S \to T$ that is bijective.

Always:
$|\mathcal{P}(A)| > |A|$

