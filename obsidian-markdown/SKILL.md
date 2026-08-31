---
name: obsidian-markdown
description: Create and edit research notes in Obsidian Flavored Markdown, including wikilinks, embeds, callouts, comments, properties, and MathJax/LaTeX. Use when the requested output or target is an Obsidian note, especially for math-heavy material. Do not use merely because the input contains mathematics, a PDF, or an image.
---

# Obsidian Markdown

Create valid Obsidian Flavored Markdown while preserving the author's wording, notation, structure, citations, source attribution, links, and unfinished work. Follow the requested transformation instead of imposing a generic note structure.

Use vault context when the working directory is a vault, the user or repository instructions provide a vault path, or a provided target note can be resolved to a vault by checking its parent directories. Otherwise, do not search arbitrary directories for a vault. Apply only the formatting and syntax rules that do not require vault context.

## Load the relevant references

- Read [references/LATEX.md](references/LATEX.md) whenever the Obsidian note contains mathematics.
- Read [references/PROPERTIES.md](references/PROPERTIES.md) before creating or changing frontmatter.
- Read [references/EMBEDS.md](references/EMBEDS.md) when embedding notes, headings, blocks, images, audio, PDFs, or searches.
- Read [references/CALLOUTS.md](references/CALLOUTS.md) when creating or changing callouts.

## Apply conventions in this order

1. Follow the user's explicit request.
2. Follow applicable repository instructions.
3. Preserve quoted or attributed source content and its notation unless the user requests a transformation.
4. Follow the target note's established conventions. Do not search unrelated notes merely to infer style. Consult another note when the task, repository instructions, or an identified note series makes it relevant.
5. Apply the defaults in this skill and its references.
6. Use generic Obsidian syntax where no local convention exists.

Do not restyle an existing note merely because another convention is more common.

## Use source material at the requested level

When the user supplies a paper, book, slide deck, image, or other source, follow the requested operation. A request to summarize, extract claims, explain a derivation, or create research notes does not authorize a verbatim transcription. Preserve quotations exactly and keep source attribution attached to the claims or passages it supports.

Use the separate `obsidian-transcription` skill when the user requests faithful, complete, or verbatim transcription from PDFs, scans, slides, handwriting, or images.

## Work with Obsidian notes

- Follow applicable project and agent instructions before editing.
- When vault context is available, prefer known existing note names and aliases. Do not search for a vault or scan unrelated notes.
- Use `[[wikilinks]]` for vault-internal destinations unless the user or repository instructions require Markdown links. Use standard Markdown links for external URLs. Do not rewrite valid existing links merely to change their format.
- Use an alias when prose and the note title differ: `[[Conditional Expectation Function (CEF)|CEF]]`.
- Link a specific heading or block when that is the intended target: `[[Note#Heading]]` or `[[Note#^block-id]]`.
- Preserve valid links, comments, TODOs, and unfinished material unless the task asks otherwise.
- Embed notes and files with `![[...]]`; preserve the target note's existing caption/size convention rather than rewriting old embeds.
- Do not add an unprompted generic "Related notes" section. Suggest a relevant connection when useful, and add such a section only when the user requests it.
- Do not create frontmatter from generic defaults. Follow [references/PROPERTIES.md](references/PROPERTIES.md).

## Use Obsidian syntax

```markdown
[[Note Name]]
[[Note Name|Display text]]
[[Note Name#Heading]]
[[Note Name#^block-id]]
![[image.webp]]
![[document.pdf#page=3]]

This paragraph can be targeted. ^block-id

==highlighted text==
Visible text %%private working comment%%
```

For a list or quotation, place a block ID on its own line after the block.

## Write mathematics

Use `$...$` for inline math with no padding spaces inside the delimiters. Use `$$` display delimiters on separate lines. Put an equation number immediately after the opening display delimiter:

```markdown
Inline: $f(x) = 2 \cdot x$.

$$\tag{1}
f(x) = ax^2 + bx + c
$$
```

Preserve the source's mathematical meaning and symbol choices. Do not replace notation, change index order, introduce shorthand, or repair a suspected mathematical error silently. See [references/LATEX.md](references/LATEX.md) for detailed LaTeX conventions and fallbacks.

## Verify before finishing

- Confirm that Markdown delimiters, wikilinks, embeds, callouts, comments, and YAML fences are balanced.
- Confirm that display equations render in Obsidian/MathJax and that each `\begin{...}` has a matching `\end{...}`.
- Confirm that the note performs the requested transformation and preserves any quotations, citations, TODOs, or other material outside the authorized change.
- Keep the edit minimal and within the requested scope.
