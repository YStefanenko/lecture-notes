# Markdown & LaTeX Cheat Sheet

## 1. Markdown

- **Headings:** `# Title`, `## Section`, `### Subsection`. Use one `#` per note title, `##` for main parts of the lecture. Obsidian's outline panel builds a contents list from these.
- **Emphasis:** `**bold**` for key terms, `*italic*` for emphasis, `==highlight==` (Obsidian) for things to revise.
- **Lists:** start a line with `- ` for bullets or `1. ` for numbered lists. Press Tab to indent a sub-point, Shift+Tab to un-indent.
- **Checkboxes:** `- [ ] ask in class about proof of Lemma 3` creates a clickable to-do. Handy for "things I didn't understand".
- **Code:** single backticks for inline code: `` `map f xs` ``. For blocks, use three backticks plus the language name:
  ````
  ```haskell
  double x = 2 * x
  ```
  ````
- **Links:** `[text](Other Note.md)` links to another note; `[text](Other Note.md#Heading)` links straight to a section. Type `[[` and Obsidian autocompletes note names for you.
- **Embeds:** `![[Note#Heading]]` shows a section of another note inline, e.g. pull a definition into a later lecture instead of copying it.
- **Callouts:** use for definitions and theorems so they stand out:
  ```
  > [!definition] Group
  > A set G with an operation that is...
  ```
  Types like `note`, `tip`, `warning`, `example` get their own colours.
- **Tables:**
  ```
  | Term | Meaning |
  |------|---------|
  | O(n) | linear  |
  ```
- **Images:** drag or paste a screenshot/photo of the board into a note and Obsidian embeds it automatically.
- **Horizontal rule:** `---` on its own line to separate parts of a lecture.
- **Shortcuts worth learning:** `Cmd+O` quick-open a note, `Cmd+E` toggle reading/editing view, `Cmd+P` command palette, `Cmd+Shift+F` search all notes.

## 2. LaTeX (maths)

- **Inline vs display:** `$x^2 + 1$` sits inside a sentence; `$$\int_0^1 f(x)\,dx$$` gets its own centred line. Use display for anything you'd want to look at on its own.
- **Super/subscripts:** `x^2`, `a_n`. Use braces for more than one character: `x^{n+1}`, `a_{ij}`.
- **Fractions and roots:** `\frac{a}{b}`, `\sqrt{x}`, `\sqrt[3]{x}`.
- **Greek letters:** `\alpha \beta \gamma \epsilon \lambda \pi \sigma`; capitals by capitalising: `\Gamma \Sigma \Omega`. Use `\varepsilon` and `\varphi` for the curly versions lecturers usually write.
- **Sums, products, integrals, limits:** `\sum_{i=1}^{n} i`, `\prod_{k=1}^n`, `\int_a^b`, `\lim_{n \to \infty}`.
- **Sets and logic:** `\in \notin \subseteq \cup \cap \emptyset \forall \exists \implies \iff \neg \land \lor`. Number sets: `\mathbb{R} \mathbb{N} \mathbb{Z} \mathbb{Q} \mathbb{C}`.
- **Relations and arrows:** `\leq \geq \neq \approx \equiv \to \mapsto`. A function: `f: A \to B`.
- **Brackets that resize:** `\left( \frac{a}{b} \right)`. Use `\{ \}` for literal curly braces, `\lvert x \rvert` or `|x|` for absolute value, `\lVert v \rVert` for norms.
- **Matrices:**
  ```
  $$\begin{pmatrix} a & b \\ c & d \end{pmatrix}$$
  ```
  `&` separates columns, `\\` starts a new row. Use `bmatrix` for square brackets, `vmatrix` for determinants.
- **Aligned working:** line up equals signs across several lines of a derivation:
  ```
  $$\begin{aligned}
  (a+b)^2 &= (a+b)(a+b) \\
          &= a^2 + 2ab + b^2
  \end{aligned}$$
  ```
- **Cases (piecewise functions):**
  ```
  $$f(x) = \begin{cases} 1 & x \geq 0 \\ 0 & x < 0 \end{cases}$$
  ```
- **Text and spacing inside maths:** `\text{ for all } x`, `\quad` for a wide gap, `\,` for a thin gap (e.g. before `dx`).
- **Latex Suite speed-ups:** in a note, `mk` opens inline maths and `dm` opens display maths. Inside maths, `//` makes a fraction and `@a` becomes `\alpha`. Tab jumps to the next empty slot. The full list is in the plugin's settings.
