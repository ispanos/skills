# LaTeX and MathJax

Use these rules for mathematics written in Obsidian. For existing material, preserve the source or surrounding notation even when it differs.

## Delimiters and equation labels

- Write inline math as `$...$`, never `$ ... $` or `\(...\)`, including inside Obsidian comments.
- Write display math with delimiters on their own lines and a blank line before and after the block:

  ```markdown
  $$
  f(x) = ax^2 + bx + c
  $$
  ```

- Do not use `\[...\]` for display math.
- Do not use `equation`, `displaymath`, or `align` as the outer environment for newly written Markdown mathematics. Use a standalone `$$` block and put `aligned` inside it when alignment is necessary.
- Put numbered-equation tags immediately after the opening delimiter:

  ```markdown
  $$\tag{2}
  y_t = \alpha + \beta x_t + u_t
  $$
  ```

- Preserve symbolic tags such as `\tag{PRF}` and source equation numbers exactly.
- Avoid one-line `$$...$$` for newly written display equations. Preserve it in existing notes unless the task includes formatting cleanup.

## Scripts, sums, and products

- Brace subscripts and superscripts: `x_{i}`, `x^{2}`, `\beta_{1}`.
- Preserve the source or target note's bounds order. If neither establishes a convention, put the lower bound before the upper bound: `\sum_{t=0}^{T}` and `\prod_{j=1}^{J}`.
- Use compact unbounded forms where appropriate: `\sum_{i} w_i`, not invented bounds.
- Keep index sets from the source, including forms such as `\sum_{i \in T}` and `\sum_{i:Z_i=z}`.

## Hats, bars, and vectors

- Use `\hat{...}` for a single symbol or short atomic estimator: `\hat{\beta}`, `\hat{\theta}_{n}`, `\hat{e}_{i}`.
- Use `\widehat{...}` when the accent must span a multi-character name or operator: `\widehat{\mathrm{ATE}}`, `\widehat{\operatorname{Var}}(\hat{\beta})`, `\widehat{RER}_{t}`.
- Preserve a source's deliberate `\hat`/`\widehat` choice, especially in log-linearized macro notation.
- Use `\bar{x}` for a single character and `\overline{xy}` when the bar spans multiple characters. Preserve the source or target note's established choice.
- Use `\mathbf{x}` for bold vectors and `^{\top}` for transpose when the source does not dictate another notation.

## Operators, text, and common symbols

- Preserve the source or target note's expectation, probability, number-set, and indicator notation. If neither establishes a convention, use `\mathbb{E}`, `\mathbb{P}`, `\mathbb{R}`, `\mathbb{N}`, and `\mathbb{1}`.
- Put prose inside math in `\text{...}`: `\text{ s.t. }`, `\text{where}`, `\text{for all}`.
- Use `\mathrm{...}` or `\operatorname{...}` for named operators rather than bare italic prose, following the surrounding note: `\mathrm{Var}`, `\operatorname{Cov}`, `\mathrm{rank}`.
- Preserve established optimization notation. When no convention is available, use semantic operators with limits placed underneath in display math:

  ```latex
  \operatorname*{arg\,min}_{\theta} Q(\theta)
  \operatorname*{plim}_{n \to \infty} \hat{\theta}_{n}
  ```

- Use `\cdot` for explicit multiplication where juxtaposition could be unclear, `\times` for Cartesian products or a source-marked multiplication sign, and `\dots` for ellipses in math.
- Preserve Greek variants such as `\epsilon` versus `\varepsilon`; default to `\epsilon` only when the source is ambiguous.

## Fractions, roots, derivatives, and integrals

- Use `\frac{numerator}{denominator}`. Preserve `\dfrac` when the source or target note deliberately uses display-sized fractions inline.
- Use `\sqrt{...}` and keep the radicand exact.
- When no convention is established, use the following derivative and integral spacing:

  ```latex
  \frac{ \partial y }{ \partial x }
  \frac{ d y }{ d x }
  \int_{0}^{\infty} f(x) \, dx
  ```

- Use `\left(`, `\right)`, `\left[`, and `\right]` for delimiters around tall fractions, sums, or matrices; do not add them mechanically to small expressions.

## Multi-line equations and environments

- Use subordinate MathJax environments such as `aligned`, `cases`, `pmatrix`, `bmatrix`, `Bmatrix`, `vmatrix`, `Vmatrix`, `array`, and `matrix` inside `$$` blocks.
- For a newly written multi-line derivation, use `aligned` so that Pandoc can convert the surrounding Markdown display block to LaTeX without nesting one display environment inside another:

  ```markdown
  $$
  \begin{aligned}
  y &= a + b \\
    &= c.
  \end{aligned}
  $$
  ```

- Preserve existing `align` blocks when they render correctly. Convert them to `aligned` only when the task includes formatting cleanup or LaTeX-export compatibility.
- Keep alignment markers and line breaks faithful to the source. Never merge separate equations when that could obscure a logical step.

## MathJax and Markdown safety

- Use MathJax-compatible commands in note content. Do not place LaTeX preamble commands such as `\usepackage` or `\newcommand` in the body. Add them to the frontmatter's `header-includes` multiline string only when applicable repository instructions or a metadata schema support it.
- Do not introduce body-level `\label` or `\ref` commands merely for Obsidian rendering. They are not preamble commands and do not belong in `header-includes`; use them only when the note's LaTeX export workflow requires them and preserves them correctly.
- Avoid custom macros unless the target note already defines and renders them successfully.
- Do not wrap intended mathematics in backticks or code fences. Use code formatting only when showing literal Markdown or LaTeX source.
- Inside Markdown tables, replace mathematical pipe characters with `\vert` or `\mid`; a literal `|` can split the table cell. Move complicated mathematics outside the table when practical.
- Do not escape underscores inside math delimiters.
- Escape a literal currency dollar sign in prose as `\$` when Obsidian could interpret it as a math delimiter.
- Keep display blocks out of headings and do not indent them by four spaces, which would turn them into code blocks.

## Optional LaTeX Suite integration

If the active vault has `.obsidian/plugins/obsidian-latex-suite/data.json` and no source or note convention decides the notation, the `snippets` key can provide additional context. Inspect it only for a math task in that vault. Treat configured expansions as evidence of the notation produced by the editing workflow, not as proof of a personal preference. Skip this integration when the plugin file is absent.
