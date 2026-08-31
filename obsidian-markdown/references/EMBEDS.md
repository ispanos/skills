# Embeds

Use Obsidian embeds for vault-local notes and files. Preserve established filenames, aliases, captions, and sizes.

## Notes and blocks

```markdown
![[Note Name]]
![[Note Name#Heading]]
![[Note Name#^block-id]]
```

Define a paragraph block ID at the end of the paragraph. Put a list or quotation block ID on its own line after the block.

## Images

```markdown
![[image.webp]]
![[image.webp|300]]
![[image.webp|640x480]]
```

Preserve sizing forms already used by the target note. For new embeds, use a plain embed unless a dimension materially helps.

## Extensions

Themes and plugins can extend how Obsidian interprets embed text. For example, some caption extensions treat the text after `|` as a rendered caption:

```markdown
![[image.webp|Figure 1: Caption]]
```

This is not a core caption syntax. Use an extension-specific form only when the target note or active setup establishes it. Preserve existing caption forms without rewriting them.

External images use standard Markdown:

```markdown
![Alt text](https://example.com/image.png)
```

## PDFs and media

```markdown
![[document.pdf]]
![[document.pdf#page=3]]
![[document.pdf#height=400]]
![[audio.mp3]]
![[video.mp4]]
```

Use the source's visible page number when known. If a printed page and PDF page differ, record the distinction clearly and do not guess.

## Search results

````markdown
```query
tag:#project status:done
```
````

Do not embed an entire note when a heading or block target communicates the intended relationship more precisely.
