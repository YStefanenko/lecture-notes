Functional Programming, Lecture 1. Back to [[FP]].

## List Comprehensions

`[ expr | generators, guards ]`, where `x <- xs` draws each element of `xs` in turn and a Boolean guard filters.

> [!mytake]- My take
> List comprehensions are made to align with set definitions in maths.
> 
> $\{x \in R \mid \text{condition}\}$ becomes `[x | x <- R, condition]`
> 
> *(Note added: Haskell uses square brackets here, not braces.)*

`map`, `filter` and `concat` can all be explained as comprehensions. These aren't the Prelude's definitions, but they define the same functions:
```haskell
map :: (a -> b) -> [a] -> [b]
map f xs = [ f x | x <- xs ]

filter :: (a -> Bool) -> [a] -> [a]
filter p xs = [ x | x <- xs, p x ]

concat :: [[a]] -> [a]
concat xss = [ x | xs <- xss, x <- xs ]   -- later generators vary fastest
```
(The lecture file hides the Prelude versions with `import Prelude hiding ((.), map, filter, concat, Word)` so it can redefine them.)

## Composition

> **Composition `(.)`**
> ```haskell
> (.) :: (b -> c) -> (a -> b) -> (a -> c)
> (f . g) x = f (g x)
> ```
> `f . g` means "do `g`, then `f`": read pipelines **right to left**. This *is* the standard definition.

An **infix operator** is a function of two arguments; in parentheses it's used prefix, so `(f . g) x = f (g x)` is the same as `(.) f g x = f (g x)`.

## Example: Most Common Words

A whole program as one pipeline of small functions (read bottom to top):
```haskell
type Text = [Char]
type Word = [Char]
type Run  = (Int, Word)

mostCommon :: Int -> Text -> String
mostCommon n = concat .        -- [String] -> String
               map showRun .   -- [Run] -> [String]
               take n .        -- [Run] -> [Run]
               reverse .       -- [Run] -> [Run]   (largest counts first)
               sort .          -- [Run] -> [Run]   (sorts by count, then word)
               map codeRun .   -- [[Word]] -> [Run]
               group .         -- [Word] -> [[Word]]  (runs of equal words)
               sort .          -- [Word] -> [Word]    (equal words become adjacent)
               words .         -- Text -> [Word]
               map canonical   -- Text -> Text
```

> [!example]- The helper functions
> ```haskell
> -- lower-case letters stay, upper-case are lowered, anything else becomes a blank
> canonical :: Char -> Char
> canonical c | isLower c = c
>             | isUpper c = toLower c
>             | otherwise = ' '
> 
> -- only ever applied to a non-empty run of identical words
> codeRun :: [Word] -> (Int, Word)
> codeRun xs = (length xs, head xs)
> 
> showRun :: (Int, Word) -> String
> showRun (n,w) = concat [ "  ", w, ": ", show n, "\n" ]
> ```
> Imports needed: `Data.List (group, sort)`, `Data.Char (isUpper, isLower, toLower)`, `System.Environment (getArgs)`. A test text is built with `unlines`, which appends `'\n'` to each string and concatenates.

## Running a Program

In GHCi:
```haskell
text <- readFile "kjb.txt"
putStr (mostCommon 10 text)
-- or in one line:
readFile "kjb.txt" >>= putStr . mostCommon 10
```

As a standalone program, `main` reads the argument and standard input:
```haskell
main :: IO ()
main = do
  [arg] <- getArgs
  text <- getContents
  putStr (mostCommon (read arg) text)
```
From the command line: `runghc Lecture01.lhs 10 < kjb.txt`, or compile with `ghc Lecture01.lhs` and run `./Lecture01 10 < kjb.txt`.
