# Onboarding Workflow

This guide is a neutral orientation layer that runs before the catalog phases.
It helps a non-Claude agent determine where the project stands and which phase
workflow to open next.

## Phase Goal

Establish repository context, identify the current project stage, and route the
runtime to the correct workflow document under `docs/project/workflows/`.

## Required Artifacts

- `docs/project/workflow-catalog.yaml` as the authoritative phase source.
- Repository layout awareness for `design/`, `docs/architecture/`, `src/`,
  `tests/`, `prototypes/`, and `production/`.

## Optional Artifacts

- `production/` stage evidence such as sprint plans, playtest reports, or epics.
- `docs/project/templates/project-stage-report.md` if you generate a stage
  analysis.
- Any existing milestone, release, or architecture artifact that helps classify
  the current phase.

## Review Points

- Confirm the active phase by inspecting artifacts, not by guessing.
- Confirm whether the project is greenfield or brownfield.
- Confirm the next missing required artifact before doing implementation work.
- If project maturity is unclear, write a stage analysis using
  `docs/project/templates/project-stage-report.md`.

## Runtime-Neutral Execution Guidance

1. Read `docs/project/workflow-catalog.yaml` to learn the canonical phase order.
2. Inspect the repository for the required artifacts listed in each phase.
3. Classify the project into the latest phase whose required artifacts are
   present and reasonably complete.
4. If there are mixed signals, write a stage analysis report before choosing the
   next step.
5. Open the workflow doc for the identified phase and continue from there.

## Phase Routing

- If concept artifacts are missing, continue to `concept.md`.
- If concept artifacts exist but MVP system design is incomplete, continue to
  `systems-design.md`.
- If design work is approved but architecture and control rules are missing,
  continue to `technical-setup.md`.
- If architecture exists but UX, prototyping, epics, stories, or first sprint
  planning are incomplete, continue to `pre-production.md`.
- If sprint execution is underway, continue to `production.md`.
- If the product is feature-complete and focus has shifted to stabilization,
  continue to `polish.md`.
- If launch preparation is underway, continue to `release.md`.
