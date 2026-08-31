# Properties and frontmatter

Obsidian properties use YAML frontmatter at the start of a note:

```yaml
---
title: Example note
aliases: []
tags:
  - method
related: "[[Other Note]]"
rating: 4.5
completed: false
due: 2026-08-31T14:30:00
---
```

## Property types

- Text: `title: Example note`
- Number: `rating: 4.5`
- Checkbox: `completed: false`
- Date: `date: 2026-08-31`
- Date and time: `due: 2026-08-31T14:30:00`
- List: `tags: [one, two]` or a YAML list

Common built-in properties include `tags`, `aliases`, and `cssclasses`. Repositories may define additional properties and controlled values.

## Internal links in properties

Obsidian recognizes internal links in Text and List properties. It does not define a separate Link property type. When writing YAML directly, quote wikilinks so that the YAML parser keeps the intended type:

```yaml
related: "[[Other Note]]"
sources:
  - "[[First Source]]"
  - "[[Second Source]]"
```

## Apply local schemas when present

1. Follow repository instructions and use any local metadata skill they require, if applicable.
2. If repository instructions identify a source-of-truth template, read it before changing frontmatter. Do not search for a template otherwise.
3. Preserve existing values and YAML types unless the task authorizes a change.
4. Populate only values supported by the note, its source, or the user's instructions. Do not guess metadata.

## YAML safeguards

- Keep list-valued properties as lists, including when empty.
- Quote wikilinks used as property values, including items in lists.
- Keep Obsidian tags free of spaces; use hyphens, underscores, or `/` for nested tags.
- Validate the final frontmatter as YAML.
- Do not copy template expressions into a concrete note created outside that template workflow.
