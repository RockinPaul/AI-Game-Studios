# Phaser Engine Support Design

Date: 2026-04-26
Status: Approved for planning

## Goal

Add Phaser 4 as a first-class engine option wherever this template currently
supports Godot, Unity, and Unreal. Phaser should be selectable during engine
setup, visible in public docs, routable through neutral and Claude adapter role
libraries, covered by version-pinned reference docs, and represented in the
skill testing framework.

Official Phaser AI skills will be vendored under
`docs/engine-reference/phaser/skills/` only. They will not become top-level
slash commands in `.claude/skills/` or `.agents/skills/`.

## Sources

- Phaser API docs: https://docs.phaser.io/api-documentation/api-documentation
- Phaser GitHub release/tag: https://github.com/phaserjs/phaser/releases/tag/v4.0.0
- Phaser official skills: https://github.com/phaserjs/phaser/tree/v4.0.0/skills
- npm package metadata confirms `phaser@4.0.0` as `latest` on 2026-04-26.

## Engine Model

Pinned engine:

- Engine: Phaser
- Version: 4.0.0
- Language: TypeScript primary, JavaScript supported
- Build system: npm scripts with Vite-style browser bundling
- Asset pipeline: Phaser Loader, texture atlases, audio assets, web-optimized
  static assets
- Testing default: Vitest for pure logic, Playwright for browser/canvas smoke and
  integration tests

Phaser should be framed honestly as the web-first 2D engine option:

- Strong fit: browser games, 2D arcade/action/puzzle/card/UI-heavy games,
  playable prototypes, web distribution, TypeScript workflows.
- Weak fit: native-first console projects, large 3D worlds, AAA visual targets,
  projects needing editor-centric workflows like Unity/Godot/Unreal.

## Agent Additions

Add Phaser engine roles in all three role surfaces:

- Neutral roles under `agents/engine/`
- Claude adapter roles under `.claude/agents/`
- Skill testing framework fixtures under
  `CCGS Skill Testing Framework/agents/engine/phaser/`

Roles:

- `phaser-specialist`: primary Phaser architecture, scene/plugin structure,
  loader, scale, deployment, and routing.
- `phaser-typescript-specialist`: TypeScript/JavaScript scene code, typing,
  module boundaries, state/data patterns.
- `phaser-rendering-specialist`: WebGL renderer, cameras, shaders, post-fx,
  particles, texture atlas and pixel-art rendering concerns.
- `phaser-physics-specialist`: Arcade Physics, Matter Physics, collision
  patterns, deterministic constraints and performance risks.
- `phaser-ui-specialist`: DOM overlay, Phaser text/bitmap text, responsive UI,
  input routing and accessibility handoff.

The primary Phaser specialist must read `docs/engine-reference/phaser/VERSION.md`
before suggesting Phaser API code, then use the module docs and official skills
under `docs/engine-reference/phaser/skills/` for subsystem-specific guidance.

## Documentation Updates

Update every engine list that currently names Godot, Unity, and Unreal so Phaser
appears as a peer option:

- `README.md`
- `CLAUDE.md`
- `docs/WORKFLOW-GUIDE.md`
- `docs/project/agent-roster.md`
- `.claude/docs/agent-roster.md`
- `docs/engine-reference/README.md`
- `docs/project/technical-preferences.md` comments/placeholders only where they
  enumerate engine examples
- `.gitignore` engine sections if Phaser web build artifacts are not already
  ignored by generic Node/web patterns

## Skill Updates

Update both adapter mirrors when a skill has a `.claude/skills/` and
`.agents/skills/` copy.

Required updates:

- `setup-engine`: add Phaser to guided selection, platform/genre tradeoffs,
  stack template, technical-preference defaults, file routing, knowledge-risk
  baseline, and reference-doc creation logic.
- `brainstorm`: add Phaser to engine-experience and recommendation surfaces.
- `test-setup`: add Phaser test scaffold and CI workflow using npm, Vitest, and
  Playwright.
- `test-helpers`: add Phaser helper guidance for scene/game lifecycle tests.
- `smoke-check`: add Phaser command selection for browser smoke checks.
- Any team/review skills that route through `Engine Specialists` should need no
  hardcoded Phaser branch if they already read `docs/project/technical-preferences.md`.
  Verify this during implementation.

## Engine Reference Docs

Create `docs/engine-reference/phaser/`:

- `VERSION.md`: version pin, release date, last verified date, knowledge-gap
  warning, source list.
- `breaking-changes.md`: summarize high-risk Phaser 3 to Phaser 4 migration
  changes and post-cutoff risks.
- `deprecated-apis.md`: lookup table for Phaser 3 or older patterns that should
  not be suggested for Phaser 4.
- `current-best-practices.md`: TypeScript, scenes, loader, scale manager,
  rendering, physics, testing and packaging guidance.
- `modules/`: concise subsystem references for setup/config, scenes,
  loading-assets, input, physics, rendering, animation, audio, UI/text, tilemaps,
  particles and cameras.
- `skills/`: official Phaser AI skills from `phaserjs/phaser@v4.0.0/skills`.

Reference docs should cite official Phaser docs and repository URLs. Module files
should stay concise enough for agents to load only the relevant subsystem.

## Testing Framework Updates

Update the CCGS Skill Testing Framework so Phaser is represented consistently:

- Add Phaser entries to the catalog.
- Add Phaser agent fixtures.
- Update rubric engine-agent list.
- Update utility skill fixtures that currently assume three engines.
- Update test-setup fixtures to include Phaser web test expectations.

Fixture expectations should validate that Phaser agents:

- Read `docs/engine-reference/phaser/` first.
- Route TypeScript, rendering, physics, and UI requests to the right specialist.
- Avoid Phaser 3-only patterns when Phaser 4 guidance differs.
- Treat browser runtime and canvas verification as part of testing.

## Verification

Implementation is complete when:

- `rg -n "Godot|godot"` surfaces no engine-option area where Phaser is missing.
- `rg -n "Unity|Unreal|Godot"` engine lists include Phaser where they enumerate
  supported engines.
- `rg -n "Phaser|phaser"` shows expected docs, agents, skill, fixture, and
  reference entries.
- Markdown/YAML structure remains valid enough to parse manually; any available
  repository validation scripts should run.
- `git diff --check` passes.

## Out of Scope

- Do not create top-level `/phaser-*` slash commands.
- Do not install Phaser npm dependencies into this template.
- Do not scaffold an actual Phaser game project.
- Do not replace existing Godot, Unity, or Unreal behavior.
