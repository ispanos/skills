# Callouts

Use callouts for semantically distinct material, not as generic decoration.

## Standard syntax

```markdown
> [!note]
> A note.

> [!note] Conditional expectation
> Definition content.

> [!example]- Worked derivation
> Derivation content.

> [!question]+ Expanded question
> Question content.
```

Use `-` for collapsed-by-default and `+` for expanded-but-foldable. Prefix every content line, including blank lines inside the callout, with `>`.

Standard callout identifiers include `note`, `abstract`, `info`, `todo`, `tip`, `success`, `question`, `warning`, `failure`, `danger`, `bug`, `example`, and `quote`. A custom title belongs after the closing bracket.

Custom identifiers may be defined by CSS files in `.obsidian/snippets/` or by plugins in `.obsidian/plugins/`, relative to the active vault. Unsupported identifiers use the `note` appearance. Inspect the active setup only when custom behavior must be verified. Preserve existing identifiers when editing. Do not assume that research-oriented identifiers such as `definition`, `theorem`, or `proof` have custom styling.

## Usage

- Without an established custom identifier, use a built-in type and put the research role in the title, such as `[!note] Definition 3.1.12: ...`.
- Use custom identifiers such as `[!definition]` or `[!proof]` only when the target note, repository instructions, CSS, or an installed plugin establishes them.
- Use foldable proof callouts when a nearby note series already does so or when the user asks for collapsible derivations.

## Nested callouts

```markdown
> [!question] Outer callout
> > [!note] Inner callout
> > Nested content
```

Keep nesting shallow and preserve source hierarchy.
