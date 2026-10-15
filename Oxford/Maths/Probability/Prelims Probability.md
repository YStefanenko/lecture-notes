> "Suppose the event of rain $A_j$ has probability $p$ for each day $j$ of this term"
> "Let $A_j$, $1 \leq j \leq n$, be independent events each with probability $p$"

## Events and Probabilities

Consider an "experiment" which has a set $\Omega$ of possible outcomes $\omega \in \Omega$.
We call $\Omega$ the **sample space**.

For example:
a) Tossing a coin: $\Omega = \{H, T\}$
b) Weather on Friday: $\Omega = \{\text{rain}, \text{no rain}\}$
c) Throwing two dice (one red, one blue): $\Omega = \{(i, j) : i, j \in \{1, 2, 3, 4, 5, 6\}\}$, where $i$ is the red die and $j$ is the blue die.

A subset $A \subseteq \Omega$ is called an **event**.

For example:
a) Coin comes up heads: $A = \{H\}$
b) Rain on Friday: $A = \{\text{rain}\}$
c) We observe a total of 9: $A = \{(3, 6), (4, 5), (5, 4), (6, 3)\}$

If $\omega \in \Omega$ is the outcome, we say that an event $A$ **occurs** if $\omega \in A$.

* **Complement:** $A^c$ occurs if $A$ doesn't occur.
* **Union:** $A \cup B$ occurs if $A$ occurs or $B$ occurs.
* **Intersection:** $A \cap B$ occurs if both $A$ and $B$ occur.
* **Set difference:** $A \setminus B = A \cap B^c$ occurs if $A$ occurs and $B$ doesn't occur.

$A$ and $B$ are **disjoint** if $A \cap B = \varnothing$, which means $A$ and $B$ can't both occur.

We assign a probability $\mathbb{P}(A)$ to each event $A$.

Simplest case: $\Omega$ is finite and all outcomes are equally likely. Then
$$\mathbb{P}(A) = \frac{|A|}{|\Omega|}$$

For example:
a) $|\Omega| = 2$, $|A| = 1$, so $\mathbb{P}(A) = \frac{1}{2}$
b) Outcomes are not equally likely, so this formula doesn't apply.
c) $|\Omega| = 6^2 = 36$, so $\mathbb{P}(A) = \frac{4}{36} = \frac{1}{9}$

## Elementary Combinatorics

**Arrangements of distinguishable objects** (e.g. $1, 2, 3, \dots, n$):
$$n \times (n-1) \times \dots \times 2 \times 1 = n! \text{ ways.}$$

**Arrangements when not all objects are distinguishable** (e.g. arrangements of AAABCD):
Given $m_1$ objects of type $x_1$, $m_2$ objects of type $x_2$, …, $m_k$ objects of type $x_k$, with $m_1 + m_2 + \dots + m_k = n$, there are
$$\frac{n!}{m_1!\, m_2! \cdots m_k!} \text{ ways.}$$

This is called a **multinomial coefficient**, denoted
$$\binom{n}{m_1, m_2, \dots, m_k}$$

**Proof:** If we had $A_1, A_2, A_3, B, C, D$ (all distinguishable), there would be $6!$ arrangements. Each arrangement has $3!$ rearrangements of $A_1, A_2, A_3$ that look identical once the labels are removed. So the $6!$ orderings fall into groups of size $3!$, giving $\frac{6!}{3!}$ distinct arrangements.


**Binary case → binomial coefficients.** The number of ways to choose $m$ objects out of $n$ is
$$\binom{n}{m} = \frac{n!}{m!\,(n-m)!}$$
Think of it as arranging $m$ ones and $n - m$ zeros into a boolean mask: each mask picks out which $m$ objects are chosen, so counting masks is the same as choosing $m$ objects without regard to order.