# Design Guidelines

These guidelines help a non-Claude runtime produce design artifacts that fit the
Game Studios workflow.

## Design Artifacts by Phase

| Phase | Primary Design Outputs |
| --- | --- |
| Concept | `design/gdd/game-concept.md`, `design/art/art-bible.md`, `design/gdd/systems-index.md` |
| Systems Design | Per-system GDDs in `design/gdd/`, plus cross-review output |
| Technical Setup | `design/accessibility-requirements.md` and architecture-linked design constraints |
| Pre-Production | `design/ux/*.md`, optional asset specifications, prototype notes |
| Production onward | Design revisions, quick specs, QA evidence, playtest findings, and release notes support |

Use the per-phase workflow docs in `docs/project/workflows/` to determine which
artifact is expected next.

## Core Principles

- Write design documents before implementation where the workflow expects them.
- Resolve ambiguity in the design artifact rather than leaving it for code.
- Keep dependencies explicit between concept, systems, UX, and architecture.
- Make validation possible: acceptance criteria should be observable and
  testable.
- Keep status markers current when a document template includes them.

## Minimum Quality Bar for System Design

For each MVP system, the design set should make these questions answerable
without guesswork:

- What player need or fantasy does this system serve?
- What are the rules, formulas, and edge cases?
- Which upstream and downstream systems depend on it?
- Which values are intended to be tuned later?
- How will the team know the design is correctly implemented?

## GDD Files (`design/gdd/`)

Every system GDD should include all 8 required sections in this order:

1. Overview
2. Player Fantasy
3. Detailed Rules
4. Formulas
5. Edge Cases
6. Dependencies
7. Tuning Knobs
8. Acceptance Criteria

**File naming:** `[system-slug].md`

**Systems index:** `design/gdd/systems-index.md` should be updated when adding a
new GDD.

**Design order:** Foundation -> Core -> Feature -> Presentation -> Polish

## Cross-Document Consistency

- The concept document defines pillars and scope boundaries.
- The systems index decomposes that concept into implementable systems.
- Per-system GDDs should reference the systems index naming and dependency model.
- UX specs should reference the related GDDs and the accessibility commitment.
- Architecture documents and ADRs should trace back to design requirements.

When these drift, update the design artifact first or document a conscious
change, then propagate it through architecture and planning artifacts.

## Quick Specs (`design/quick-specs/`)

Use lightweight specs for tuning changes, minor mechanics, or balance
adjustments.

## UX Specs (`design/ux/`)

- Per-screen specs: `design/ux/[screen-name].md`
- HUD design: `design/ux/hud.md`
- Interaction pattern library: `design/ux/interaction-patterns.md`
- Accessibility requirements: `design/accessibility-requirements.md`

## Review Expectations

- Concept work should be reviewed before systems proliferate.
- Each system design should be reviewed on its own merits.
- All MVP GDDs should receive a cross-document consistency pass.
- UX work should be reviewed against both design intent and accessibility.
- Design revisions during production should be reflected in the relevant design
  files, not only in implementation notes.

## Recommended Supporting Templates

- Use `docs/project/templates/project-stage-report.md` when a stage analysis is
  needed before deciding which design work comes next.
- Use `docs/project/templates/post-mortem.md` for sprint, milestone, or project
  retrospectives that drive design-process improvements.
