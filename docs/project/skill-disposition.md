# Skill Disposition

This document records the migration disposition for the current Claude skills.

## Bucket A -- Core Workflow Wrappers

These skills should remain in `.claude/skills/` as Claude adapter entrypoints,
but the workflow meaning they expose must be defined in the neutral core.

Examples:
- `start`
- `setup-engine`
- `project-stage-detect`
- `adopt`
- `brainstorm`
- `map-systems`
- `design-system`
- `create-architecture`
- `architecture-decision`
- `create-epics`
- `create-stories`
- `sprint-plan`
- `gate-check`

**Disposition:**
- Keep as Claude adapter wrappers
- Point docs to neutral workflow references first
- Retain slash-command UX as adapter behavior only

## Bucket B -- Shared-Artifact Consumers

These skills may stay Claude-specific operationally, but they should read
neutral-core files instead of old `.claude/docs/*` shared-doc locations.

Common retargets:
- `docs/project/technical-preferences.md`
- `docs/project/coding-standards.md`
- `docs/project/design-guidelines.md`
- `docs/project/docs-guidelines.md`
- `docs/project/workflow-catalog.yaml`

**Disposition:**
- Keep in Claude adapter
- Retarget shared-file references to neutral canonical files
- Only extract further if another runtime needs direct equivalents

## Bucket C -- Claude-Only Convenience / Orchestration

These skills rely heavily on Claude UX, Claude tool semantics, or Claude
subagent orchestration and should remain explicitly adapter-specific for now.

Examples:
- `help`
- `team-*`
- `skill-test`
- `skill-improve`

**Disposition:**
- Mark as Claude adapter features in docs
- Document neutral fallback behavior where helpful
- Do not block neutral-core readiness on cross-runtime equivalents

## High-Priority Retarget Candidates

These are the first Claude skills that should eventually be retargeted to the
neutral core because they currently read old shared paths directly:

- `start`
- `setup-engine`
- `help`
- `ux-design`
- `ux-review`
- `test-setup`
- `test-helpers`
- `create-architecture`
- `create-control-manifest`
- `dev-story`
- `code-review`
- `adopt`
- `architecture-decision`
- `architecture-review`

## Portability Rule

The neutral-core migration is complete when every skill falls into one of the
three buckets above and the bucket choice is explicit in repo documentation.
