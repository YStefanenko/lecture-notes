Functional Programming, Lectures 2–3. Back to [[FP]].

## Pattern Matching, Guards and Indexing

- **Pattern matching:** one equation per case, tried top to bottom (`name 0 = "zero"`, `name 1 = "one"`, …).
- **Indexing** with `xs !! i` (0-based) is often neater: `units u = unitStrings !! u`.
- **Guards** `| condition = result` pick the first true condition; `otherwise` is just `True`.
- `div` and `mod` are integer division and remainder; backticks make them infix: ``n `div` 100``.

> [!example]- Example: converting numbers to English words (Lecture 2)
> Split the number into parts, convert each part, then combine: `convert2 = combine2 . digits2`.
> ```haskell
> digits2 :: Int -> (Int,Int)
> digits2 n = (div n 10, mod n 10)
> 
> combine2 :: (Int,Int) -> String
> combine2 (t,u)
>   | t==0         = units u
>   | t==1         = teens u
>   | 2<=t && u==0 = tens t
>   | 2<=t && u/=0 = tens t ++ "-" ++ units u
> 
> teens u = teenStrings !! u        -- "ten" .. "nineteen"
> tens t  = tenStrings !! (t-2)     -- "twenty" .. "ninety"
> ```
> The same pattern scales up: `convert3` splits off hundreds (``n `div` 100``, ``n `mod` 100``) and adds `" hundred and "`; `convert6` splits off thousands and adds `" thousand"`, then
> ```haskell
> link n = if n < 100 then " and " else " "
> ```
> so `convert = convert6` handles $0 \le n < 1\,000\,000$. Each level reuses the level below: small functions composed together.

## Local Definitions: `let` and `where`

```haskell
f1 n = let phi    = (1 + root5)/2
           phibar = -1/phi
           root5  = sqrt 5
       in (phi^n - phibar^n)/root5

f2 n = (phi^n - phibar^n)/root5
  where phi    = (1 + root5)/2
        phibar = -1/phi
        root5  = sqrt 5
```
- `let … in e` is an **expression**; `where` attaches to a whole **equation**.
- Definitions in the same block can refer to each other in any order.
- **Scope gotcha:** a `where` nested under `phi`'s definition is only visible inside `phi`. If `root5` is defined there, the outer `(…)/root5` can't see it, so that version fails.

**Conditionals:**
```haskell
case test of
  True  -> ...
  False -> ...

if test then ... else ...      -- the else is compulsory
```

## Operators and Sections (Lecture 3)

You can define your own infix operators from symbols:
```haskell
x +++ y = if even x then y else -y
x // y  = 2 / (1/x - 1/y)
```
and use any operator prefix, or partially apply it on either side (a **section**):

> [!mytake]- My take
> ```haskell
> x +++ y   = function x y
> (+++) x y = function x y
> (x +++) y = function x y
> (+++ y) x = function x y
> 
> x `function` y = function x y
> ```

So `2 +++ 3`, `(+++) 2 3`, `(2 +++) 3` and `(+++ 3) 2` are all the same. Going the other way, an ordinary function `f x y = 2 / (1/x + 1/y)` can be used infix with backticks: ``2 `f` 3``.

## Precedence

**Rule 1: function application beats everything.** Application (juxtaposition) binds tighter than any operator and is left-associative:
- `f x y` = `(f x) y`
- `f x + g y` = `(f x) + (g y)`
- `f g x` = `(f g) x`, **not** `f (g x)`

**Rule 2: operators have a fixity from 0 (loosest) to 9 (tightest),** plus an associativity: `infixl`, `infixr`, or `infix` (non-associative, so it can't be chained without parentheses).

| Prec | Operators                                | Assoc      |
| ---- | ---------------------------------------- | ---------- |
| 9    | `.` `!!`                                 | r / l      |
| 8    | `^` `^^` `**`                            | r          |
| 7    | `*` `/` `` `div` `` `` `mod` ``          | l          |
| 6    | `+` `-` `<>`                             | l (`<>` r) |
| 5    | `:` `++`                                 | r          |
| 4    | `==` `/=` `<` `<=` `>` `>=` `` `elem` `` | non-assoc  |
| 4    | `<$>` `<*>` `<$`                         | l          |
| 3    | `&&`                                     | r          |
| 2    | `\|\|`                                   | r          |
| 1    | `>>=` `>>`                               | l          |
| 0    | `$` `$!` `` `seq` ``                     | r          |

**Rule 3: backticked functions** like ``x `foo` y`` default to `infixl 9` unless the function declares its own fixity. You can check any operator's fixity in GHCi with `:i (op)`.

**Rule 4: `\`, `let`, `if`, and `case` extend as far right as possible.** For example, `\x -> x + 1 $ y` puts everything after the arrow inside the lambda.

**Gotcha: unary minus has precedence 6, like binary minus.** So `f -1` parses as `f - 1`, and you need `f (-1)`.
