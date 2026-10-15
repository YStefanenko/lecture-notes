12/10/26: "A ton of definitions"

## Natural Numbers

> **Definition 0.1 (Natural numbers)**
> 	A natural number is a member of the sequence 0,1,2,3,..., obtained by starting from 0 and adding 1 successively.

We write $\mathbb{N}$ = {0,1,2,3,...} for the set of all natural numbers.


## Operations 

> **Definition 0.2 (Less than or equal to)**
> 	Let m and n be natural numbers. We write $m \geq n$ to mean that there exists a natural number k such that $m + k = n$.

> **Definition 0.3 (Addition of natural numbers)**
> 	Define addition on $\mathbb{N}$ the rules that for all $m∈N$,
		1. $m+ 0 = m$, and
		2. for any $n∈N$, $m+ (n+ 1) = (m+ n) + 1$.

>**Definition 0.12 (Multiplication of natural numbers)**
	Define multiplication on $\mathbb{N}$ the rules that for all $m∈N$,
		1. $m \times 0 = 0$, and
		2. for any $n∈N$, $m×(n+ 1) = (m×n) + m$.

> **Definition 0.4 (Divides)**
> 	Given natural numbers m and n, we say that m divides n if there exists a natural number k such that $m×k= n$. We write $m|n$ if m divides n.

> **Definition 0.8 (Prime number)**
> 	A natural number p>1 is prime if no natural numbers except 1 and p divide p.

> **Definition 0.13 (Factorial)**
	Define factorial $n!$ on $\mathbb{N}$ the rules that
		1. $0! = 1$, and
		2. for any $n∈N$, $(n+ 1)! = n! ×(n+ 1)$.

Importantly: n + 0 = n and n × 1 = n  for all n ∈ N.

## Induction

> **Theorem 0.3 (Principle of Induction)**
	Let $P(n)$ be a family of statements indexed by the natural numbers. Suppose that
		3. $P(0)$ is true, and
		4. for any $n$, if $P(n)$ is true then $P(n+ 1)$ is also true.
	Then $P(n)$ is true for all natural numbers n.

> **Theorem 0.4 (Strong Form of Induction)**
	Let $P(n)$ be a family of statements indexed by the natural numbers. Suppose that
		5. $P(0)$ is true, and
		6. for any n, if $P(0), P(1),..., P(n)$ are true then $P(n+ 1)$ is also true.
	Then $P(n)$ is true for all natural numbers n.

> **Theorem 0.14 (Well-ordering property of the natural numbers)**
> 	Every non-empty subset of N has a least element.

Induction $<=>$ Well-ordering principle

## Properties

> **Proposition 0.11 (Associativity)**
> 	Addition on N is associative. 
> 	That is, for all $x,y,z ∈N$, $x+ (y+ z) = (x+ y) + z$.

Proved through induction.

> **Proposition 0.11 (Commutativity)**
> 	Addition on N is commutative. 
> 	That is, for all $x,y ∈N$, $x + y = y + x$.




