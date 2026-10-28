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

> [!proof]- Proof
> If we had $A_1, A_2, A_3, B, C, D$ (all distinguishable), there would be $6!$ arrangements. Each arrangement has $3!$ rearrangements of $A_1, A_2, A_3$ that look identical once the labels are removed. So the $6!$ orderings fall into groups of size $3!$, giving $\frac{6!}{3!}$ distinct arrangements.


**Binary case → binomial coefficients.** The number of ways to choose $m$ objects out of $n$ is
$$\binom{n}{m} = \frac{n!}{m!\,(n-m)!}$$
Think of it as arranging $m$ ones and $n - m$ zeros into a boolean mask: each mask picks out which $m$ objects are chosen, so counting masks is the same as choosing $m$ objects without regard to order.

> **Lemma 1.1 (Multinomial count)**
> The number of arrangements of $n$ objects, where $\alpha_i$ appears $m_i$ times and $m_1 + \dots + m_k = n$, is
> $$\frac{n!}{m_1!\,m_2!\cdots m_k!}. \tag{1.1}$$
> This is the coefficient of $a_1^{m_1}\cdots a_k^{m_k}$ in $(a_1 + \dots + a_k)^n$, hence "multinomial".

> [!example]- Example 1.2 (STATISTICS)
> The letters of STATISTICS (3 S, 3 T, 2 I, 1 A, 1 C) can be arranged in $\dfrac{10!}{3!\,3!\,2!}$ ways.

**Stirling's formula:** $n! \sim \sqrt{2\pi}\,n^{n + \frac12}e^{-n}$ (ratio $\to 1$); the error is about 1% already at $n = 10$. See [[A1 - Convergence Tests]] for a proof.

**Binomial theorem:** $(x + y)^n = \sum_{m=0}^n \binom nm x^m y^{n-m}$. Multiplying out $(x + y)\cdots(x + y)$ picks $x$ or $y$ from each bracket, and $\binom nm$ counts the ways to choose which $m$ brackets give $x$.

> [!example]- Example 1.3 (is player 1 in the team?)
> Pick a team of $m$ from a squad of $n$, all teams equally likely. Encode a team as $(i_1, \dots, i_n) \in \{0,1\}^n$ with $\sum i_k = m$. Then
> $$\mathbb{P}(\text{player 1 picked}) = \frac{\binom{n-1}{m-1}}{\binom nm} = \frac mn.$$

**Counting by bijection:** match the objects you want to count with objects you already know how to count.

> [!example]- Example 1.4 (stars and bars)
> The number of non-negative integer solutions of $x_1 + \dots + x_m = n$ is
> $$\binom{n + m - 1}{n}.$$
> Biject solutions with sequences of $n$ stars and $m - 1$ bars, e.g. $\star\star\,|\,|\,\star\,|$ is $(2, 0, 1, 0)$.

> **Lemma 1.5 (Vandermonde's identity)**
> For $k, m, n \geq 0$ (with $\binom mj = 0$ for $j > m$):
> $$\binom{m+n}{k} = \sum_{j=0}^k \binom mj\binom{n}{k-j}. \tag{1.2}$$

> [!proof]- Proof (double counting)
> Count committees of $k$ people from $m$ men and $n$ women. Directly: $\binom{m+n}{k}$. Alternatively, a committee has some $j \in \{0, \dots, k\}$ men and $k - j$ women, giving $\binom mj\binom n{k-j}$ committees for each $j$; sum over $j$. $\square$

**Aside on sizes of sets:** an infinite set is **countable** if it can be listed $\{x_1, x_2, \dots\}$ (bijection with $\mathbb{N}$), otherwise **uncountable**. $\mathbb{N}$ and $\mathbb{Q}$ are countable; $\mathbb{R}$ is not ([[A1 - Countability]]).

## Rest of the course
1. [[P1 - Axioms and Conditional Probability]]: probability spaces, conditional probability, total probability, Bayes, independence *(Ch 1.3–1.7)*
2. [[P1 - Discrete Random Variables]]: p.m.f.s, classical distributions, expectation, variance, conditional expectation *(Ch 2.0–2.3)*
3. [[P1 - Joint Discrete Distributions]]: joint p.m.f.s, marginals, independence, linearity, covariance *(Ch 2.4)*
4. [[P1 - Difference Equations and Random Walks]]: recurrences, gambler's ruin *(Ch 3)*
5. [[P1 - Generating Functions and Branching Processes]]: p.g.f.s, random sums, extinction *(Ch 4)*
6. [[P1 - Continuous Random Variables]]: c.d.f.s, p.d.f.s, classical distributions, functions of r.v.s *(Ch 5.1–5.4)*
7. [[P1 - Joint Continuous Distributions]]: joint densities, marginals, bivariate normal *(Ch 5.5)*
8. [[P1 - Random Samples and the Weak Law]]: sample mean, Markov, Chebyshev, WLLN *(Ch 6)*
9. [[P1 - Appendix]]: analysis reminders, continuity of $\mathbb{P}$, distribution tables
