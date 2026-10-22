Functional Programming, Lectures 3–4. Back to [[FP]].

## `type` vs `data`

> **Type synonyms and datatypes**
> - `type` gives a **new name** for an existing type: `type Book = [Char]`. Nothing new is created.
> - `data` defines a **new type**, listing its alternatives separated by `|`:
> ```haskell
> data Bool        = False | True
> data Maybe a     = Nothing | Just a
> data Either a b  = Left a | Right b
> data PairType a b = Pair a b
> ```

## Constructors

The **constructors** (`False`, `Nothing`, `Just`, `Left`, `Right`, `Pair`, …) come for free, as a consequence of the definition:
```haskell
False, True :: Bool
Nothing :: Maybe a
Just    :: a -> Maybe a
Left    :: a -> Either a b
Right   :: b -> Either a b
Pair    :: a -> b -> PairType a b
```
A constructor with arguments is an ordinary function, e.g. `Just 5 :: Maybe Int`, while `Nothing :: Maybe Int` works too.

**Functions are defined by pattern matching on constructors:**
```haskell
boolToInt :: Bool -> Int
boolToInt False = 0
boolToInt True  = 1

maybeToList :: Maybe a -> [a]
maybeToList Nothing  = []
maybeToList (Just x) = [x]

either :: (a -> c) -> (b -> c) -> Either a b -> c
either f g (Left x)  = f x
either f g (Right y) = g y

sumPair :: PairType Int Int -> Int
sumPair (Pair x y) = x + y
```
E.g. `h = either length (*2) :: Either String Int -> Int` gives `h (Left "foo") = 3` and `h (Right 5) = 10`.

> [!mytake]- My take
> ```haskell
> either :: (a -> b) -> (b -> c) -> Either a b -> c
> either f g (Left x) = f x
> either f g (Right y) = g y
> ```
> (Left x) and (Right y) state whether the input is of the given type.
> 
> *(Note added: the correct type is `(a -> c) -> (b -> c) -> Either a b -> c`; both functions must produce the same result type `c`.)*

## Selectors and Discriminators

> **Selectors** extract something from a value of the new type. They are user-defined and may be **partial** (undefined on some constructors).
> ```haskell
> fromJust :: Maybe a -> a
> fromJust (Just x) = x          -- fromJust Nothing is an error
> 
> left  :: Either a b -> a
> left (Left x) = x
> right :: Either a b -> b
> right (Right y) = y
> 
> first  (Pair x y) = x
> second (Pair x y) = y
> ```

> **Discriminators** say which constructor a value was built with. They are user-defined and **total**.
> ```haskell
> isJust :: Maybe a -> Bool
> isJust (Just x) = True
> isJust Nothing  = False
> 
> isLeft :: Either a b -> Bool
> isLeft (Left x)  = True
> isLeft (Right x) = False
> ```

> [!mytake]- My take
> Selectors (used to extract something from a new type)
> ```haskell
> func (Left x) = x
> func (Right y) = y
> ```
> 
> ```haskell
> isLeft (Left x) = True
> isLeft (Right y) = False
> ```
> *(Note added: the two selector equations are really two separate functions, `left` and `right`. A single function can't return an `a` in one case and a `b` in the other.)*

Selectors plus discriminators can replace pattern matching:
```haskell
maybeToList x = if isJust x then [fromJust x] else []
either f g e  = if isLeft e then f (left e) else g (right e)
```

## Recursive Types

A type can refer to itself:
```haskell
data List a = Nil | Cons a (List a)
-- Nil, Cons 1 Nil, Cons 1 (Cons 2 Nil), ...
```
The built-in list `[a]` has exactly this structure:

| | `List a` | `[a]` |
| --- | --- | --- |
| Constructors | `Nil`, `Cons` | `[]`, `(:)` |
| Selectors | — | `head`, `tail` |
| Discriminator | — | `null` |

`[1,2]` is shorthand for `1 : 2 : []`.

## Recursive Functions

Recursion follows the shape of the type: one equation per constructor.
```haskell
map f []     = []
map f (x:xs) = f x : map f xs     -- vs. map f xs = [ f x | x <- xs ]

fact :: Integer -> Integer
fact 0 = 1
fact n = n * fact (n-1)
```
Recursive definitions don't always terminate:
```haskell
inf :: Integer
inf = 1 + inf      -- never finishes evaluating

bottom = bottom    -- the simplest non-terminating definition
```
These are the motivation for $\bot$ in [[FP - Evaluation, Bottom and Strictness]].
