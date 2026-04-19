# Production Workflow

Derived from the `production` phase in `docs/project/workflow-catalog.yaml`.

## Phase Goal

Run the project through repeatable sprint cycles that pick ready stories,
implement them, review them, and capture quality and planning feedback.

## Required Artifacts

- Sprint plans in `production/sprints/sprint-*.md`
- Active implementation evidence in `src/`
- Story tracking under `production/epics/**/*.md`
  Condition: stories should show in-progress or completed state as work moves.

## Optional Artifacts

- QA plans for epics or sprints.
- Bug reports and triage outputs.
- Retrospectives.
- Scope review outputs tied to sprint changes.

## Review Points

- Review story readiness before implementation when a story is unclear.
- Review completed work against acceptance criteria before closing a story.
- Review code when a feature has architectural risk or spans multiple systems.
- Review sprint scope whenever new work is added mid-sprint.
- Review sprint outcomes at the end of each sprint using a retrospective.

## Runtime-Neutral Execution Guidance

1. Create or update the current sprint plan before starting work.
2. Select stories that are ready and trace back to the approved design and
   architecture.
3. Implement stories in `src/` and update story state in
   `production/epics/**/*.md`.
4. Use a completion review before marking a story done so acceptance criteria,
   deviations, and missing tests are surfaced.
5. Generate QA plans or bug reports when feature complexity or defect volume
   makes them useful.
6. Run retrospectives regularly enough that delivery issues are captured before
   they become systemic.
7. Treat sprint status snapshots and scope checks as advisory controls for
   planning, not as replacements for story-level review.

## Next Workflow

When the project is feature-complete enough that the main focus becomes
stabilization and experience quality rather than new feature throughput,
continue to `polish.md`.
