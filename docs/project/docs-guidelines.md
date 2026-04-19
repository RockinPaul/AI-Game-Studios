# Documentation Guidelines

These guidelines define how to maintain the runtime-neutral documentation layer
under `docs/project/`.

## Objectives

- Keep neutral docs aligned with `docs/project/workflow-catalog.yaml`.
- Describe workflows by artifacts and outcomes, not by a single runtime's UI.
- Make it easy for an agent to answer three questions quickly:
  what phase is active, what artifact is required next, and what review must
  happen before advancing.

## Required Structure for Workflow Docs

Each file in `docs/project/workflows/` should include these sections:

- `Phase Goal`
- `Required Artifacts`
- `Optional Artifacts`
- `Review Points`
- `Runtime-Neutral Execution Guidance`

Keep the section names stable so agents can scan them mechanically.

## Source of Truth

- Treat `docs/project/workflow-catalog.yaml` as authoritative for phase order,
  artifact paths, and required versus optional steps.
- If a neutral workflow doc intentionally covers material outside the catalog,
  label it clearly. `workflows/onboarding.md` is the current example because it
  is an orientation layer rather than a catalog phase.
- When the catalog changes, update the corresponding workflow doc in the same
  change set when possible.

## Writing Rules

- Prefer artifact paths over abstract descriptions.
- Describe reviews as decision points, not as tool invocations.
- Avoid adapter-specific command language except in an explicitly labeled
  example section.
- If adapter examples are useful, label them `Adapter Example` and keep them
  secondary to the neutral guidance.
- Use repository paths exactly as they appear in the catalog so agents can
  navigate without translation.

## Template Rules

- Neutral templates belong in `docs/project/templates/`.
- Templates should be usable by people or agents without assuming a specific
  toolchain.
- If a neutral template is derived from an adapter-specific template, preserve
  the artifact purpose and expected output shape, but remove runtime-specific
  wording unless it is relevant as an example.

## Architecture Decision Records (`docs/architecture/`)

Use the ADR template: `docs/project/templates/architecture-decision-record.md`

**Required sections:** Title, Status, Context, Decision, Consequences,
ADR Dependencies, Engine Compatibility, GDD Requirements Addressed

**Status lifecycle:** `Proposed` -> `Accepted` -> `Superseded`

**TR Registry:** `docs/architecture/tr-registry.yaml`
- Stable requirement IDs link GDD requirements to stories.
- Never renumber existing IDs.

**Control Manifest:** `docs/architecture/control-manifest.md`
- Flat programmer rules sheet: Required / Forbidden / Guardrails per layer
- Date-stamped `Manifest Version:` in header

## Engine Reference (`docs/engine-reference/`)

Version-pinned engine API snapshots live here. Always check them before using
post-cutoff engine APIs.

## Discovery Expectations

- `docs/project/README.md` must link every workflow doc and every neutral
  template.
- Workflow docs should link to the next phase when progression is linear.
- When a workflow depends on a reusable report or retrospective format, name the
  matching template explicitly.

## Maintenance Checklist

- Confirm phase order still matches `docs/project/workflow-catalog.yaml`.
- Confirm every required artifact path in the workflow doc still matches the
  catalog.
- Confirm optional artifacts still reflect optional or advisory steps.
- Confirm the `Review Points` section reflects the current approval or audit
  expectations.
- Confirm all links from `docs/project/README.md` still resolve.
