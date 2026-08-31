---
name: obsidian-transcription
description: Faithfully transcribe PDFs, scans, slides, handwriting, and images into Obsidian Flavored Markdown. Use when the user requests complete, verbatim, or source-faithful transcription, especially for math-heavy material. Do not use for summaries, selective extraction, synthesis, or ordinary note writing.
---

# Obsidian transcription

Create an editable Obsidian note that preserves the visible source without silently summarizing, correcting, completing, or interpreting it. Follow the user's requested scope. A request to create research notes does not imply verbatim transcription.

Use vault context only when the working directory or a provided target note is inside a vault, or when the user or repository instructions provide a vault path. Do not search arbitrary directories for a vault.

Read [references/MATH-OCR.md](references/MATH-OCR.md) whenever the source contains mathematical notation.

## Apply conventions in this order

1. Follow the user's explicit request, including the requested pages, slides, or regions.
2. Follow applicable repository instructions.
3. Preserve legible source content, notation, typography, and order.
4. Follow the target note's established formatting when it does not alter the source.
5. Apply the defaults in this skill.

## Transcribe the source

1. Work in source order, page by page or slide by slide.
2. Transcribe every visible word, mathematical expression, label, caption, footnote, bullet, and meaningful layout relationship within the requested scope.
3. Represent structure semantically:
   - use headings for actual titles and section hierarchy;
   - preserve list nesting and numbering;
   - use Markdown tables only when the source is genuinely tabular;
   - retain figure captions and visible labels;
   - embed a source image when it carries information that text cannot preserve.
4. Add `---` between slides or source sections only when requested or already established in the target note.
5. Preserve quotation wording and consistently used source typography.
6. Do not turn ordinary source paragraphs into callouts unless the source or target format calls for it.

## Mark uncertainty without guessing

When a glyph or passage is genuinely illegible, do not choose arbitrarily among plausible readings. Keep a neutral visible form when possible and add a nearby Obsidian comment:

```markdown
$\overset{?}{x}_{t}$ %% OCR uncertain: accent may be a bar or hat %%
```

Do not silently correct a suspected source error. Preserve it and add a traceable comment only when the task allows annotations.

## Return the requested artifact

If the user asks only for transcription, return only the Markdown content. Do not add an introduction, conclusion, or code fence unless requested. When editing a file, keep the change within the requested source range and preserve unrelated note content.

## Verify before finishing

- Compare the transcription against the source at the highest available resolution.
- Check for omitted or duplicated text, equations, labels, qualifiers, citations, footnotes, and figure captions.
- Check list indentation, table structure, Markdown delimiters, Obsidian comments, and equation labels.
- Confirm that every illegible region remains visibly uncertain rather than plausibly invented.
- Confirm that the result is a transcription rather than a summary, solution, or editorial rewrite.
