13/10/26: ""

## Relations

>**Definition 2.1 (Relation)**
	A relation $R$ on a set $S$ is a subset of $S \times S$.
	If $(a, b) \in R$, we write $aRb$.

>**Definition 2.5 (Reflexive, symmetric, anti-symmetric, transitive)**
	Let $S$ be a set, $R$ a relation on $S$ and $x, y, z \in S$. We say that
	1. $R$ is reflexive if $xRx$ for all $x$ in $S$,
	2. $R$ is symmetric if whenever $xRy$ then $yRx$,
	3. $R$ is anti-symmetric if whenever $xRy$ and $yRx$ then $x = y$,
	4. $R$ is transitive if whenever $xRy$ and $yRz$ then $xRz$.

## Equivalence Relations

>**Definition 2.8 (Equivalence relation)**
	A relation $R$ on a set $S$ is an equivalence relation if it is reflexive, symmetric and transitive.
	If $R$ is an equivalence relation, we denote it by $\sim$ (other symbols, including $\equiv$, are sometimes used).

>**Definition 2.10 (Equivalence class)**
	Given an equivalence relation $\sim$ on a set $S$, and given $x \in S$, the equivalence class of $x$, denoted $\bar{x}$ (or sometimes $[x]$), is the subset
$$\bar{x} = \{y \in S : y \sim x\}.$$

>**Definition 2.11 (Quotient set)**
	Given an equivalence relation $\sim$ on a set $S$, the set of equivalence classes is called the quotient set and is denoted $S/\sim$. We have
	$$S/\sim \; = \{\bar{x} : x \in S\}$$


$S/\sim$ is a set of sets.


>**Definition 2.12 (Partition)**
	A partition of a set $S$ is a collection of subsets $\{A_i \subseteq S : i \in I\}$, where $I$ is an indexing set, with the property that
	1. $A_i \neq \emptyset$ for all $i \in I$ (all the subsets are non-empty),
	2. $\bigcup_{i \in I} A_i = S$ (every member of $S$ lies in one of the subsets),
	3. $A_i \cap A_j = \emptyset$ for every $i \neq j$ (the subsets are disjoint).

The subsets are called the parts of the partition.

Quotient set is a partition.



