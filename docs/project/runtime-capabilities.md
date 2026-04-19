# Runtime Capabilities

This document defines the neutral capabilities a runtime should provide to work
well with the template. It intentionally avoids binding the workflow to one
provider's tool names.

## Core Capabilities

| Neutral capability | Purpose |
|--------------------|---------|
| `present-options` | Show structured choices to the user |
| `capture-open-response` | Ask for free-form input |
| `delegate-role` | Hand a scoped task to another role or child agent |
| `read-file` | Read project files |
| `search-files` | Search by path or content |
| `write-file` | Create or update project files |
| `run-command` | Run shell/build/test commands |

## Optional Capabilities

| Neutral capability | Purpose |
|--------------------|---------|
| `lifecycle-hooks` | Run adapter-owned automation on session or tool events |
| `statusline` | Surface current stage or task focus in the UI |
| `parallel-agents` | Run multiple independent analysis/implementation lanes |

## Claude Adapter Examples

| Neutral capability | Claude adapter today |
|--------------------|----------------------|
| `present-options` | `AskUserQuestion` |
| `delegate-role` | `Task` |
| `read-file` | `Read`, `Glob`, `Grep` |
| `write-file` | `Write`, `Edit` |
| `run-command` | `Bash` |
| `lifecycle-hooks` | `.claude/settings.json` hooks |
| `statusline` | `.claude/statusline.sh` |

## Portability Rule

Shared workflow docs should describe the neutral capability first.
Adapter docs may then explain the concrete tool mapping.
