# Polish Workflow

Derived from the `polish` phase in `docs/project/workflow-catalog.yaml`.

## Phase Goal

Improve performance, balance, presentation quality, and player experience while
validating the product through repeated playtesting.

## Required Artifacts

- At least three playtest reports in `production/playtests/*.md`

## Optional Artifacts

- Performance profiling outputs.
- Balance analysis outputs.
- Asset audit outputs.
- Additional issue logs created from coordinated polish passes.

## Review Points

- Review playtest coverage across onboarding, mid-game, and difficulty curve.
- Review coordinated polish findings across performance, audio, visual quality,
  and UX.
- Review performance and balance issues before they become release blockers.
- Review asset quality and compliance if large-scale content production occurred.

## Runtime-Neutral Execution Guidance

1. Run repeated playtest sessions and save each report to `production/playtests/`.
2. Ensure the playtest set covers at least the new player experience,
   mid-progression systems, and overall difficulty curve.
3. Profile and tune performance where needed.
4. Inspect balance data and progression curves where needed.
5. Audit asset quality and conformance where needed.
6. Perform an integrated polish pass that considers technical quality, UX,
   visual cohesion, and audio feedback together rather than in isolation.
7. Use the findings to create final fixes or release blockers before entering the
   release workflow.

## Next Workflow

After the product has enough playtest evidence and the major polish blockers are
under control, continue to `release.md`.
