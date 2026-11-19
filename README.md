# dotfiles

My dotfiles, managed with [chezmoi](https://www.chezmoi.io/).

No secrets are stored here: every file is scanned with [gitleaks](https://github.com/gitleaks/gitleaks) before it's committed.

## Restore

```sh
chezmoi init --apply git@github.com:bounteous17/dotfiles.git
```
