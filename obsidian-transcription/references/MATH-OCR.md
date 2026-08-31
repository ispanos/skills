# Mathematical OCR safeguards

Preserve the source's mathematical meaning and symbol choices. Use `$...$` for inline mathematics and separate `$$` delimiters for display mathematics when the target note does not establish another supported form.

## Read each expression as a visual region

- Identify the outer structure first, such as an equality, relation, fraction bar, root, matrix, or delimited expression.
- Transcribe the numerator, denominator, limits, indices, arguments, and other components only after establishing that structure.
- Compare every mathematical region to the source at full available resolution. A text-only OCR result is not evidence for mathematics.
- Keep separate equations separate when merging them could hide a logical step.

## Check ambiguous glyphs and marks

- Distinguish `0/O`, `1/l/I`, `v/\nu`, `p/\rho`, `x/\times`, hyphen/minus, primes, dots, hats, and bars from context.
- Distinguish the visually similar euro sign `€` and set-membership symbol `∈` (`\in`) from the source and its context.
- Check every subscript, superscript, limit, prime, accent, delimiter, fraction bar, function argument, nonzero condition, and equation tag against the image.
- If the existence of a mark is clear but its type is not, retain neutral visible uncertainty and explain it in a nearby `%% OCR uncertain: ... %%` comment.

## Check generated LaTeX

- Retain the leading backslash on LaTeX commands introduced by the transcription.
- Inspect mathematical blocks for missing backslashes when a bare word such as `qquad`, `quad`, `cdot`, `times`, `frac`, or `text` appears where a command is visually evident. Do not change a source variable or prose merely because it matches a command name.
- Balance math delimiters and every `\begin{...}` with its corresponding `\end{...}`.
- Do not escape underscores inside math delimiters.
- Do not wrap intended mathematics in code formatting.

Do not infer a missing term from mathematical plausibility. If an expression cannot be read with confidence, preserve the uncertainty instead of substituting a likely expression.
