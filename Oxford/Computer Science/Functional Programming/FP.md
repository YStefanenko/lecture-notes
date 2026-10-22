Functional Programming (Oxford Prelims, CS). Index of topic notes.

> [!mytake]- My take
> 12/10/26: "Glad I have had the tutorial to do"

## Course Admin
- Lectures Mon 10 and Thu 10; practicals in groups with demonstrators; tutorials with the college tutor.
- Textbooks: **Bird** or **Hutton**.
- Reference: [Hoogle](https://hoogle.haskell.org), which searches functions by name *or by type*.
- Haskell at home: https://www.haskell.org/downloads/ . At the department: `ssh yourusername@ecs.ox.ac.uk` (VPN needed off the university network).
- Further reading from Lecture 1:
  - [ICFP 2026](https://icfp26.sigplan.org)
  - [ACM paper](https://dl.acm.org/doi/10.1145/2018396.2018413)
  - [IEEE Spectrum on FP](https://spectrum.ieee.org/functional-programming)
  - [GitHub ReadME on FP](https://github.com/readme/featured/functional-programming)
  - [Haskell Brooks Curry](https://iep.utm.edu/haskell-brooks-curry/)

## Topics
1. [[FP - GHCi, Types and Currying]]: GHCi commands, basic types, lists, strings, tuples, curried functions, partial application, associativity *(Lecture 1)*
2. [[FP - List Comprehensions and Composition]]: `map`/`filter`/`concat` as comprehensions, `(.)`, the `mostCommon` pipeline, running programs *(Lecture 1)*
3. [[FP - Definitions, Operators and Precedence]]: pattern matching, guards, numbers to words, `let`/`where`, `case`/`if`, operators and sections, fixity *(Lectures 2–3)*
4. [[FP - Datatypes and Recursion]]: `type` vs `data`, constructors, selectors, discriminators, recursive types, recursive functions *(Lectures 3–4)*
5. [[FP - Polymorphism, Type Inference and Type Classes]]: polymorphism, theorems for free, inferring the type of `flip`, `Eq` instances *(Lectures 3–4)*
6. [[FP - Evaluation, Bottom and Strictness]]: eager, normal-order and lazy evaluation, $\bot$, partial values, strictness *(Lecture 4)*
