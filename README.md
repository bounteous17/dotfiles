<div align="center">

# 🏠 dotfiles

**My macOS setup, managed with [chezmoi](https://www.chezmoi.io/)**

![chezmoi](https://img.shields.io/badge/managed%20with-chezmoi-4B8BBE?style=for-the-badge)
![macOS](https://img.shields.io/badge/macOS-000000?style=for-the-badge&logo=apple&logoColor=white)
![zsh](https://img.shields.io/badge/shell-zsh-F15A24?style=for-the-badge&logo=gnubash&logoColor=white)
![gitleaks](https://img.shields.io/badge/secrets-gitleaks%20clean-success?style=for-the-badge&logo=git&logoColor=white)

[Quick start](#-quick-start) •
[What's inside](#-whats-inside) •
[Secrets](#-secrets) •
[Daily workflow](#-daily-workflow)

</div>

---

## 🚀 Quick start

On a fresh machine, install chezmoi and apply these dotfiles in one go:

```sh
sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply <your-github-user>
```

Or, if chezmoi is already installed (`brew install chezmoi`):

```sh
chezmoi init --apply <your-github-user>
```

Preview what would change before applying:

```sh
chezmoi diff
```

## 📦 What's inside

| Tool | Config | Notes |
| --- | --- | --- |
| 👻 **Ghostty** | `~/Library/Application Support/com.mitchellh.ghostty` | Terminal emulator |
| 📊 **htop** | `~/.config/htop` | Process viewer |
| 🔑 **SSH** | `~/.ssh/config` | Host config only, **never keys** |
| 🤖 **Claude Code** | `~/.claude/settings.json`, `~/.claude/CLAUDE.md` | Settings and global instructions |
| 🖥️ **Claude Desktop** | `claude_desktop_config.json` | MCP server config |
| 🐚 **zsh** | `~/.zshrc`, `~/.zshenv`, `~/.zprofile` | Shell setup |

## 🔐 Secrets

No secrets live in this repo. Every file is scanned with [gitleaks](https://github.com/gitleaks/gitleaks) before it is added:

```sh
gitleaks dir <path> --no-banner --redact
```

- **zsh tokens** (npm registries, etc.) live in `~/.zshrc.local`, which is sourced by `~/.zshrc` and is **not tracked**.
- **`~/.kube/config`** is intentionally left out because it embeds a private key.

Create your own `~/.zshrc.local` after applying:

```sh
# ~/.zshrc.local
export NPM_RINGIER_TOKEN="..."
export NPM_RASCH_TOKEN="..."
```

## 🛠️ Daily workflow

```sh
chezmoi add <file>        # start tracking a file
chezmoi edit <file>       # edit the managed copy
chezmoi diff              # see pending changes
chezmoi apply             # write changes to $HOME
chezmoi cd                # jump into this repo
```

Before every commit, scan for leaks:

```sh
gitleaks dir . --no-banner --redact
```

## 📚 Resources

- [chezmoi docs](https://www.chezmoi.io/user-guide/setup/)
- [gitleaks](https://github.com/gitleaks/gitleaks)
- [Ghostty](https://ghostty.org/)

## 📄 License

[MIT](LICENSE)
