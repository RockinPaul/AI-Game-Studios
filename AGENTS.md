# Game Studios Template -- Neutral Agent Entry

This file is the runtime-neutral entrypoint for agents that do not use
`CLAUDE.md` as their primary project instruction file.

## Start Here

- Shared project guidance: `docs/project/README.md`
- Canonical phase catalog: `docs/project/workflow-catalog.yaml`
- Neutral workflow docs: `docs/project/workflows/`
- Neutral role library: `agents/README.md`
- Shared coordination rules: `docs/project/coordination-rules.md`
- Shared coding standards: `docs/project/coding-standards.md`
- Shared context policy: `docs/project/context-management.md`
- Workflow overview: `docs/project/workflow-overview.md`
- Runtime capabilities: `docs/project/runtime-capabilities.md`
- Skill disposition: `docs/project/skill-disposition.md`
- Neutral-core readiness: `docs/project/neutral-core-readiness.md`
- Runtime support matrix: `docs/platforms/support-matrix.md`

## Non-Claude Quick Start

If you are not using Claude Code, use this first-run sequence:

1. Read `docs/project/README.md`.
2. Read `agents/README.md` and `docs/project/agent-roster.md`.
3. Read `docs/project/coordination-rules.md` and `docs/project/runtime-capabilities.md`.
4. Start with `docs/project/workflows/onboarding.md`, then move through the phase docs by artifact and outcome.
5. Fill in project-specific choices in `docs/project/technical-preferences.md` when the workflow calls for them.

## Current Adapter State

The repository now exposes a neutral documentation layer for multi-agent use.
The existing Claude adapter remains in place:

- Claude root entry: `CLAUDE.md`
- Claude adapter assets: `.claude/`

If your runtime supports agent delegation, role selection, or structured user
choice UIs, treat the documents in `docs/project/` as the canonical shared
behavior and map your runtime's own tools onto that behavior.

## Project Artifacts

The project data model is already runtime-neutral. Core working areas remain:

- `design/` for design docs
- `docs/architecture/` for ADRs and technical decisions
- `src/` for implementation
- `tests/` for verification
- `production/` for sprint and release artifacts

## Transitional Note

The workflow and skill layer under `.claude/skills/` is still the most complete
adapter implementation. Other runtimes should use the neutral docs in
`docs/project/` plus `agents/` until additional adapters are added.
