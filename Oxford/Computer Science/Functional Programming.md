12/10/26: "Glad I have had the tutorial to do"

## Useful
- `:t` - returns type
- `:info` - returns useful info
- `:{` + `:}` - starts and ends multiline
- `--` - comment
- `:!clear` - clears the terminal
- `clear` - clears the terminal

## Associativity

For expressions (left-associative): 
**a b c = (a b) c**

For type definitions (right-associative):
**a -> b -> c = a -> (b -> c)**

Btw:
```
add x y = x + y
add x = (\y -> x + y)
add = (\x -> (\y -> x + y))
add = (\x y -> x + y)
```

## Types
- *Int*
- *Integer*
- *Num*
- *Float*
- *Double*
- *Fractional*
- *Char*
- *String*

## List Comprehensions

List comprehensions are made to align with set definitions in maths.

$\{x \in R | condition\}$ becomes `{x | x <- R, condition}`


## Precedence

**Rule 1: function application beats everything.** Application (juxtaposition) binds tighter than any operator and is left-associative:

- `f x y` = `(f x) y`
- `f x + g y` = `(f x) + (g y)`
- `f g x` = `(f g) x`, **not** `f (g x)`

**Rule 2: operators have a fixity from 0 (loosest) to 9 (tightest),** plus an associativity: `infixl`, `infixr`, or `infix` (non-associative, so it can’t be chained without parentheses).

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
| 2    | `\|`                                     | r          |
| 1    | `>>=` `>>`                               | l          |
| 0    | `$` `$!` `` `seq` ``                     | r          |

**Rule 3: backticked functions** like ``x `foo` y`` default to `infixl 9` unless the function declares its own fixity. You can check any operator’s fixity in GHCi with `:i (op)`.

**Rule 4: `\`, `let`, `if`, and `case` extend as far right as possible.** For example, `\x -> x + 1 $ y` puts everything after the arrow inside the lambda.

**Gotcha: unary minus has precedence 6, like binary minus.** So `f -1` parses as `f - 1`, and you need `f (-1)`.

## Operators To/From Functions

```
x +++ y   = function x y
(+++) x y = function x y
(x +++) y = fucntion x y
(+++ y) x = function x y

x `function` y = function x y
```

## Defining Types

Defining new names for types.
```
type Book = [Char]
```

Defining new types.
```
data Bool = False | True
data Maybe a = Nothing | Just a
data Either a b = Left a | Right b
data PairType a b = Pair a b
```
Nothing, Just, Left, Right are **constructors**. They are defined as the result of the definition.

```
either :: (a -> b) -> (b -> c) -> Either a b -> c
either f g (Left x) = f x
either f g (Right y) = g y
```

(Left x) and (Right y) state whether the input is of the given type.

Selectors (used to extract something from a new type)
```
func (Left x) = x
func (Right y) = y
```


```
isLeft (Left x) = True
isLeft (Right y) = False
```


## Polymorphic Functions
Polymorphic Functions - work for any types (types notated as a, b, c...)

For any f :: a -> a  and g :: [a] -> [a]

map f . g = g . map f

f and g MUST work on any type of data therefore they are quite limited e.g. reverse, identity.


## Type Class

Eq a => a -> a -> Bool
Means the function works for any type a for which " == " can be performed. Eq a is called a type class. 

" == " is defined differently for different types therefore it is NOT a true polymorphic function.
```
data OPair a = OPair a a

instance Eq a => Eq (OPair a) where
	OPair p q = OPair r s | p==r      = q==s
						  | otherwise = False
```

## Evaluation

sq x = x * x

Eager evaluation
sq (3+4)  = sq 7 
		= 7 * 7 
		= 49

Normal evaluation
sq (3+4)  = (3 + 4) * (3 + 4) 
		= 7 * (3 + 4) 
		= 7 * 7 
		= 49

Lazy evaluation
sq (3+4)  = let x = (3 + 4) in x * x
		= let x = 7 in x * x
		= let x = 7 in 7 * x
		= let x = 7 in 7 * 7
		= 49

