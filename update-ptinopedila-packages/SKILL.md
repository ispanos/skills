---
name: update-ptinopedila-packages
description: Add one or more Homebrew formulas, Homebrew casks, and/or Flatpaks to the purpose-specific default package lists for the ptinopedila custom image, update required Homebrew tap trust configuration, then validate, commit, and push the focused change with plain Git. Use when the user says things such as "add X Brew package and push it," "add Y Flatpak to my image," or asks to update the default packages in ptinopedila, including when Codex starts outside the repository.
---

# Update ptinopedila Packages

Update the package defaults in `$HOME/Projects/ublue-os/ptinopedila`, commit only the requested changes, push with plain `git`, and return a clickable GitHub Actions link.

## Workflow

1. Use `$HOME/Projects/ublue-os/ptinopedila` as the repository regardless of the starting directory. Confirm it is a Git worktree and inspect any applicable `AGENTS.md` instructions.
2. Run `git status -sb` and inspect the relevant files before editing. If unrelated changes exist, preserve them and stage only the files required by the package change. If an unrelated change overlaps a target file and cannot be separated safely, stop and ask the user.
3. Normalize obvious speech or typing mistakes only when the intended package is unambiguous. Verify an uncertain Homebrew formula/cask name or Flatpak application ID before editing. Ask only when multiple plausible packages remain.
4. Skip a package already present and report that no change was needed for it.
5. Edit with `apply_patch`, preserving comments, indentation, categories, and the existing ordering style.

## Package Locations

### Homebrew

Inspect all files under
`files/shared/usr/share/ublue-os/homebrew/preinstall.d/*.Brewfile`, including
their `Name`, `Description`, `Category`, and `Install policy` headers. Add each
package to the narrowest matching existing bundle:

- `ptinopedila-core.Brewfile`: essential shell and workstation administration tools.
- `developer.Brewfile`: editors and integrated development environments.
- `developer-fonts.Brewfile`: monospaced and Nerd Fonts for development.
- `research-tools.Brewfile`: document conversion, PDF inspection, media metadata, and OCR.
- `research-fonts.Brewfile`: fonts for documents, presentations, and figures.
- `latex.Brewfile`: TeX and LaTeX tooling.
- `julia.Brewfile`: the Julia toolchain.
- Dedicated application bundles such as `chairlift.Brewfile`: only the named application and its required declarations.

Do not recreate or refer to the deleted monolithic
`ptinopedila-cli.Brewfile`. Do not create a new bundle unless the user requests
one or the package clearly needs an independently managed bundle. Ask when no
existing bundle is an unambiguous fit.

- Add a normal formula as `brew "<formula>"`.
- Add `cask "<cask>"` only when the requested package is specifically a Homebrew cask.
- Keep formulas in the formula block and casks in the cask block. Preserve alphabetical ordering when practical.
- Treat non-official taps as untrusted. Add `trusted: true` to the tap and to every fully qualified formula or cask from it.
- For a third-party cask, follow the repository's existing pre-trust pattern in `files/shared/usr/lib/systemd/user/brew-preinstall.service.d/10-ptinopedila-trust.conf` and the manual installer in `files/shared/usr/share/ublue-os/just/60-custom.just`.

### Flatpak

Edit `recipes/common_modules/workstation.yml` under the `type: default-flatpaks` module, in the system-scope `install` list.

- Use the canonical Flatpak application ID, not a display name.
- Place it under the best existing category comment and preserve YAML indentation.
- Do not add a duplicate already inherited or explicitly listed when the repository makes that inheritance clear.

## Validate and Commit

1. Inspect the focused diff and run `git diff --check`.
2. For every changed Brewfile, run `brew bundle check --verbose --file=<Brewfile> --no-upgrade`. Confirm that any failure lists only genuinely missing dependencies, not an untrusted tap.
3. For a Flatpak edit, also verify that `recipes/common_modules/workstation.yml` remains valid YAML using an available non-mutating parser or repository validation command.
4. Stage only the files changed for this request using explicit paths.
5. Choose a terse imperative commit message that describes the full change. Prefer:
   - `Add <name> to default Brew packages`
   - `Add <name> to default Flatpaks`
   - `Add <names> to default packages` for a combined Brew/Flatpak change
6. Commit with plain `git commit -m "<message>"`.
7. Push the current branch to `origin` using plain `git`. Do not invoke `gh`, create a pull request, or use a GitHub publishing skill. If sandboxed SSH or network access blocks the push, retry through the normal permission-escalation flow.
8. Confirm the local branch is synchronized with its upstream and report the commit hash and subject.

## Handoff

Derive the GitHub repository URL from `origin`, supporting SSH and HTTPS remotes. Return a Markdown link to `<repository-url>/actions`, labeled `GitHub Actions`, so the user can click it. Do not run `xdg-open` or launch a browser.
