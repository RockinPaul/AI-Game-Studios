# Neutral Project Docs

This directory is the runtime-neutral entry point for the Game Studios template.
Use it when your agent runtime does not natively understand Claude-style slash
commands or when you need a phase-by-phase reference without adapter-specific
language.

## Start Here

1. Read `docs/project/workflows/onboarding.md` to orient yourself.
2. Use the workflow document for the phase you are currently in.
3. Use `docs/project/templates/` when a workflow asks for a report or
   retrospective artifact.
4. Cross-check any phase requirement against the authoritative catalog in
   `docs/project/workflow-catalog.yaml`.

## Workflow Map

The authoritative production pipeline has seven catalog phases. This neutral
layer adds one onboarding guide ahead of them.

| Order | Workflow Doc | Status in Catalog | Purpose |
| --- | --- | --- | --- |
| 0 | `workflows/onboarding.md` | Pre-phase guidance | Orient a runtime, inspect the repository, and identify the active phase |
| 1 | `workflows/concept.md` | Catalog phase | Turn an idea into a documented concept, art direction, and systems map |
| 2 | `workflows/systems-design.md` | Catalog phase | Produce approved per-system design docs and a cross-GDD review |
| 3 | `workflows/technical-setup.md` | Catalog phase | Establish architecture, ADRs, control rules, and accessibility commitments |
| 4 | `workflows/pre-production.md` | Catalog phase | Produce UX specs, prototype the core loop, create epics and stories, and plan the first sprint |
| 5 | `workflows/production.md` | Catalog phase | Run sprint-based implementation, review, QA planning, and retrospectives |
| 6 | `workflows/polish.md` | Catalog phase | Drive performance, balance, asset quality, and repeated playtesting |
| 7 | `workflows/release.md` | Catalog phase | Complete release readiness work and ship |

## Templates

Neutral templates referenced by shared docs live in `docs/project/templates/`.

| Template | Use |
| --- | --- |
| `templates/architecture-decision-record.md` | ADR writing under `docs/architecture/` |
| `templates/project-stage-report.md` | Stage detection output, readiness analysis, and gap reporting |
| `templates/post-mortem.md` | Sprint, milestone, or project retrospective |

## Guidelines

| Document | Purpose |
| --- | --- |
| `docs-guidelines.md` | How to write and maintain neutral operational documentation |
| `design-guidelines.md` | How to structure game design artifacts so they support the workflow |
| `source-guidelines.md` | How implementation artifacts should align with the workflow |

## Canonical Shared Docs

- `directory-structure.md` -- neutral repository layout
- `workflow-catalog.yaml` -- canonical phase/stage catalog for the neutral core
- `workflow-overview.md` -- neutral explanation of the 7-phase pipeline
- `technical-preferences.md` -- shared project configuration fields
- `coordination-rules.md` -- role delegation and escalation rules
- `coding-standards.md` -- code, design, and test expectations
- `context-management.md` -- session-state and continuity guidance
- `agent-roster.md` -- role catalog independent of any one runtime
- `runtime-capabilities.md` -- neutral capability contract for runtimes
- `orchestration-contract.md` -- delegation and approval flow independent of Claude tools
- `skill-inventory.md` -- full inventory of Claude skills and their migration status
- `skill-disposition.md` -- which skills are wrappers, shared-core consumers, or Claude-only

## Relationship to Adapter Docs

- `docs/project/workflow-catalog.yaml` is the authoritative workflow source for
  the neutral layer.
- `docs/WORKFLOW-GUIDE.md` remains the detailed Claude-oriented walkthrough.
- These `docs/project/` files translate the same workflow into runtime-neutral
  language and point to the same artifact paths.

## Adapter Boundary

Today, `.claude/` remains the most complete runtime adapter.

Treat these as adapter-specific, not core:

- `CLAUDE.md`
- `.claude/settings.json`
- `.claude/hooks/`
- `.claude/statusline.sh`
- `.claude/skills/`
- `.claude/agents/`

## Current Canonical Rule

When a neutral file exists under `docs/project/` and an older equivalent still
exists under an adapter-owned location, prefer the neutral file as canonical.
The adapter copy should be treated as a mirror or helper unless the neutral file
explicitly says otherwise.
