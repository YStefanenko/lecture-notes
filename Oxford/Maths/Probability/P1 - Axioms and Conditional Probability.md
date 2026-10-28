Prelims Probability, Chapter 1.3–1.7. Back to [[P1 - Basics]].

## The Axiomatic Approach

> **Definition 1.6 (Probability space)**
> A **probability space** is a triple $(\Omega, \mathcal{F}, \mathbb{P})$ where $\Omega$ is the sample space, $\mathcal{F}$ is a collection of subsets of $\Omega$ (**events**) and $\mathbb{P} : \mathcal{F} \to \mathbb{R}$ is a **probability measure**, satisfying:
> - **F1** $\Omega \in \mathcal{F}$.
> - **F2** If $A \in \mathcal{F}$ then $A^c \in \mathcal{F}$.
> - **F3** If $\{A_i : i \in I\}$ is a finite or countably infinite collection in $\mathcal{F}$, then $\bigcup_{i \in I} A_i \in \mathcal{F}$.
> 	Simpler case: $A,B \in \mathcal{F} \implies (A \cup B) \in \mathcal{F}$
> - **P1** $\mathbb{P}(A) \geq 0$ for all $A \in \mathcal{F}$.
> - **P2** $\mathbb{P}(\Omega) = 1$.
> - **P3** If $\{A_i : i \in I\}$ is a finite or countably infinite collection in $\mathcal{F}$ with $A_i \cap A_j = \varnothing$ for $i \neq j$, then $\mathbb{P}\left(\bigcup_{i \in I} A_i\right) = \sum_{i \in I}\mathbb{P}(A_i)$.
> 	Simpler case: $A,B \in \mathcal{F}$ and $\implies (A \cap B)=\varnothing \implies \mathbb{P}(A \cup B) = \mathbb{P}(A) + \mathbb{P}(B)$

> [!mytake]- My Take
> $\omega$ is an outcome. 
> $A$ is an event which is a collection of outcomes. A can just be ${\omega}$.
> $\mathcal{F}$ is a set of all events.

Special case of P3: if $A \cap B = \varnothing$ then $\mathbb{P}(A \cup B) = \mathbb{P}(A) + \mathbb{P}(B)$. This implies P3 for all finite collections (induction), but the countably infinite version is genuinely stronger.

If $\Omega$ is finite or countable, take $\mathcal{F}$ to be all subsets of $\Omega$. If $\Omega$ is uncountable, the power set is too big to assign probabilities consistently (Part A Integration).

> [!example]- Example 1.7 (probability function)
> For countable $\Omega = \{\omega_1, \omega_2, \dots\}$ and $p_i \geq 0$ with $\sum p_i = 1$, set $\mathbb{P}(A) = \sum_{i : \omega_i \in A} p_i$. This satisfies P1–P3; $(p_1, p_2, \dots)$ is a **probability function**.

> **Theorem 1.8**
> For $A, B \in \mathcal{F}$:
> 1. $\mathbb{P}(A^c) = 1 - \mathbb{P}(A)$;
> 2. if $A \subseteq B$ then $\mathbb{P}(A) \leq \mathbb{P}(B)$.

> [!proof]- Proof
> 1. $A \cup A^c = \Omega$ disjointly, so by P3 and P2, $\mathbb{P}(A) + \mathbb{P}(A^c) = 1$.
> 2. $B = A \cup (B \cap A^c)$ disjointly, so $\mathbb{P}(B) = \mathbb{P}(A) + \mathbb{P}(B \cap A^c) \geq \mathbb{P}(A)$ by P1. $\square$

## Conditional Probability

> [!example]- Example 1.9 (motivation)
> Roll a fair die. $B = \{2, 4, 6\}$ (even), $C = \{6\}$. Knowing $B$ happened, the outcomes $2, 4, 6$ are equally likely, so $\mathbb{P}(C|B) = \frac13$. With $A = \{3, 6\}$: $\mathbb{P}(A|B) = \frac13 = \mathbb{P}(A \cap B)/\mathbb{P}(B)$.

> **Definition 1.10 (Conditional probability)**
> If $\mathbb{P}(B) > 0$, the **conditional probability of $A$ given $B$** is
> $$\mathbb{P}(A|B) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(B)}.$$
> (Undefined if $\mathbb{P}(B) = 0$.)

> **Theorem 1.11**
> If $\mathbb{P}(B) > 0$ and $Q(A) = \mathbb{P}(A|B)$, then $(\Omega, \mathcal{F}, Q)$ is a probability space.

> [!proof]- Proof
> Same $\mathcal{F}$, so check P1–P3.
> - P1: $Q(A) = \mathbb{P}(A \cap B)/\mathbb{P}(B) \geq 0$.
> - P2: $Q(\Omega) = \mathbb{P}(B)/\mathbb{P}(B) = 1$.
> - P3: for disjoint $A_i$, the sets $A_i \cap B$ are disjoint, so
> $$Q\Big(\bigcup A_i\Big) = \frac{\mathbb{P}\left(\bigcup (A_i \cap B)\right)}{\mathbb{P}(B)} = \sum \frac{\mathbb{P}(A_i \cap B)}{\mathbb{P}(B)} = \sum Q(A_i). \quad \square$$

> **Multiplication rule**
> $$\mathbb{P}(A \cap B) = \mathbb{P}(A|B)\,\mathbb{P}(B) \tag{1.3}$$
> and more generally (induction)
> $$\mathbb{P}(A_1 \cap \dots \cap A_n) = \mathbb{P}(A_1)\,\mathbb{P}(A_2|A_1)\,\mathbb{P}(A_3|A_1 \cap A_2) \cdots \mathbb{P}(A_n|A_1 \cap \dots \cap A_{n-1}). \tag{1.4}$$

> [!example]- Examples 1.12 & 1.13 (multiplication rule)
> **1.12** Urn with 8 red and 4 white balls; draw 3 without replacement. $\mathbb{P}(\text{all red}) = \frac{8}{12}\cdot\frac{7}{11}\cdot\frac{6}{10} = \frac{14}{55}$.
> 
> **1.13** Draw 6 of 26 letter tickets without replacement. $\mathbb{P}(\text{they spell CALVIN}) = \frac{6}{26}\cdot\frac{5}{25}\cdot\frac{4}{24}\cdot\frac{3}{23}\cdot\frac{2}{22}\cdot\frac{1}{21}$, where $A_i$ is "the $i$th ticket is one of C, A, L, V, I, N".

> [!example]- Example 1.14 (noisy bitstream)
> $\mathbb{P}(0 \text{ sent}) = \frac47$, $\mathbb{P}(1 \text{ sent}) = \frac37$, $\mathbb{P}(1 \text{ rec} | 0 \text{ sent}) = \frac18$, $\mathbb{P}(0 \text{ rec} | 1 \text{ sent}) = \frac16$. Find $\mathbb{P}(0 \text{ sent} | 0 \text{ rec})$.
> 
> $\mathbb{P}(0 \text{ sent}, 0 \text{ rec}) = (1 - \frac18)\cdot\frac47 = \frac12$ and $\mathbb{P}(1 \text{ sent}, 0 \text{ rec}) = \frac16 \cdot \frac37 = \frac{1}{14}$. So $\mathbb{P}(0 \text{ rec}) = \frac12 + \frac1{14} = \frac{8}{14}$ and
> $$\mathbb{P}(0 \text{ sent} | 0 \text{ rec}) = \frac{1/2}{8/14} = \frac78.$$

## Law of Total Probability and Bayes

> **Definition 1.15 (Partition)**
> $\{B_1, B_2, \dots\}$ is a **partition** of $\Omega$ if $\Omega = \bigcup_{i \geq 1} B_i$ (at least one happens) and $B_i \cap B_j = \varnothing$ for $i \neq j$ (no two happen together).

> **Theorem 1.16 (Law of total probability / partition theorem)**
> If $\{B_i\}$ is a partition of $\Omega$ with $\mathbb{P}(B_i) > 0$ for all $i$, then for any $A \in \mathcal{F}$,
> $$\mathbb{P}(A) = \sum_{i \geq 1}\mathbb{P}(A|B_i)\,\mathbb{P}(B_i).$$

> [!proof]- Proof
> $\mathbb{P}(A) = \mathbb{P}\left(A \cap \bigcup B_i\right) = \mathbb{P}\left(\bigcup (A \cap B_i)\right) = \sum \mathbb{P}(A \cap B_i) = \sum \mathbb{P}(A|B_i)\mathbb{P}(B_i)$, using P3 since the $A \cap B_i$ are disjoint. $\square$

If some $\mathbb{P}(B_i) = 0$ you can still write $\mathbb{P}(A) = \sum_i \mathbb{P}(A \cap B_i)$.

> [!example]- Example 1.17 (crossword setters)
> Setter I writes $m$ clues, setter II writes $n$. Alice solves a setter-I clue with probability $\alpha$, a setter-II clue with probability $\beta$. For a random clue:
> $$\mathbb{P}(\text{solve}) = \alpha\frac{m}{m+n} + \beta\frac{n}{m+n} = \frac{\alpha m + \beta n}{m+n}.$$

> **Theorem 1.18 (Bayes' Theorem)**
> If $\{B_i\}$ is a partition with $\mathbb{P}(B_i) > 0$ and $\mathbb{P}(A) > 0$, then
> $$\mathbb{P}(B_k|A) = \frac{\mathbb{P}(A|B_k)\,\mathbb{P}(B_k)}{\sum_{i \geq 1}\mathbb{P}(A|B_i)\,\mathbb{P}(B_i)}.$$

> [!proof]- Proof
> $\mathbb{P}(B_k|A) = \frac{\mathbb{P}(B_k \cap A)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A|B_k)\mathbb{P}(B_k)}{\mathbb{P}(A)}$; substitute the law of total probability for $\mathbb{P}(A)$. $\square$

> [!example]- Example 1.19 (Alice again)
> Given that Alice solved the clue, $\mathbb{P}(\text{setter I} | \text{solved}) = \dfrac{\alpha m}{\alpha m + \beta n}$.

**Odds form of Bayes.** The **odds** of $B$ are $\mathbb{P}(B)/\mathbb{P}(B^c)$. Using the partition $\{B, B^c\}$:
$$\underbrace{\frac{\mathbb{P}(B|A)}{\mathbb{P}(B^c|A)}}_{\text{conditional odds}} = \underbrace{\frac{\mathbb{P}(A|B)}{\mathbb{P}(A|B^c)}}_{\text{Bayes factor}}\ \underbrace{\frac{\mathbb{P}(B)}{\mathbb{P}(B^c)}}_{\text{odds}}.$$

> [!example]- Example 1.20 (rare condition, "99% accurate" test)
> Prevalence $\frac{1}{1000}$, no false negatives, false positive rate $0.01$. With $B$ = has condition and $A$ = tests positive:
> $$\frac{\mathbb{P}(B|A)}{\mathbb{P}(B^c|A)} = \frac{1}{0.01}\cdot\frac{1/1000}{999/1000} = 0.0999,$$
> so $\mathbb{P}(B|A) \approx 0.091$. Under 10%: false positives swamp true positives when prevalence is low.

> [!example]- Example 1.21 (Simpson's paradox)
> Kidney stone treatments (Charig et al., 1986). Overall: A succeeds $273/350 = 0.78$, B succeeds $289/350 = 0.83$. Split by stone size:
> 
> | | Small ($<2$cm) | Large ($>2$cm) |
> |---|---|---|
> | A | $81/87 = 0.93$ | $192/263 = 0.73$ |
> | B | $234/270 = 0.87$ | $55/80 = 0.69$ |
> 
> A wins in both groups, yet B wins overall: A got more of the harder (large) cases, a **confounding variable**. In general we can have
> $$\mathbb{P}(E|F \cap G) > \mathbb{P}(E|F^c \cap G), \quad \mathbb{P}(E|F \cap G^c) > \mathbb{P}(E|F^c \cap G^c), \quad \text{yet} \quad \mathbb{P}(E|F) < \mathbb{P}(E|F^c).$$

## Independence

> **Definition 1.22 (Independence)**
> 1. Events $A$ and $B$ are **independent** if $\mathbb{P}(A \cap B) = \mathbb{P}(A)\mathbb{P}(B)$.
> 2. A family $\{A_i : i \in I\}$ is **independent** if $\mathbb{P}\left(\bigcap_{i \in J}A_i\right) = \prod_{i \in J}\mathbb{P}(A_i)$ for all finite $J \subseteq I$.
> 3. The family is **pairwise independent** if $\mathbb{P}(A_i \cap A_j) = \mathbb{P}(A_i)\mathbb{P}(A_j)$ whenever $i \neq j$.
> 
> **Pairwise independent does NOT imply independent.**

If $A, B$ are independent and $\mathbb{P}(B) > 0$, then $\mathbb{P}(A|B) = \mathbb{P}(A)$: knowing $B$ doesn't change the chance of $A$.

> [!example]- Example 1.23 (dice)
> Two fair dice; $A$ = first shows 4, $B$ = total 6, $C$ = total 7. $\mathbb{P}(A \cap B) = \frac1{36} \neq \frac16\cdot\frac5{36}$, so $A, B$ are **not** independent. But $A$ and $C$ are independent (check: $\frac{1}{36} = \frac16 \cdot \frac16$).

> **Theorem 1.24**
> If $A$ and $B$ are independent then so are (a) $A$ and $B^c$, (b) $A^c$ and $B^c$.

> [!proof]- Proof
> (a) $A = (A \cap B) \cup (A \cap B^c)$ disjointly, so
> $$\mathbb{P}(A \cap B^c) = \mathbb{P}(A) - \mathbb{P}(A)\mathbb{P}(B) = \mathbb{P}(A)\mathbb{P}(B^c).$$
> (b) Apply (a) to $B^c$ and $A$. $\square$

More generally, if $\{A_i\}$ is independent then so is $\{A_i^c\}$ (exercise: inclusion–exclusion or induction).

## Useful Rules for Calculating Probabilities (1.7)

- **AND:** multiplication rule $\mathbb{P}(A \cap B) = \mathbb{P}(A|B)\mathbb{P}(B)$, or its generalisation (1.4).
- **OR:** if disjoint, add. Otherwise take complements:
$$\mathbb{P}(A_1 \cup \dots \cup A_n) = 1 - \mathbb{P}(A_1^c \cap \dots \cap A_n^c),$$
or use **inclusion–exclusion**:
$$\mathbb{P}\Big(\bigcup_{i=1}^n A_i\Big) = \sum_i \mathbb{P}(A_i) - \sum_{i<j}\mathbb{P}(A_i \cap A_j) + \dots + (-1)^{n+1}\mathbb{P}(A_1 \cap \dots \cap A_n).$$
- **Can't do it directly?** Split over a partition and use the law of total probability.
- **Check:** every probability must lie in $[0, 1]$.
