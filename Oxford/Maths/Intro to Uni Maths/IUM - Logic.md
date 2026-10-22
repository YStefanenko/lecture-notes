Symbols:
- $\land$  - and
- $\lor$  - or
- $\neg$  - not

> **Definition 4.1 (And, Or, Not)**
> 
> | $P$ | $Q$ | $P \land Q$ | $P \lor Q$ |
> |---|---|---|---|
> | F | F | F | F |
> | F | T | F | T |
> | T | F | F | T |
> | T | T | T | T |
> 
> $\neg P$ is T when $P$ is F, and F when $P$ is T.

Mathematical "or" is inclusive ($P$, $Q$ or both).
Analogy with sets: if $P$ is "$x \in A$" and $Q$ is "$x \in B$", then $\lor \leftrightarrow \cup$, $\land \leftrightarrow \cap$, $\neg \leftrightarrow {}^c$. So the distributive and De Morgan laws carry over from [[IUM - Sets]].

> [!example]- Example 4.2
> In $\mathbb{N}$, let $P$ = "$n = 2$" and $Q$ = "$n$ is even". Then $P \lor Q$ is "$n$ is even", $P \land Q$ is "$n = 2$", and $\neg P$ is "$n \neq 2$".

## De Morgan's Laws for Logic
(Proposition 4.3)
Let $P$ and $Q$ be statements. Then:
$$\neg(P \lor Q) \iff (\neg P) \land (\neg Q) \quad \text{and} \quad \neg(P \land Q) \iff (\neg P) \lor (\neg Q).$$
## Implies
$P \implies Q$ is the same as $Q \lor \neg P$

> **Definition 4.4 (Implies)**
> 'P implies Q', written $P \Rightarrow Q$, means $Q \lor (\neg P)$:
> 
> | $P$ | $Q$ | $P \Rightarrow Q$ |
> |---|---|---|
> | F | F | T |
> | F | T | T |
> | T | F | F |
> | T | T | T |

No causation needed: "If Paris is the capital of France then the Thames flows through London" is true. If $P$ is never true, $P \Rightarrow Q$ is **vacuously true** (e.g. "for all $x \in \varnothing$, …").

> [!example]- Example 4.5
> $P$ = "$n = 2$", $Q$ = "$n$ is even": $P \Rightarrow Q$ but $Q \not\Rightarrow P$.

Don't write "if $x = -1 \Rightarrow x^2 = 1$": the $\Rightarrow$ already stands for both "if" and "then".

Equivalents:
- P implies Q
- if P then Q
- P only if Q
- P is sufficient for Q
- Q is necessary for P
- if Q doesn't hold then P doesn't hold
- not Q implies not P

> **Definition 4.6 (Contrapositive, converse)**
> For a statement $P \Rightarrow Q$:
> 1. the **contrapositive** is $\neg Q \Rightarrow \neg P$. It is always true when the original is.
> 2. the **converse** is $Q \Rightarrow P$. It is sometimes, but not always, true when the original is.
> 3. the **negation** is $\neg(P \Rightarrow Q)$, equivalently $P \land (\neg Q)$. It is never true when the original is.

## Contrapositive
$P \implies Q$ becomes $\neg Q \implies \neg P$
Those are equivalent.

## Converse
$P \implies Q$ becomes $Q \implies P$
Not necessarily true.

## Negation
$P \implies Q$ becomes $\neg(P \implies Q)$
Opposite of the original statement.
Equivalently $P \land \neg Q$ ("P is true and Q is false").

In logic notation every $\exists$ and $\forall$ swap. The statement get negated.

## If and only if
$P \iff Q$ means $P \implies Q$  and $Q \implies P$.
Necessary and sufficient.
Equivalently $(P \land Q) \lor (\neg P \land \neg Q)$. Prove the two directions separately, and don't keep using $P$ once you've switched to assuming $Q$.

## Quantifiers
- $\forall$: for all. $\exists$: there exists. $\exists!$: there exists a unique.
- Write "$\exists x \in S$ s.t. $P(x)$".
- To prove "$\forall x \in X,\ P(x)$", start with "Let $x \in X$."
- **Order matters**, read left to right: later variables may depend on earlier ones. "$\forall s\ \exists c$ s.t. $s \in c$" (every student has a college) is not "$\exists c$ s.t. $\forall s,\ s \in c$" (one college contains everyone).

> [!example]- Examples 4.7 – 4.9
> **4.7** $\forall x \in \mathbb{R}\ x^2 \geq 0$ but $\exists x \in \mathbb{C}$ s.t. $x^2 < 0$.
> 
> **4.8** Injective: $\forall x_1, x_2 \in X,\ f(x_1) = f(x_2) \Rightarrow x_1 = x_2$. Surjective: $\forall y \in Y\ \exists x \in X$ s.t. $f(x) = y$.
> 
> **4.9** "Every prime $> 2$ is odd": $\forall p \in \mathcal{P},\ p > 2 \Rightarrow \exists n \in \mathbb{N}$ s.t. $p = 2n+1$.
> "Every non-negative real has a real square root": $\forall x \in \mathbb{R},\ (x < 0 \text{ or } \exists y \in \mathbb{R} \text{ s.t. } y^2 = x)$.

> **Proposition 4.10 (Negation)**
> 1. The negation of '$\forall x \in X,\ P(x)$' is '$\exists x \in X$ s.t. $\neg P(x)$'.
> 2. The negation of '$\exists x \in X$ s.t. $P(x)$' is '$\forall x \in X,\ \neg P(x)$'.

Negate from the outside in:
$$\neg(\forall s\ \exists c \text{ s.t. } s \in c) \iff \exists s \text{ s.t. } \neg(\exists c \text{ s.t. } s \in c) \iff \exists s \text{ s.t. } \forall c,\ s \notin c.$$

> [!example]- Example 4.19 (limits, negating a definition)
> $f : \mathbb{R} \to \mathbb{R}$ tends to 0 as $x \to \infty$ if
> $$\forall \varepsilon > 0\ \exists X \in \mathbb{R} \text{ s.t. } \forall x \in \mathbb{R},\ x > X \Rightarrow |f(x)| < \varepsilon.$$
> **(i) $e^{-x}$: yes.** Let $\varepsilon > 0$. Take $X = -\ln \varepsilon$. For $x > X$, $|e^{-x}| < e^{-X} = \varepsilon$ (decreasing and positive).
> 
> **(ii) $\cos x$: no.** The negation is
> $$\exists \varepsilon > 0 \text{ s.t. } \forall X \in \mathbb{R}\ \exists x \in \mathbb{R} \text{ s.t. } x > X \text{ and } |f(x)| \geq \varepsilon.$$
> Take $\varepsilon = \tfrac12$. For any $X$, pick $2\pi n > X$; then $\cos(2\pi n) = 1 \geq \varepsilon$.
> (Pattern: $\forall\exists\forall (Q \Rightarrow R)$ negates to $\exists\forall\exists (Q \land \neg R)$.)

## Hypothesis and conclusion
Most theorems have the form "if $P$ then $Q$": $P$ is the **hypothesis**, $Q$ is the **conclusion**. Rewrite with "Let … / Suppose …" for the hypotheses and "Then …" for the conclusion.

> [!example]- Examples 4.12 – 4.14
> **4.12** "If $n$ is a non-zero natural number, then $n$ has a unique prime factorisation." Hypothesis: $n \in \mathbb{N} \setminus \{0\}$. Conclusion: unique prime factorisation.
> 
> **4.13** "Every prime greater than 2 is odd" becomes "Let $p$ be a prime $> 2$. Then $p$ is odd."
> 
> **4.14 (IVT, well stated)** Let $f : \mathbb{R} \to \mathbb{R}$ be continuous, and suppose $a < b$, $f(a) < 0$, $f(b) > 0$. Then $\exists c \in (a,b)$ with $f(c) = 0$.

## Proof techniques

> **Theorem 4.15 (AM-GM Inequality)**
> Let $x, y$ be non-negative real numbers. Then
> $$\frac{x+y}{2} \geq \sqrt{xy},$$
> with equality if and only if $x = y$.

> [!proof]- Direct proof
> $(x - y)^2 \geq 0$, with equality iff $x = y$. Expand and add $4xy$:
> $$x^2 - 2xy + y^2 \geq 0 \implies x^2 + 2xy + y^2 \geq 4xy \implies \tfrac14 (x+y)^2 \geq xy.$$
> Take square roots (valid since $x, y \geq 0$). $\square$

> [!proof]- Proof by contradiction
> Suppose $\exists x, y \geq 0$ with $\sqrt{xy} > \frac12(x+y)$. Squaring (both sides non-negative) and rearranging:
> $$4xy > x^2 + 2xy + y^2 \implies 0 > (x-y)^2,$$
> a contradiction. Replacing $>$ by $=$ shows equality iff $x = y$. $\square$

> **Theorem 4.16 (AM-GM Inequality, $n$ numbers)**
> Let $n \geq 2$. If $x_1, \dots, x_n$ are non-negative reals, then
> $$\frac{x_1 + x_2 + \dots + x_n}{n} \geq (x_1 x_2 \cdots x_n)^{1/n}.$$

> [!proof]- Proof (induction up powers of 2, then backwards)
> **Powers of 2, $n = 2^m$.** $m = 1$ is Theorem 4.15. If true for $n$, then for $2n$:
> $$\frac{1}{2n}\sum_{i=1}^{2n} x_i = \frac12\left(\frac1n\sum_{i=1}^{n} x_i + \frac1n\sum_{i=n+1}^{2n} x_i\right) \geq \frac12\left((x_1\cdots x_n)^{1/n} + (x_{n+1}\cdots x_{2n})^{1/n}\right)$$
> $$\geq \sqrt{(x_1\cdots x_n)^{1/n}(x_{n+1}\cdots x_{2n})^{1/n}} = (x_1 \cdots x_{2n})^{1/(2n)},$$
> using the inductive hypothesis, then the case $m = 1$.
> 
> **Downwards: $n \Rightarrow n-1$.** Given $x_1, \dots, x_{n-1}$, let $M = x_n = \frac{1}{n-1}(x_1 + \dots + x_{n-1})$. The case $n$ gives
> $$M = \frac{x_1 + \dots + x_{n-1} + M}{n} \geq (x_1 \cdots x_{n-1} M)^{1/n}.$$
> Divide by $M^{1/n}$: $M^{(n-1)/n} \geq (x_1 \cdots x_{n-1})^{1/n}$. Raise to the power $n/(n-1)$: $M \geq (x_1 \cdots x_{n-1})^{1/(n-1)}$.
> 
> Every $n \geq 2$ is reached by going down from some power of 2. $\square$

**Counterexamples.** One counterexample disproves a claim. Try simple or extreme cases (zero, empty set, constant function), and ones that break the hypothesis you're relaxing.

> [!example]- Example: refuting a "generalised" AM-GM
> Claim: for all real $x, y$, $\frac12(x+y) \geq \sqrt{|xy|}$, with equality iff $x = y$.
> Counterexample: $x = 1$, $y = -1$ (LHS $= 0$, RHS $= 1$).



