# Systems Design Workflow

Derived from the `systems-design` phase in `docs/project/workflow-catalog.yaml`.

## Phase Goal

Produce approved design documentation for each MVP system and validate the full
design set for cross-system consistency before architecture begins.

## Required Artifacts

- Approved MVP system GDDs under `design/gdd/`
  Condition: use `design/gdd/systems-index.md` as the tracker; each MVP system
  should have an approved design state.
- `design/gdd/gdd-cross-review-*.md`

## Optional Artifacts

- Additional consistency check outputs when the design set changes mid-stream.

## Review Points

- Review each system design independently before treating it as approved.
- Review the entire MVP design set together to catch contradictions,
  dependency issues, and balance or scope conflicts.
- Re-run a consistency pass when new systems are added or existing GDDs change
  in ways that could affect upstream or downstream systems.

## Runtime-Neutral Execution Guidance

1. Use `design/gdd/systems-index.md` as the authoritative list of systems to
   design.
2. Design MVP systems first, in dependency order.
3. Write each system GDD with enough specificity that implementation and QA do
   not have to invent rules later.
4. Mark review state in the system artifact or the systems index so the current
   approval status is visible.
5. After all MVP systems are individually reviewed, perform a holistic review of
   the full design set and save the results as `design/gdd/gdd-cross-review-*.md`.
6. Do not enter technical setup while core system rules, dependencies, or
   acceptance criteria remain unresolved.

## Next Workflow

After MVP system designs are approved and the cross-review is complete, continue
to `technical-setup.md`.
