# Setup Requirements

This template requires a few tools to be installed for full functionality.
Claude-specific hooks fail gracefully if tools are missing — nothing will break, but
you'll lose validation features.

## Required

| Tool | Purpose | Install |
| ---- | ---- | ---- |
| **Git** | Version control, branch management | [git-scm.com](https://git-scm.com/) |
| **Claude Code** | Claude adapter runtime | `npm install -g @anthropic-ai/claude-code` |

Non-Claude agents should start from `AGENTS.md` and `docs/project/` instead of
depending on `.claude/`.

For shared configuration, prefer the canonical files in `docs/project/`.
The Claude adapter keeps compatibility mirrors such as `.claude/docs/workflow-catalog.yaml`
and `.claude/docs/technical-preferences.md` for Claude-specific consumers.

## Recommended

| Tool | Used By | Purpose | Install |
| ---- | ---- | ---- | ---- |
| **jq** | Claude hook scripts | JSON parsing in commit/push/asset/agent hooks | See below |
| **Python 3** | Claude hook scripts | JSON validation for data files | [python.org](https://www.python.org/) |
| **Bash** | All hooks | Shell script execution | Included with Git for Windows |

### Installing jq

**Windows** (any of these):
```
winget install jqlang.jq
choco install jq
scoop install jq
```

**macOS**:
```
brew install jq
```

**Linux**:
```
sudo apt install jq     # Debian/Ubuntu
sudo dnf install jq     # Fedora
sudo pacman -S jq       # Arch
```

## Platform Notes

### Windows
- Git for Windows includes **Git Bash**, which provides the `bash` command
  used by all hooks in `settings.json`
- Ensure Git Bash is on your PATH (default if installed via the Git installer)
- Claude adapter hooks use `bash .claude/hooks/[name].sh` — this works on Windows
  because Claude Code invokes commands through a shell that can find `bash.exe`

### macOS / Linux
- Bash is available natively
- Install `jq` via your package manager for full hook support

## Verifying Your Setup

Run these commands to check prerequisites:

```bash
git --version          # Should show git version
bash --version         # Should show bash version
jq --version           # Should show jq version (optional)
python3 --version      # Should show python version (optional)
```

## What Happens Without Optional Tools

| Missing Tool | Effect |
| ---- | ---- |
| **jq** | Commit validation, push protection, asset validation, and agent audit hooks silently skip their checks. Commits and pushes still work. |
| **Python 3** | JSON data file validation in commit and asset hooks is skipped. Invalid JSON can be committed without warning. |
| **Both** | All hooks still execute without error (exit 0) but provide no validation. You're flying without safety nets. |

## Recommended IDEs / Runtimes

Claude Code works with any editor, but the bundled Claude adapter is optimized for:
- **VS Code** with the Claude Code extension
- **Cursor** (Claude Code compatible)
- Terminal-based Claude Code CLI

For other agent runtimes, prefer whatever environment can read `AGENTS.md` and
follow the shared docs in `docs/project/`.
