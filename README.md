# Agent skills

This repository contains the agent skills I use with Codex.
Some are my own, while others are copied or adapted from published skills.

## Install the collection

Clone the repository to the user skills directory:

```sh
git clone <repository-url> ~/.agents/skills
```

Restart Codex if the skills do not appear in the current session.

## Install one skill

Copy the complete skill directory to `~/.agents/skills`:

```sh
cp -R <skill-name> ~/.agents/skills/
```

## What is included

Each directory at the repository root is one self-contained skill.
The `SKILL.md` file contains its instructions.
Some skills also include agent metadata or reference material.

The following skills are original work:

- `markdown-math`
- `update-ptinopedila-packages`
- `zotero-docs`

The following skills adapt earlier work:

- `document-markup-writing` adapts Diomidis Spinellis's
  [Advice for writing LaTeX documents](https://github.com/dspinellis/latex-advice).
- `obsidian-markdown` adapts Steph Ango's `obsidian-markdown` skill.
- `obsidian-transcription` was split from that adaptation as a companion skill
  for source-faithful transcription.

Each adaptation has an `UPSTREAM.md` that records its source and changes.
The `document-markup-writing` record also documents the original author's
permission for that adaptation.

The remaining skills come from the upstream projects named in their
`UPSTREAM.md` files.
Those records include the source repository, pinned commit, author, and local
changes.

## Licensing

This repository does not place every skill under one license.
Each skill directory has its own `LICENSE` file.
See [LICENSE.md](LICENSE.md) for the repository-wide licensing policy.
