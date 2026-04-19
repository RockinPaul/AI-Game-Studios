# Release Workflow

Derived from the `release` phase in `docs/project/workflow-catalog.yaml`.

## Phase Goal

Prepare the game for launch by completing release validation, producing player-
facing communication artifacts, and confirming final launch readiness.

## Required Artifacts

- A completed release checklist in the project's release-tracking location.
- A completed launch checklist in the project's release-tracking location.

## Optional Artifacts

- Patch notes.
- Changelog.
- `docs/project/templates/post-mortem.md` for retrospective follow-through after
  launch or milestone completion.

## Review Points

- Review the release checklist across code, content, store, legal, and
  operational readiness.
- Review the launch checklist as the final go or no-go decision point.
- Review patch notes and changelog outputs so public and internal audiences get
  the right level of detail.

## Runtime-Neutral Execution Guidance

1. Run a release readiness pass that validates the product across departments,
   not only in code.
2. Record the release checklist results in the project's normal release-tracking
   location.
3. Produce patch notes if the release needs player-facing change communication.
4. Produce a changelog if the release needs internal historical tracking.
5. Complete a final launch readiness checklist before shipping.
6. Do not treat optional communication artifacts as substitutes for the required
   release and launch validation work.

## Supporting Template

For retrospective learning after release, use
`docs/project/templates/post-mortem.md`.
