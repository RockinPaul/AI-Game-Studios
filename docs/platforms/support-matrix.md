# Runtime Support Matrix

This document separates the **neutral core** from **adapter-specific features**.

## Core vs Adapter Features

| Capability | Neutral Core | Claude Adapter Today | Other Runtimes Today |
|-----------|--------------|----------------------|----------------------|
| Shared project docs | Yes (`docs/project/`) | Yes | Docs-only |
| Design / ADR / production artifacts | Yes | Yes | Yes |
| Workflow guide | Yes | Yes | Docs-only |
| Canonical workflow catalog | Yes (`docs/project/workflow-catalog.yaml`) | Mirror only | Docs-only |
| Neutral per-phase workflow docs | Yes (`docs/project/workflows/`) | Yes as reference | Docs-only |
| Role roster | Yes | Yes | Docs-only |
| Neutral role library | Yes (`agents/`) | Yes as reference | Docs-only |
| Skill disposition map | Yes (`docs/project/skill-disposition.md`) | Yes | Docs-only |
| Slash-command UX | No | Yes | No |
| Claude tool-specific skills | No | Yes | No |
| Structured option UI (`AskUserQuestion`) | No | Yes | Runtime-specific fallback |
| In-process subagent spawning (`Task`) | No | Yes | Runtime-specific fallback |
| Hook lifecycle automation | No | Yes | Not implemented |
| Status line integration | No | Yes | Not implemented |

## Current Recommendation

- Use `AGENTS.md` and `docs/project/` for non-Claude agents.
- Use `CLAUDE.md` and `.claude/` for Claude Code.
- Treat `.claude/skills/` as the current reference adapter, not as the only valid interface.
- Treat `.claude/docs/workflow-catalog.yaml` as a Claude mirror of the neutral catalog, not the canonical source.
- See `docs/project/neutral-core-readiness.md` for the current migration finish-line status.

## Next Adapter Steps

To add a new runtime cleanly:

1. Reuse `docs/project/` as the shared core.
2. Add a runtime-specific root entry file if needed.
3. Map runtime features onto neutral capabilities:
   - present options
   - capture open response
   - delegate role
   - read/search/write files
   - run commands
4. Keep runtime-only automation outside the neutral core.
