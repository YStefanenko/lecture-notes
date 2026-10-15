12/10/26: "Glad I have had the tutorial to do"

## Useful
- `:t` - returns type
- `:info` - returns useful info
- `:{` + `:}` - starts and ends multiline
- `--` - comment
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

