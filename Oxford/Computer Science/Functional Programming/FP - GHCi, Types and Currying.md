Functional Programming, Lecture 1. Back to [[FP]].

## Useful GHCi Commands
- `:t` returns the type of an expression.
- `:info` (or `:i`) returns useful info, including an operator's fixity: `:i (+)`.
- `:{` and `:}` start and end a multiline block (needed to type a signature plus definition).
- `--` starts a comment.
- `:!clear` or `clear` clears the terminal.

## Basic Types

| Type | Examples | Notes |
| --- | --- | --- |
| `Bool` | `True`, `False` | `not`, `&&`, `\|\|` |
| `Int` | `1 :: Int` | fixed-size machine integer |
| `Integer` | `1 :: Integer` | arbitrary precision |
| `Float`, `Double` | `1.5 :: Double` | single / double precision |
| `Char` | `'a'`, `'B'`, `'\n'` | single quotes |
| `String` | `"aB\n"`, `""` | **just `[Char]`**: `['a','B','\n'] :: String` |
| `[a]` | `[1,2,3]`, `[[1,2],[3]]` | lists hold one type |
| `(a, b)` | `([], False)` | tuples (product types) can mix types |

- An unannotated literal is **overloaded**: `:t 1` gives `Num a => a`, `:t 1.5` gives `Fractional a => a`. `Num` and `Fractional` are *type classes* (families of types), not types. See [[FP - Polymorphism, Type Inference and Type Classes]].
- `:t []` gives `[a]`: the empty list has every list type.

> [!mytake]- My take
> Types:
> - *Int*
> - *Integer*
> - *Num*
> - *Float*
> - *Double*
> - *Fractional*
> - *Char*
> - *String*
> 
> *(Note added: `Num` and `Fractional` are type classes rather than types.)*

**List basics:** `head [1,2,3] = 1`, `tail [1,2,3] = [2,3]`, `[1,2,3] ++ [4,5,6] = [1,2,3,4,5,6]`, `concat [[1,2,3],[4,5,6]] = [1,2,3,4,5,6]`.

> [!example]- GHCi experiments from the lecture
> ```haskell
> not (False && False)   -- True
> not False && False     -- False: application binds tighter than &&
> not (not True)         -- True; `not not True` doesn't type-check
> not True || not False  -- True
> 1*2+3*4                -- 14
> 1-2-3                  -- -4, same as (1-2)-3; 1-(2-3) = 2
> ```

## Functions, Currying and Partial Application

Three ways to write addition:
```haskell
add1 :: (Int,Int) -> Int     -- takes a pair (uncurried)
add1 (x,y) = x+y

add2 :: Int -> Int -> Int    -- curried: takes x, returns a function of y
add2 x y = x+y

add3 :: Int -> Int -> Int    -- the same, with a lambda made explicit
add3 x = (\y -> x+y)
```

**Partial application:** a curried function can be given fewer arguments, producing a new function.
```haskell
succ = add2 1     -- succ :: Int -> Int; succ 10 = 11
id   = add2 0     -- id 10 = 10
```

## Associativity

> **The two directions**
> - Function **application** is **left**-associative: `a b c = (a b) c`.
> - The type arrow `->` is **right**-associative: `a -> b -> c = a -> (b -> c)`.

These fit together: `add2 :: Int -> (Int -> Int)` takes one `Int` and returns a function, so `add2 1 2 = (add2 1) 2`. This is also why `not not True` fails: it means `(not not) True`, and `not` can't take a function.

> [!mytake]- My take
> All of these are the same function:
> ```haskell
> add x y = x + y
> add x = (\y -> x + y)
> add = (\x -> (\y -> x + y))
> add = (\x y -> x + y)
> ```
