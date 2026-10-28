Prelims Probability, Chapter 3. Back to [[P1 - Basics]].

Difference equations are a tool rather than probability, but conditioning on the first step of a process naturally produces them.

> [!example]- Example 3.1 (Gambler's ruin: setting up)
> Win £1 with probability $p$, lose £1 with probability $q = 1 - p$, independently. Stop at £0 or £$M$. Let $u_n$ = probability of ending with nothing from £$n$. Conditioning on the first play (after which it's like starting again from $n \pm 1$):
> $$u_n = p\,u_{n+1} + q\,u_{n-1}, \quad 1 \leq n \leq M - 1, \qquad u_0 = 1,\ u_M = 0. \tag{3.1}$$

> **Definition 3.2 (Linear difference equation)**
> A **$k$th order linear recurrence relation** (difference equation) is
> $$\sum_{j=0}^k a_j u_{n+j} = f(n) \tag{3.2}$$
> with constants $a_0, \dots, a_k$, $a_0 \neq 0 \neq a_k$. A solution is a sequence $(u_n)_{n \geq 0}$ satisfying it for all $n \geq 0$.

This is completely analogous to linear ODEs $a y'' + b y' + c y = f(x)$.

> **Theorem 3.3 (General = particular + homogeneous)**
> The general solution of (3.2) is $u_n = v_n + w_n$, where $(v_n)$ is any particular solution and $(w_n)$ is any solution of the **homogeneous** equation $\sum_{j=0}^k a_j w_{n+j} = 0$.

> [!proof]- Proof
> Since $a_k \neq 0$, $u_{n+k} = \frac{1}{a_k}\left(f(n) - \sum_{j=0}^{k-1}a_j u_{n+j}\right)$; choosing $u_0 = \dots = u_{k-1} = 0$ determines a solution inductively, so solutions exist. If $(u_n)$ and $(v_n)$ both solve (3.2), then $u_n - v_n$ solves the homogeneous equation by linearity. Conversely $v_n + w_n$ is always a solution. $\square$

## First Order Equations

**Recipe:** the homogeneous equation $w_{n+1} = a w_n$ gives $w_n = A a^n$. For a particular solution, guess something shaped like $f$. If that guess already solves the homogeneous equation, multiply by $n$ ("try the next most complicated thing").

> [!example]- Example 3.4: $u_{n+1} = a u_n + b$, $u_0 = 3$
> Homogeneous: $w_n = A a^n$. Try a constant $v_n = C$: $C = aC + b$, so $C = \frac{b}{1-a}$ (if $a \neq 1$). Then $u_n = A a^n + \frac{b}{1-a}$, and $u_0 = 3$ gives
> $$u_n = 3a^n + \frac{b(1 - a^n)}{1 - a}.$$
> **If $a = 1$:** constants solve the homogeneous equation, so try $v_n = Cn$: $C = b$, so $u_n = A + bn = 3 + bn$. (Equivalently, put $a = 1 + \epsilon$ and let $\epsilon \to 0$.)

> [!example]- Example 3.5: $u_{n+1} = a u_n + bn$
> Try $v_n = Cn + D$: $C = aC + b$ and $C + D = aD$, so for $a \neq 1$, $C = \frac{b}{1-a}$, $D = \frac{-C}{1-a}$:
> $$u_n = A a^n + \frac{bn}{1-a} - \frac{b}{(1-a)^2}.$$
> A boundary condition fixes $A$. (Exercise 3.6: for $a = 1$, try $v_n = Cn + Dn^2$.)

## Second Order Equations

For $u_{n+1} + a u_n + b u_{n-1} = f(n)$: try $w_n = \lambda^n$ in the homogeneous equation to get the **auxiliary equation**
$$\lambda^2 + a\lambda + b = 0.$$

> **Homogeneous solution**
> - Distinct roots $\lambda_1 \neq \lambda_2$: $w_n = A_1\lambda_1^n + A_2\lambda_2^n$.
> - Repeated root $\lambda$: $w_n = (A + Bn)\lambda^n$ (Exercise 3.7: check it).

Particular solutions: same tricks, leaving out terms that already solve the homogeneous equation. A first-order equation needs one boundary condition; a second-order one needs two (often $u_0, u_1$, but in gambler's ruin it's $u_0, u_M$).

> [!example]- Example 3.8: $u_{n+1} + 2u_n - 3u_{n-1} = 1$
> $\lambda^2 + 2\lambda - 3 = 0$ gives $\lambda = -3, 1$, so $w_n = A(-3)^n + B$. Constants solve the homogeneous equation, so try $v_n = Cn$: $C(n+1) + 2Cn - 3C(n-1) = 1$ gives $C = \frac14$.
> $$u_n = A(-3)^n + B + \tfrac14 n.$$

> [!example]- Example 3.9: $u_{n+1} - 2u_n + u_{n-1} = 1$
> Repeated root $\lambda = 1$: $w_n = An + B$. Try $v_n = Cn^2$: $C(n+1)^2 - 2Cn^2 + C(n-1)^2 = 2C = 1$, so $C = \frac12$.
> $$u_n = An + B + \tfrac12 n^2.$$

> [!example]- Example 3.10 (Fibonacci numbers)
> $f_{n+2} = f_{n+1} + f_n$, $f_0 = f_1 = 1$. $\lambda^2 - \lambda - 1 = 0$ gives $\lambda = \frac{1 \pm \sqrt5}{2}$. The initial conditions give $A = \frac{\sqrt5 + 1}{2\sqrt5}$, $B = \frac{\sqrt5 - 1}{2\sqrt5}$, so
> $$f_n = \frac{1}{\sqrt5}\left[\left(\frac{1 + \sqrt5}{2}\right)^{n+1} - \left(\frac{1 - \sqrt5}{2}\right)^{n+1}\right],$$
> an integer for every $n$ despite the $\sqrt5$.

> [!example]- Example 3.11 (complex roots)
> $u_{n+2} - 2u_{n+1} + 4u_n = 0$, $u_0 = u_1 = 1$. Roots $\lambda = 1 \pm i\sqrt3 = 2e^{\pm i\pi/3}$; the initial conditions give $A = B = \frac12$, so
> $$u_n = \tfrac12(1 + i\sqrt3)^n + \tfrac12(1 - i\sqrt3)^n = 2^n\cos\frac{n\pi}{3},$$
> which is real.

## Random Walks

A **random walk** moves between nodes, with the next-step probabilities depending only on the current position, not the path so far. (Examples: molecules in a gas, foraging animals, stock prices.)

> **Gambler's ruin probability**
> With $u_0 = 1$, $u_M = 0$ and $p\,u_{n+1} - u_n + q\,u_{n-1} = 0$, the probability of ruin from £$n$ is
> $$u_n = \frac{(q/p)^n - (q/p)^M}{1 - (q/p)^M} \quad (p \neq \tfrac12), \qquad u_n = 1 - \frac nM \quad (p = \tfrac12).$$

> [!proof]- Derivation
> The auxiliary equation $p\lambda^2 - \lambda + q = (p\lambda - q)(\lambda - 1) = 0$ gives $\lambda = 1, q/p$. For $p \neq \frac12$: $u_n = A + B(q/p)^n$, and $u_0 = 1$, $u_M = 0$ give
> $$A = -\frac{(q/p)^M}{1 - (q/p)^M}, \qquad B = \frac{1}{1 - (q/p)^M}.$$
> For $p = \frac12$ the root $1$ is repeated: $u_n = A + Bn$, giving $1 - n/M$ (Exercise 3.12). $\square$

> [!example]- Example 3.13 (expected duration of the game)
> Let $e_n$ = expected number of plays from £$n$ until hitting $0$ or $M$. Conditioning on the first step (which costs 1 play):
> $$e_n = p(1 + e_{n+1}) + q(1 + e_{n-1}) \implies p\,e_{n+1} - e_n + q\,e_{n-1} = -1, \qquad e_0 = e_M = 0. \tag{3.6}$$
> Same homogeneous part as before; constants solve it, so try $v_n = Cn$: $C = -\frac{1}{p - q}$. For $p \neq q$:
> $$e_n = \frac{M}{p - q}\cdot\frac{1 - (q/p)^n}{1 - (q/p)^M} - \frac{n}{p - q}.$$
> (Exercise 3.14: find $e_n$ for $p = q = \frac12$.)

**No upper barrier.** Let $M \to \infty$:
$$\lim_{M \to \infty} u_n^{(M)} = \begin{cases} (q/p)^n & p > q \\ 1 & p \leq q. \end{cases}$$

> **Theorem 3.15 (non-examinable)**
> For a random walk on $\mathbb{Z}$ started at $n > 0$, stepping $+1$ with probability $p$ and $-1$ with probability $q$, the probability $u_n$ of ever hitting $0$ is
> $$u_n = \begin{cases} (q/p)^n & p > q, \\ 1 & p \leq q. \end{cases}$$
> So the walk can escape to $+\infty$ with positive probability iff $p > q$.

> [!proof]- Proof
> Let $H$ = "hits 0" and $A_M$ = "hits 0 before $M$". The $A_M$ increase with $M$ and $H = \bigcup_M A_M$. By continuity of $\mathbb{P}$ along increasing events (Prop A.8, [[P1 - Appendix]]):
> $$u_n = \mathbb{P}(H) = \lim_{M \to \infty}\mathbb{P}(A_M) = \lim_{M \to \infty}u_n^{(M)}. \quad \square$$
