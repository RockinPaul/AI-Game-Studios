# Neutral Core Readiness

This document records the current finish-line status for the neutral-core
migration.

## Finish Line

The migration is considered complete when a non-Claude agent can:

1. start from `AGENTS.md`
2. discover the canonical workflow and project rules under `docs/project/`
3. discover the neutral role library under `agents/`
4. understand phase progression, required artifacts, and review points without
   treating `.claude/` as the canonical system definition

## Current Verdict

**Verdict:** READY

The neutral core is usable for non-Claude agents.

## Canonical Neutral-Core Surfaces

- Entry point: `AGENTS.md`
- Shared docs hub: `docs/project/README.md`
- Canonical workflow catalog: `docs/project/workflow-catalog.yaml`
- Phase-by-phase workflow docs: `docs/project/workflows/`
- Workflow overview: `docs/project/workflow-overview.md`
- Runtime capability contract: `docs/project/runtime-capabilities.md`
- Orchestration contract: `docs/project/orchestration-contract.md`
- Canonical technical preferences: `docs/project/technical-preferences.md`
- Neutral role library: `agents/`
- Neutral roster index: `docs/project/agent-roster.md`
- Neutral templates: `docs/project/templates/`
- Skill inventory/disposition: `docs/project/skill-inventory.md`, `docs/project/skill-disposition.md`

## Adapter-Specific Surfaces

These remain adapter-owned and are not the neutral core:

- `CLAUDE.md`
- `.claude/settings.json`
- `.claude/hooks/`
- `.claude/statusline.sh`
- `.claude/skills/`
- `.claude/agents/`

## Documented Mirror / Compatibility Areas

These still exist for Claude compatibility during migration:

- `.claude/docs/workflow-catalog.yaml`
  - Canonical source remains `docs/project/workflow-catalog.yaml`
- `.claude/docs/technical-preferences.md`
  - Canonical source remains `docs/project/technical-preferences.md`

These mirrors are acceptable for current compatibility, but they remain drift
risks until the remaining Claude consumers are fully retargeted.

## What A Non-Claude Agent Should Read

Recommended onboarding order:

1. `AGENTS.md`
2. `docs/project/README.md`
3. `agents/README.md`
4. `docs/project/agent-roster.md`
5. `docs/project/workflows/onboarding.md`
6. `docs/project/workflow-catalog.yaml`
7. `docs/project/runtime-capabilities.md`
8. `docs/project/technical-preferences.md` when the workflow calls for it

## Validation Checklist

- [x] `AGENTS.md` points to neutral workflow docs and the neutral role library.
- [x] `docs/project/workflow-catalog.yaml` is documented as canonical.
- [x] `docs/project/workflows/` exists and covers onboarding plus all 7 phases.
- [x] `agents/` exists as a runtime-neutral role library.
- [x] Shared docs no longer require `.claude/docs/*` as the canonical source.
- [x] Claude docs describe their workflow catalog and technical preferences as mirrors/adapter-specific copies.
- [x] Older stale counts/wording in major docs and framework docs have been swept.

## Remaining Risks

### Medium

- Many unchanged Claude skills still read `.claude/docs/technical-preferences.md`
  directly. The mirror contract prevents breakage, but manual drift is still
  possible.
- The Claude workflow catalog mirror can still diverge from the neutral catalog
  if future edits are not disciplined.

### Low

- Some older docs outside the main entry surfaces may still contain Claude-heavy
  phrasing or older structural assumptions.
- Template references are now split between neutral templates and Claude mirror
  templates; long-term maintenance should continue moving shared templates into
  `docs/project/templates/` first.

## Recommended Next Cleanup

1. Retarget the remaining high-frequency Claude skill consumers of
   `.claude/docs/technical-preferences.md`.
2. Continue reducing stale adapter phrasing in older non-entry docs.
3. Optionally add a second runtime adapter to prove the neutral-core design in
   practice.
