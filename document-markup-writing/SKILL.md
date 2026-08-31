---
name: document-markup-writing
description: Create, revise, and review readable, maintainable source in document-oriented markup languages while preserving authorial intent, markup, and rendered output. Use when writing or editing LaTeX, Markdown, Quarto, reStructuredText, AsciiDoc, or similar markup documents (.tex, .md, .qmd, .rst, .adoc); applying semantic line breaks; preserving citations, mathematics, comments, and document structure; organizing source files; or reviewing document-source diffs.
---

# Document markup writing

Improve the maintainability of document markup source
without changing the author's intended meaning or rendered output.
Treat source structure and prose wording as separate concerns.
Change the wording only when the task asks for it.

## Inspect the project

1. Read applicable repository instructions.
2. Identify the markup language, dialect, renderer, and build tools.
3. Inspect the main document, shared configuration, definitions,
   nearby source, included files, and build configuration relevant to the task.
4. Follow established terminology, markup, file organization,
   and formatting conventions.
5. Treat project conventions as authoritative over this skill's defaults.

## Preserve the author's work

- Preserve wording, voice, mathematical notation, equations,
  citations and citation keys, labels and anchors, references,
  comments, and custom markup unless the task explicitly requires changes.
- Never invent citation keys, references, results, or source material.
- Make the smallest coherent edit that fulfills the request.
- Avoid reformatting or reflowing unrelated text.
- Keep semantic changes separate from broad formatting changes
  whenever the task permits.

## Use semantic line breaks

- Apply semantic line breaks to new or substantially revised prose.
- Start a new source line after each complete sentence.
- Break long sentences at meaningful clause or phrase boundaries.
- Place logically parallel elements on separate lines when useful.
- Aim for roughly 60--80 characters per line,
  but prioritize logical structure over a rigid width.
- Allow longer lines for indivisible commands, markup, links,
  inline mathematics, URLs, and citations
  when splitting them would reduce clarity.
- Confirm that source line breaks do not change the rendered document
  in the active format and renderer.
- Do not reflow untouched paragraphs merely to enforce line length.
- Use blank lines only where the format should begin a new paragraph or block.

## Apply format-specific rules

### LaTeX

- Inspect the preamble, document classes, packages, custom commands,
  bibliography configuration, included files, and build commands.
- Preserve commands, environments, labels, citation keys,
  and custom definitions unless the task requires changes.
- Remember that a blank line starts a new paragraph.
- Do not introduce unsafe breaks inside commands, command arguments,
  verbatim content, or environments whose whitespace affects output.
- Compile or lint the document when an existing workflow makes that practical.

### Markdown and related formats

- Identify the active dialect and renderer, such as CommonMark, GitHub Flavored
  Markdown, Pandoc, Quarto, or Obsidian Markdown.
- Follow Markdown instructions and skills local to the project or directory.
- When neither local instructions nor existing files establish a dialect,
  use GitHub Flavored Markdown.
- Prefer syntax that also renders correctly in VS Code Markdown Preview.
- Do not introduce Pandoc, Quarto, or Obsidian-specific extensions
  unless the document requires them.
- Preserve frontmatter, attributes, heading identifiers, links,
  reference definitions, footnotes, directives, embedded HTML,
  and code fences.
- Distinguish ordinary soft line breaks from hard breaks marked by syntax
  such as trailing spaces or a backslash.
- Preserve indentation and line boundaries inside lists, block quotes,
  tables, code blocks, and other structures where whitespace is meaningful.
- Preserve Pandoc-style citations exactly, including citation keys,
  locators, prefixes, suffixes, grouped citations, and author suppression.
- Use Pandoc citations when the project has a Pandoc or Quarto workflow.
  Do not introduce them into an ordinary GitHub Flavored Markdown document
  without evidence that its renderer supports citations.
- Preserve bibliography and CSL metadata unless the task asks to change them.
- Keep mathematical delimiters and notation compatible with the target renderer.
- Render or lint the document when an existing workflow makes that practical.

### Other document markup languages

- Identify which whitespace, delimiters, directives, and control lines
  affect document structure or output.
- Apply the shared rules only where the markup language treats changes safely.
- Preserve format-specific metadata, cross-references, includes,
  and literal or executable blocks.
- Use the project's normal parser, renderer, build, or lint tool to validate edits.

## Use comments deliberately

- Preserve existing comments, TODO markers, and annotations.
- Add comments only when the format supports them and they clarify
  non-obvious intent, document structure, or unfinished work.
- Do not add a summary comment to every paragraph mechanically.
- Follow editor-specific folding conventions only when the project uses them.
- Do not remove or silently resolve TODOs unless requested.

## Respect document organization

- Preserve the existing single-file or multi-file organization
  unless the user asks for restructuring.
- Prefer a single main source file for a new short document
  when no project convention dictates otherwise.
- Split a new long work at natural boundaries such as chapters or sections
  when this improves navigation, reuse, or selective rendering.
- Keep inclusions, links, references, and paths consistent
  with the project's existing approach.

## Validate the edit

1. Inspect the diff for accidental prose reflow,
   lost comments, broken markup, and unrelated changes.
2. Run the project's existing build, render, or lint command
   when available and proportionate to the task.
3. Check warnings, errors, and rendered-output changes
   relevant to the edited source.
4. Report what was validated and any checks that could not be run.
