# Pre-Production Workflow

Derived from the `pre-production` phase in `docs/project/workflow-catalog.yaml`.

## Phase Goal

Convert approved design and architecture into implementable UX, prototype
evidence, scoped epics and stories, and a first sprint plan.

## Required Artifacts

- At least one UX spec in `design/ux/*.md`
- At least one prototype README in `prototypes/*/README.md`
- At least one epic in `production/epics/*/EPIC.md`
- Story artifacts under `production/epics/**/*.md`
  Condition: at least two matching files so the epic set is decomposed into
  implementable work.
- At least one sprint plan in `production/sprints/sprint-*.md`
- At least one playtest report in `production/playtests/*.md`

## Optional Artifacts

- `design/assets/asset-manifest.md`
- Test framework scaffold under `tests/`

## Review Points

- Review UX specs for alignment with design intent and accessibility commitments.
- Review the prototype to confirm the core loop is worth building further.
- Review epics and stories for architectural traceability and implementation
  readiness.
- Review the first sprint plan for realistic sequencing and scope.
- Review the first vertical slice playtest to confirm the product is ready for
  production investment.

## Runtime-Neutral Execution Guidance

1. Write the key UX specifications in `design/ux/` for the main menu, core HUD,
   and other high-value player flows.
2. Review the UX set before creating implementation work.
3. Build at least one throwaway prototype in `prototypes/` and document it with
   a README that explains purpose, findings, and limitations.
4. Optionally generate asset specs or an asset manifest if art production needs
   a formal handoff.
5. Convert approved design and architecture into epics under
   `production/epics/`, then break those epics into story files.
6. If the project needs automated testing infrastructure before sprint work,
   scaffold it under `tests/`.
7. Create the first sprint plan and capture at least one vertical slice playtest
   report before moving into sustained production.

## Next Workflow

After the first sprint is planned and the vertical slice has been playtested,
continue to `production.md`.
