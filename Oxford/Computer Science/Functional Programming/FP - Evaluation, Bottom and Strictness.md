Functional Programming, Lecture 4. Back to [[FP]].

## Evaluation Strategies

Take `sq x = x * x` and evaluate `sq (3+4)`:

| Strategy | Idea | Steps |
| --- | --- | --- |
| **Eager** (call by value) | evaluate arguments first | `sq (3+4) = sq 7 = 7*7 = 49` |
| **Normal order** (call by name) | substitute the unevaluated argument | `(3+4)*(3+4) = 7*(3+4) = 7*7 = 49`, so `3+4` is computed **twice** |
| **Lazy** (call by need) | substitute, but share it and evaluate at most once | `let x = 3+4 in x*x = let x = 7 in x*x = … = 49` |

Haskell is **lazy**: normal order's power without the repeated work.

> [!mytake]- My take
> sq x = x * x
> 
> Eager evaluation
> ```
> sq (3+4) = sq 7
>          = 7 * 7
>          = 49
> ```
> 
> Normal evaluation
> ```
> sq (3+4) = (3 + 4) * (3 + 4)
>          = 7 * (3 + 4)
>          = 7 * 7
>          = 49
> ```
> 
> Lazy evaluation
> ```
> sq (3+4) = let x = (3 + 4) in x * x
>          = let x = 7 in x * x
>          = let x = 7 in 7 * x
>          = let x = 7 in 7 * 7
>          = 49
> ```

> **Termination**
> Normal-order evaluation is guaranteed to find a normal form if one exists. So is lazy evaluation, but **not** eager evaluation.

> [!example]- Example: `const 3 bottom`
> With `const x y = x` and `bottom = bottom`:
> - lazily, `const 3 bottom = 3` (the second argument is never needed);
> - eagerly, we first try to evaluate `bottom`, and loop forever.

## Bottom

> **Bottom, $\bot$**
> When reasoning about non-termination we use a special value **bottom**, $\bot$ ("entirely undefined"). It also stands for every kind of error.

- `bottom` is entirely undefined, but `[bottom]` and `[bottom, bottom]` are **partially** defined: you can ask for their length.
- Values containing $\bot$ are **partial**, and they are **not equal to** $\bot$ itself.

> [!example]- How many values of type `(Bool, Bool)`? As many as 10
> $\bot$ itself, plus a pair `(x, y)` where each of `x`, `y` is one of $\bot$, `False`, `True`: $1 + 3 \times 3 = 10$.

## Strictness

> **Definition (strict)**
> - `f :: a -> b` is **strict** if $f\ \bot = \bot$ ("`f` uses its argument").
> - `f :: a -> b -> c` is **strict in its first argument** if $f\ \bot\ y = \bot$ for all `y`. This is the same as `f :: a -> (b -> c)` being strict.
> - It is **strict in its second argument** if $f\ x\ \bot = \bot$ for all `x`. This is the same as `flip f :: b -> (a -> c)` being strict.

- `const x y = x` is strict in its first argument but **not** its second.
- **Constructors are not strict:** `Just bottom` is a value, so `isJust (Just bottom) = True`.
- But `isJust` itself **is** strict: pattern matching has to evaluate its argument, so `isJust bottom = bottom`.

> [!note]- The "halting problem"
> ```haskell
> f x = x /= bottom where bottom = bottom
> ```
> This doesn't test whether `x` is undefined: evaluating `x /= bottom` needs the value of `bottom`, so `f` never returns. No program can decide whether a value is $\bot$; that's the halting problem.
