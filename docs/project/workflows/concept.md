# Concept Workflow

Derived from the `concept` phase in `docs/project/workflow-catalog.yaml`.

## Phase Goal

Turn a game idea into a documented concept with engine context, visual
direction, and a systems map that is ready to hand off into system-level design.

## Required Artifacts

- `docs/project/technical-preferences.md`
  Condition: engine information is filled in.
- `design/gdd/game-concept.md`
- `design/art/art-bible.md`
- `design/gdd/systems-index.md`

## Optional Artifacts

- Brainstorming notes or equivalent ideation capture.
- A concept review record before advancing.

## Review Points

- Review the concept for clarity, pillars, and scope boundaries before the team
  invests in downstream design.
- Confirm the engine choice and technical preferences are explicit enough for
  architecture and UX work.
- Confirm the art bible establishes a usable visual identity.
- Confirm the systems index enumerates the MVP systems and dependency ordering.

## Runtime-Neutral Execution Guidance

1. Explore and narrow the game concept until the core fantasy, pillars, and
   scope are explicit.
2. Run the neutral engine setup workflow in `workflows/engine-setup.md`, then
   record engine choice, version, conventions, and budgets in
   `docs/project/technical-preferences.md`.
3. Write `design/gdd/game-concept.md` using a structure that captures concept,
   target player experience, core loop, pillars, and scope.
4. Write `design/art/art-bible.md` so visual production has a stable source of
   truth.
5. Decompose the concept into systems in `design/gdd/systems-index.md`, with
   dependency ordering and priority tiers.
6. Do not move to systems design until the MVP system set is visible in the
   systems index.

## Next Workflow

After the required artifacts are present and reviewed, continue to
`systems-design.md`.
