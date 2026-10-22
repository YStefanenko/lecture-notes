12/10/26: "A ton of definitions"

## Natural Numbers

> **Definition 0.1 (Natural numbers)**
> A natural number is a member of the sequence 0,1,2,3,..., obtained by starting from 0 and adding 1 successively.

We write $\mathbb{N}$ = {0,1,2,3,...} for the set of all natural numbers.


## Operations 

> **Definition 0.2 (Less than or equal to)**
> Let m and n be natural numbers. We write $m \leq n$ to mean that there exists a natural number k such that $m + k = n$.

> **Definition 0.10 (Addition of natural numbers)**
> Define addition on $\mathbb{N}$ the rules that for all $m∈N$,
> 1. $m+ 0 = m$, and
> 2. for any $n∈N$, $m+ (n+ 1) = (m+ n) + 1$.

>**Definition 0.12 (Multiplication of natural numbers)**
> Define multiplication on $\mathbb{N}$ the rules that for all $m∈N$,
> 1. $m \times 0 = 0$, and
> 2. for any $n∈N$, $m×(n+ 1) = (m×n) + m$.

> **Definition 0.7 (Divides)**
> Given natural numbers m and n, we say that m divides n if there exists a natural number k such that $m×k= n$. We write $m|n$ if m divides n.

> **Definition 0.8 (Prime number)**
> A natural number p>1 is prime if no natural numbers except 1 and p divide p.

> **Proposition 0.9**
> Every natural number greater than 1 may be expressed as a product of one or more prime numbers.

> [!proof]- Proof (strong induction)
> Let $P(n)$ be the statement that $n$ may be expressed as a product of primes. $P(2)$ holds since 2 is prime.
> 
> Let $n \geq 2$ and suppose $P(m)$ holds for all $m < n$. If $n$ is prime, it is the product of one prime, $n$. If not, there exist $r, s > 1$ with $n = rs$. By the inductive hypothesis $r$ and $s$ are products of primes, so $n = rs$ is too.
> 
> By strong induction, $P(n)$ holds for all $n \geq 2$. $\square$

> **Definition 0.13 (Factorial)**
> Define factorial $n!$ on $\mathbb{N}$ the rules that
> 1. $0! = 1$, and
> 2. for any $n∈N$, $(n+ 1)! = n! ×(n+ 1)$.

> **Definition 0.15 (Binomial coefficient)**
> For natural numbers $n$ and $k$, we define the binomial coefficient
> $$\binom{n}{k} = \frac{n!}{k!\,(n-k)!} \quad \text{for } 0 \leq k \leq n.$$
> Read as "$n$ choose $k$", also written ${}^nC_k$. By convention $\binom{n}{k} = 0$ if $k > n$.

It counts the ways of choosing $k$ elements from a set of size $n$ (Pascal's triangle: row $n$ holds the non-zero $\binom{n}{k}$).

Importantly: n + 0 = n and n × 1 = n  for all n ∈ N.

## Induction

> **Theorem 0.3 (Principle of Induction)**
> Let $P(n)$ be a family of statements indexed by the natural numbers. Suppose that
> 1. $P(0)$ is true, and
> 2. for any $n$, if $P(n)$ is true then $P(n+ 1)$ is also true.
> 
> Then $P(n)$ is true for all natural numbers n.

> [!proof]- Proof (from the well-ordering property)
> Let $S$ be the set of $n$ such that $P(n)$ is false. Suppose for contradiction $S \neq \varnothing$. By well-ordering, $S$ has a least element. It isn't 0, since $P(0)$ is true, so it is $n+1$ for some $n \in \mathbb{N}$. As $n+1$ is least, $n \notin S$, so $P(n)$ holds. Then by (ii) $P(n+1)$ holds, contradicting $n+1 \in S$. So $S = \varnothing$. $\square$

> [!example]- Example: Proposition 0.4
> **Proposition 0.4.** For any $n \in \mathbb{N}$, $\displaystyle\sum_{k=0}^{n} k = \frac{n(n+1)}{2}$.
> 
> *Proof.* $P(0)$: both sides are 0. Suppose $P(n)$ holds. Then
> $$\sum_{k=0}^{n+1} k = \sum_{k=0}^{n} k + (n+1) = \frac{n(n+1)}{2} + (n+1) = \frac{(n+1)(n+2)}{2},$$
> using the inductive hypothesis. This is $P(n+1)$, so by induction $P(n)$ holds for all $n$. $\square$

> **Corollary 0.5 (Induction from $N$)**
> Let $N$ be an integer and let $P(n)$ be a family of statements indexed by integers $n \geq N$. Suppose that
> 1. $P(N)$ is true, and
> 2. for any $n \geq N$, if $P(n)$ is true then $P(n+1)$ is also true.
> 
> Then $P(n)$ is true for all $n \geq N$.

> [!proof]- Proof
> Apply the principle of induction to $Q(n) = P(n + N)$ for $n \in \mathbb{N}$. $\square$

> **Theorem 0.6 (Strong Form of Induction)**
> Let $P(n)$ be a family of statements indexed by the natural numbers. Suppose that
> 1. $P(0)$ is true, and
> 2. for any n, if $P(0), P(1),..., P(n)$ are true then $P(n+ 1)$ is also true.
> 
> Then $P(n)$ is true for all natural numbers n.

> [!proof]- Proof
> Let $Q(n)$ be the statement "$P(k)$ holds for $k = 0, 1, \dots, n$". The hypotheses say exactly that $Q(0)$ holds and $Q(n) \Rightarrow Q(n+1)$. By ordinary induction $Q(n)$ holds for all $n$, hence so does $P(n)$. $\square$

> **Theorem 0.14 (Well-ordering property of the natural numbers)**
> Every non-empty subset of N has a least element.

> [!proof]- Proof (by contradiction + strong induction)
> Suppose $S \subseteq \mathbb{N}$ is non-empty with no least element. Let $S^* = \mathbb{N} \setminus S$ and let $P(n)$ be "$n \in S^*$".
> - $P(0)$: if $0 \in S$ it would be the least element, so $0 \in S^*$.
> - Suppose $P(0), \dots, P(n)$ hold. If $n+1 \in S$ it would be least (everything smaller is not in $S$), so $n+1 \in S^*$.
> 
> By strong induction $S^* = \mathbb{N}$, so $S = \varnothing$, a contradiction. $\square$

Induction $<=>$ Well-ordering principle

## Binomial Theorem

> **Lemma 0.16 (Pascal's Triangle)**
> Let $n$ and $k$ be natural numbers with $1 \leq k \leq n$. Then
> $$\binom{n}{k-1} + \binom{n}{k} = \binom{n+1}{k}.$$

> [!proof]- Proof
> Put the LHS over a common denominator:
> $$\frac{n!}{(k-1)!(n-k+1)!} + \frac{n!}{k!(n-k)!} = \frac{n!\,\big(k + (n-k+1)\big)}{k!(n-k+1)!} = \frac{(n+1)!}{k!(n+1-k)!} = \binom{n+1}{k}. \quad \square$$
> (This lemma + induction shows binomial coefficients are integers.)

> **Theorem 0.17 (Binomial Theorem)**
> Let $x$ and $y$ be real (or complex) numbers, and $n$ any natural number. Then
> $$(x+y)^n = \sum_{k=0}^{n} \binom{n}{k} x^k y^{n-k}.$$

> [!proof]- Proof (induction on $n$)
> $n = 0$: both sides are 1.
> 
> Assume it holds for $n$. Then
> $$(x+y)^{n+1} = (x+y)\sum_{k=0}^{n}\binom{n}{k}x^k y^{n-k} = \sum_{k=0}^{n}\binom{n}{k}x^{k+1}y^{n-k} + \sum_{k=0}^{n}\binom{n}{k}x^k y^{n+1-k}.$$
> Pull out the last term of the first sum ($x^{n+1}$) and the first term of the second ($y^{n+1}$), and reindex the first sum with $l = k+1$:
> $$= x^{n+1} + \sum_{k=1}^{n}\left[\binom{n}{k-1} + \binom{n}{k}\right]x^k y^{n+1-k} + y^{n+1}$$
> $$= x^{n+1} + \sum_{k=1}^{n}\binom{n+1}{k}x^k y^{n+1-k} + y^{n+1} = \sum_{k=0}^{n+1}\binom{n+1}{k}x^k y^{n+1-k}$$
> using Lemma 0.16. So it holds for $n+1$. $\square$

## Properties

> **Proposition 0.11 (Associativity)**
> Addition on N is associative. 
> That is, for all $x,y,z ∈N$, $x+ (y+ z) = (x+ y) + z$.

Proved through induction.

> [!proof]- Proof (induction on $z$)
> $z = 0$: $x + (y + 0) = x + y = (x + y) + 0$, using rule (i) twice.
> 
> Suppose it holds for $z = n$. Then
> $$\begin{aligned} x + (y + (n+1)) &= x + ((y+n)+1) && \text{rule (ii)} \\ &= (x + (y+n)) + 1 && \text{rule (ii)} \\ &= ((x+y)+n)+1 && \text{inductive hypothesis} \\ &= (x+y)+(n+1) && \text{rule (ii)} \end{aligned}$$
> So by induction it holds for all $z$. $\square$

> **Proposition 0.11 (Commutativity)**
> Addition on N is commutative. 
> That is, for all $x,y ∈N$, $x + y = y + x$.




