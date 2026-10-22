Functional Programming, Lectures 3–4. Back to [[FP]].

## Polymorphism

> **Polymorphic functions**
> A polymorphic function works for **any** type; its type has type variables `a`, `b`, `c`, …:
> ```haskell
> map     :: (a -> b) -> [a] -> [b]
> reverse :: [a] -> [a]
> concat  :: [[a]] -> [a]
> ```

Because `g :: [a] -> [a]` must work for every `a`, it **can't look at the elements**: it can only rearrange, drop or duplicate them.

> **Theorem for free**
> For any `f :: a -> a` and any polymorphic `g :: [a] -> [a]`:
> $$\texttt{map f . g} = \texttt{g . map f}$$
> e.g. `map f . reverse = reverse . map f`. Changing the elements commutes with rearranging them.

> [!mytake]- My take
> Polymorphic Functions: work for any types (types notated as a, b, c...)
> 
> For any f :: a -> a and g :: [a] -> [a]
> 
> map f . g = g . map f
> 
> f and g MUST work on any type of data therefore they are quite limited e.g. reverse, identity.
> 
> *(Note added: it's `g` that has to be polymorphic. `f` can be any function, e.g. `map (+1) . reverse = reverse . map (+1)`.)*

## Type Inference

To infer a type, give every unknown a type variable, write an equation for each application, and solve.

> [!example]- Example: the type of `flip f x y = f y x`
> Let `flip :: a`, `f :: b`, `x :: c`, `y :: d`.
> - Left side: `flip f` gives $a = b \to e$; `flip f x` gives $e = c \to g$; `flip f x y` gives $g = d \to h$.
> - Right side: `f y` gives $b = d \to i$; `f y x` gives $i = c \to j$; both sides are equal, so $j = h$.
> 
> Substituting:
> $$a = b \to e = (d \to i) \to (c \to g) = (d \to (c \to j)) \to (c \to (d \to j)).$$
> Renaming the variables, `flip :: (a -> b -> c) -> (b -> a -> c)`.
> 
> **Quicker:** `flip` takes 3 arguments, so `flip :: a -> b -> c -> d` with `f :: a`, `x :: b`, `y :: c`. Since `f y x :: d`, we need $a = c \to b \to d$, giving `flip :: (c -> b -> d) -> b -> c -> d`.

## Type Classes

> **Type class**
> A **type class** is a family of types supporting some operations:
> ```haskell
> class Eq a where
>   (==) :: a -> a -> Bool
> ```
> `Eq a => a -> a -> Bool` means "for any type `a` that is an instance of `Eq`". A type joins the class by giving an `instance`.

> [!mytake]- My take
> Eq a => a -> a -> Bool
> Means the function works for any type a for which " == " can be performed. Eq a is called a type class.
> 
> " == " is defined differently for different types therefore it is NOT a true polymorphic function.
> ```haskell
> data OPair a = OPair a a
> 
> instance Eq a => Eq (OPair a) where
>   OPair p q == OPair r s | p==r      = q==s
>                          | otherwise = False
> ```
> *(Note added: the instance line needs `==`, not `=`, between the two pairs, since it defines `(==)`.)*

The same data shape can have different equalities. An **ordered** pair (like `(a, a)`) needs matching positions; an **unordered** pair also accepts the swap:
```haskell
data UPair a = UPair a a

instance Eq a => Eq (UPair a) where
  UPair p q == UPair r s | p==r      = q==s
                         | p==s      = q==r
                         | otherwise = False
```

For a recursive type the instance is recursive too, with `_` as a wildcard catch-all:
```haskell
instance Eq a => Eq (List a) where
  Nil       == Nil       = True
  Cons x xs == Cons y ys = x == y && xs == ys
  _         == _         = False
```
The `Eq a =>` context says: lists of `a` can be compared **if** elements of `a` can.
