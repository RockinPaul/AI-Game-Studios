# Phaser Engine Support Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Add Phaser 4.0.0 as a first-class peer engine option beside Godot, Unity, and Unreal across docs, role routing, setup/test skills, reference docs, and framework fixtures.

**Architecture:** Keep runtime-neutral docs canonical under `docs/project/`, keep Claude adapter mirrors under `.claude/`, and keep Codex/agents mirrors under `.agents/` where the repo already contains them. Vendor official Phaser AI skills only under `docs/engine-reference/phaser/skills/`, then route Phaser agents to that reference location instead of adding top-level slash commands.

**Tech Stack:** Markdown, YAML, shell verification with `rg`, official Phaser 4.0.0 docs and GitHub tag, TypeScript/Vite/Vitest/Playwright as Phaser project defaults.

---

## File Map

Create:

- `docs/engine-reference/phaser/VERSION.md`
- `docs/engine-reference/phaser/breaking-changes.md`
- `docs/engine-reference/phaser/deprecated-apis.md`
- `docs/engine-reference/phaser/current-best-practices.md`
- `docs/engine-reference/phaser/modules/setup-config.md`
- `docs/engine-reference/phaser/modules/scenes.md`
- `docs/engine-reference/phaser/modules/loading-assets.md`
- `docs/engine-reference/phaser/modules/input.md`
- `docs/engine-reference/phaser/modules/physics.md`
- `docs/engine-reference/phaser/modules/rendering.md`
- `docs/engine-reference/phaser/modules/animation.md`
- `docs/engine-reference/phaser/modules/audio.md`
- `docs/engine-reference/phaser/modules/ui-text.md`
- `docs/engine-reference/phaser/modules/tilemaps.md`
- `docs/engine-reference/phaser/modules/particles.md`
- `docs/engine-reference/phaser/modules/cameras.md`
- `docs/engine-reference/phaser/skills/` copied from `phaserjs/phaser@v4.0.0/skills/`
- `agents/engine/phaser-specialist.md`
- `agents/engine/phaser-typescript-specialist.md`
- `agents/engine/phaser-rendering-specialist.md`
- `agents/engine/phaser-physics-specialist.md`
- `agents/engine/phaser-ui-specialist.md`
- `.claude/agents/phaser-specialist.md`
- `.claude/agents/phaser-typescript-specialist.md`
- `.claude/agents/phaser-rendering-specialist.md`
- `.claude/agents/phaser-physics-specialist.md`
- `.claude/agents/phaser-ui-specialist.md`
- `CCGS Skill Testing Framework/agents/engine/phaser/phaser-specialist.md`
- `CCGS Skill Testing Framework/agents/engine/phaser/phaser-typescript-specialist.md`
- `CCGS Skill Testing Framework/agents/engine/phaser/phaser-rendering-specialist.md`
- `CCGS Skill Testing Framework/agents/engine/phaser/phaser-physics-specialist.md`
- `CCGS Skill Testing Framework/agents/engine/phaser/phaser-ui-specialist.md`

Modify:

- `README.md`
- `CLAUDE.md`
- `docs/WORKFLOW-GUIDE.md`
- `docs/engine-reference/README.md`
- `docs/project/agent-roster.md`
- `docs/project/technical-preferences.md`
- `.claude/docs/agent-roster.md`
- `.gitignore`
- `.claude/skills/setup-engine/SKILL.md`
- `.agents/skills/setup-engine/SKILL.md`
- `.claude/skills/brainstorm/SKILL.md`
- `.agents/skills/brainstorm/SKILL.md`
- `.claude/skills/test-setup/SKILL.md`
- `.agents/skills/test-setup/SKILL.md`
- `.claude/skills/test-helpers/SKILL.md`
- `.agents/skills/test-helpers/SKILL.md`
- `.claude/skills/smoke-check/SKILL.md`
- `.agents/skills/smoke-check/SKILL.md`
- `CCGS Skill Testing Framework/catalog.yaml`
- `CCGS Skill Testing Framework/quality-rubric.md`
- `CCGS Skill Testing Framework/README.md`
- `CCGS Skill Testing Framework/CLAUDE.md`
- `CCGS Skill Testing Framework/templates/agent-test-spec.md`
- `CCGS Skill Testing Framework/skills/utility/setup-engine.md`
- `CCGS Skill Testing Framework/skills/utility/start.md`
- `CCGS Skill Testing Framework/skills/utility/test-setup.md`

Protect:

- Do not stage the whole untracked `.agents/` directory with `git add .agents/`.
- Stage exact `.agents/skills/.../SKILL.md` files that this plan modifies.
- Do not create `.claude/skills/phaser-*` or `.agents/skills/phaser-*`.

---

### Task 1: Add Failing Acceptance Checks

**Files:**
- Create: `/tmp/phaser-support-checks.sh`
- No repository files modified.

- [ ] **Step 1: Write a temporary acceptance script**

Run:

```bash
cat > /tmp/phaser-support-checks.sh <<'EOF'
#!/usr/bin/env bash
set -euo pipefail

cd /workspace/AI-Game-Studios

require_rg() {
  local pattern="$1"
  local path="$2"
  rg -n "$pattern" "$path" >/dev/null
}

require_path() {
  test -e "$1"
}

require_path docs/engine-reference/phaser/VERSION.md
require_path docs/engine-reference/phaser/current-best-practices.md
require_path docs/engine-reference/phaser/modules/scenes.md
require_path docs/engine-reference/phaser/skills/v4-new-features/SKILL.md

require_path agents/engine/phaser-specialist.md
require_path agents/engine/phaser-typescript-specialist.md
require_path agents/engine/phaser-rendering-specialist.md
require_path agents/engine/phaser-physics-specialist.md
require_path agents/engine/phaser-ui-specialist.md

require_path .claude/agents/phaser-specialist.md
require_path .claude/agents/phaser-typescript-specialist.md
require_path .claude/agents/phaser-rendering-specialist.md
require_path .claude/agents/phaser-physics-specialist.md
require_path .claude/agents/phaser-ui-specialist.md

require_path "CCGS Skill Testing Framework/agents/engine/phaser/phaser-specialist.md"

require_rg "Phaser" README.md
require_rg "Phaser" CLAUDE.md
require_rg "phaser-specialist" docs/project/agent-roster.md
require_rg "phaser-specialist" .claude/docs/agent-roster.md
require_rg "Phaser" docs/WORKFLOW-GUIDE.md
require_rg "phaser" docs/engine-reference/README.md

require_rg "Phaser 4" .claude/skills/setup-engine/SKILL.md
require_rg "Phaser 4" .agents/skills/setup-engine/SKILL.md
require_rg "Phaser" .claude/skills/brainstorm/SKILL.md
require_rg "Phaser" .agents/skills/brainstorm/SKILL.md
require_rg "Vitest" .claude/skills/test-setup/SKILL.md
require_rg "Vitest" .agents/skills/test-setup/SKILL.md
require_rg "Playwright" .claude/skills/smoke-check/SKILL.md
require_rg "Playwright" .agents/skills/smoke-check/SKILL.md

require_rg "phaser-specialist" "CCGS Skill Testing Framework/catalog.yaml"
require_rg "phaser-specialist" "CCGS Skill Testing Framework/quality-rubric.md"

if rg -n "claude/skills/phaser|agents/skills/phaser" . >/dev/null; then
  echo "Unexpected top-level Phaser skill found"
  exit 1
fi

echo "Phaser support acceptance checks passed"
EOF
chmod +x /tmp/phaser-support-checks.sh
```

- [ ] **Step 2: Run the script to confirm the current failure**

Run:

```bash
/tmp/phaser-support-checks.sh
```

Expected: FAIL before implementation, with the first missing Phaser path reported.

- [ ] **Step 3: Commit decision**

No commit for `/tmp/phaser-support-checks.sh`; it is a disposable verification script.

---

### Task 2: Vendor Official Phaser Skills Under Engine Reference

**Files:**
- Create: `docs/engine-reference/phaser/skills/`

- [ ] **Step 1: Fetch Phaser 4.0.0 source into `/tmp`**

Run:

```bash
rm -rf /tmp/phaser-v4.0.0
git clone --depth 1 --branch v4.0.0 https://github.com/phaserjs/phaser.git /tmp/phaser-v4.0.0
```

Expected: `/tmp/phaser-v4.0.0/skills/v4-new-features/SKILL.md` exists.

- [ ] **Step 2: Copy only the official skills directory**

Run:

```bash
mkdir -p docs/engine-reference/phaser
rm -rf docs/engine-reference/phaser/skills
cp -R /tmp/phaser-v4.0.0/skills docs/engine-reference/phaser/skills
```

- [ ] **Step 3: Verify skill count and location**

Run:

```bash
find docs/engine-reference/phaser/skills -name SKILL.md | sort | wc -l
find docs/engine-reference/phaser/skills -maxdepth 2 -name SKILL.md | sort
```

Expected: first command prints `28`. Output includes `docs/engine-reference/phaser/skills/v4-new-features/SKILL.md` and `docs/engine-reference/phaser/skills/v3-to-v4-migration/SKILL.md`.

- [ ] **Step 4: Run acceptance script**

Run:

```bash
/tmp/phaser-support-checks.sh
```

Expected: still FAIL because reference docs and agents are not created yet.

- [ ] **Step 5: Commit**

Run:

```bash
git add docs/engine-reference/phaser/skills
git commit -m "docs(phaser): vendor official ai skills"
```

---

### Task 3: Create Phaser Versioned Reference Docs

**Files:**
- Create: all `docs/engine-reference/phaser/*.md`
- Create: all `docs/engine-reference/phaser/modules/*.md`
- Modify: `docs/engine-reference/README.md`

- [ ] **Step 1: Create `VERSION.md`**

Write:

```markdown
# Phaser — Version Reference

| Field | Value |
|-------|-------|
| **Engine Version** | Phaser 4.0.0 |
| **Release Date** | 2026-04-10 |
| **Project Pinned** | 2026-04-26 |
| **Last Docs Verified** | 2026-04-26 |
| **LLM Knowledge Cutoff** | May 2025 |
| **Risk Level** | HIGH — Phaser 4 released after the model cutoff |

## Knowledge Gap Warning

Phaser 4.0.0 is newer than the LLM knowledge cutoff. Agents must verify Phaser
API usage against this directory, the official Phaser docs, and the vendored
official Phaser skills under `docs/engine-reference/phaser/skills/`.

## Verified Sources

- API docs: https://docs.phaser.io/api-documentation/api-documentation
- Release tag: https://github.com/phaserjs/phaser/releases/tag/v4.0.0
- Official skills: https://github.com/phaserjs/phaser/tree/v4.0.0/skills
- npm package: https://www.npmjs.com/package/phaser/v/4.0.0
```

- [ ] **Step 2: Create core reference files**

Create `breaking-changes.md` with these sections:

```markdown
# Phaser — Breaking Changes

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

## Phaser 3 to Phaser 4

- Phaser 4 is a post-cutoff major release. Treat Phaser 3 examples from older
  tutorials as suspect until checked against the official v4 docs or the
  vendored `v3-to-v4-migration` skill.
- Prefer TypeScript-friendly imports and module boundaries over global script-tag
  examples for new projects.
- Verify renderer, filter, post-fx, and shader examples against the v4 rendering
  docs because Phaser 4 changed renderer internals.
- Verify physics examples against the v4 Arcade and Matter docs before using
  Phaser 3 snippets from search results.

## Migration Source

- `docs/engine-reference/phaser/skills/v3-to-v4-migration/SKILL.md`
- https://github.com/phaserjs/phaser/releases/tag/v4.0.0
```

Create `deprecated-apis.md` with these entries:

```markdown
# Phaser — Deprecated or Risky Patterns

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

| Avoid | Use Instead | Reason |
|---|---|---|
| Unverified Phaser 3 tutorial snippets | Phaser 4 docs plus vendored v4 skills | Phaser 4 is a major post-cutoff release |
| Global `Phaser` script-tag architecture for app projects | TypeScript modules with explicit imports | Keeps project testable and compatible with modern bundlers |
| Polling every input in broad `update()` loops | Phaser input events or scoped update logic | Reduces frame work and makes tests easier |
| Loading assets inside active gameplay logic | Scene `preload()` and Loader events | Keeps loading lifecycle deterministic |
| Recreating text, particles, or temporary sprites each frame | Reuse, pool, or update existing game objects | Avoids browser GC spikes |
```

Create `current-best-practices.md` with these sections:

```markdown
# Phaser — Current Best Practices

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

## Project Shape

- Use TypeScript for new Phaser projects unless the project explicitly chooses
  plain JavaScript.
- Use Vite-style browser bundling for fast iteration and predictable CI.
- Keep Phaser scene classes thin; put game rules in plain TypeScript modules
  that Vitest can test without a browser canvas.

## Scene Lifecycle

- Load assets in `preload()`, construct world state in `create()`, and keep
  `update()` focused on per-frame behavior that cannot be event-driven.
- Use scene transitions deliberately. Document what data is passed through the
  registry, scene data, or a project-owned state module.

## Browser Runtime

- Test pure logic with Vitest and browser/canvas behavior with Playwright.
- Use stable canvas dimensions in smoke tests so screenshots and input positions
  are deterministic.
- Treat mobile browser, desktop browser, and embedded webview behavior as
  distinct platform targets when input or scaling matters.

## Performance

- Atlas sprites, reuse objects, and avoid allocations inside `update()`.
- Use Phaser cameras, groups, containers, and object pools deliberately; each has
  transform and traversal cost.
- Profile in browser dev tools and record the browser used for evidence.
```

- [ ] **Step 3: Create module files**

Create each module with the exact content blocks below.

`modules/setup-config.md`:

```markdown
# Phaser Module — Setup and Config

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Default stack: TypeScript, npm scripts, Vite, Vitest, Playwright.
- Keep Phaser config in one module such as `src/game/config.ts`.
- Set scale mode, parent element, background color, physics default, and scene
  list explicitly.
- Do not hide project-wide constants inside scene constructors.

Official skill: `docs/engine-reference/phaser/skills/game-setup-and-config/SKILL.md`
```

`modules/scenes.md`:

```markdown
# Phaser Module — Scenes

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Use scenes for lifecycle boundaries: boot, preload, menu, gameplay, HUD, and
  result screens.
- Keep game rules in plain TypeScript modules when possible.
- Pass scene data explicitly; avoid global mutable state unless documented.
- Keep `update()` small and event-driven behavior outside the hot path.

Official skill: `docs/engine-reference/phaser/skills/scenes/SKILL.md`
```

`modules/loading-assets.md`:

```markdown
# Phaser Module — Loading Assets

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Load assets in `preload()` or a dedicated preload scene.
- Use texture atlases for sprite-heavy games.
- Track Loader progress for loading screens instead of assuming instant loads.
- Use stable asset keys and document naming in `technical-preferences.md`.

Official skill: `docs/engine-reference/phaser/skills/loading-assets/SKILL.md`
```

`modules/input.md`:

```markdown
# Phaser Module — Input

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Use Phaser input events for pointer, keyboard, and touch where possible.
- Keep input mapping separate from gameplay rules.
- Test browser focus, canvas focus, and mobile touch behavior with Playwright
  when input is story-critical.

Official skill: `docs/engine-reference/phaser/skills/input-keyboard-mouse-touch/SKILL.md`
```

`modules/physics.md`:

```markdown
# Phaser Module — Physics

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Choose Arcade Physics for simple high-performance 2D collision.
- Choose Matter Physics only when rigid bodies, compound bodies, or advanced
  collision behavior are required.
- Keep physics constants in config modules and test pure calculations with
  Vitest.

Official skills:
- `docs/engine-reference/phaser/skills/physics-arcade/SKILL.md`
- `docs/engine-reference/phaser/skills/physics-matter/SKILL.md`
```

`modules/rendering.md`:

```markdown
# Phaser Module — Rendering

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Verify renderer, filter, post-fx, shader, and render texture examples against
  Phaser 4 docs before use.
- Use texture atlases and pixel-art scale settings deliberately.
- Use Playwright screenshots for visual smoke evidence.

Official skills:
- `docs/engine-reference/phaser/skills/filters-and-postfx/SKILL.md`
- `docs/engine-reference/phaser/skills/render-textures/SKILL.md`
- `docs/engine-reference/phaser/skills/graphics-and-shapes/SKILL.md`
```

`modules/animation.md`:

```markdown
# Phaser Module — Animation

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Define reusable animation keys in scene setup or a dedicated animation module.
- Keep animation state decisions separate from sprite creation.
- Avoid recreating animations every scene restart; guard animation registration
  when scenes can be relaunched.

Official skill: `docs/engine-reference/phaser/skills/animations/SKILL.md`
```

`modules/audio.md`:

```markdown
# Phaser Module — Audio

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Load audio in preload scenes and use stable keys for music and SFX.
- Keep volume, mute, and music state in a project-owned settings module.
- Test browser autoplay restrictions on target browsers before relying on audio
  at boot.

Official skill: `docs/engine-reference/phaser/skills/audio-and-sound/SKILL.md`
```

`modules/ui-text.md`:

```markdown
# Phaser Module — UI and Text

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Use Phaser text or bitmap text for canvas-native HUD elements.
- Use DOM overlay only when browser-native input, forms, or accessibility
  behavior is required.
- Test responsive scale, browser focus, and text legibility with Playwright for
  UI-heavy stories.

Official skill: `docs/engine-reference/phaser/skills/text-and-bitmaptext/SKILL.md`
```

`modules/tilemaps.md`:

```markdown
# Phaser Module — Tilemaps

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Keep tilemap JSON, tileset images, and map keys named consistently.
- Validate collision layers during scene create before enabling gameplay.
- Treat large maps as performance-sensitive; profile draw calls and collision
  body counts in target browsers.

Official skill: `docs/engine-reference/phaser/skills/tilemaps/SKILL.md`
```

`modules/particles.md`:

```markdown
# Phaser Module — Particles

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Pool or reuse particle emitters for frequent effects.
- Keep particle counts and lifetimes within browser performance budgets.
- Verify particle-heavy scenes with screenshot evidence and browser profiler
  notes.

Official skill: `docs/engine-reference/phaser/skills/particles/SKILL.md`
```

`modules/cameras.md`:

```markdown
# Phaser Module — Cameras

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Use cameras for viewport, follow, shake, fade, and split-view behavior.
- Keep camera effects readable and avoid stacking effects without a clear owner.
- Test camera bounds and scale behavior across target aspect ratios.

Official skill: `docs/engine-reference/phaser/skills/cameras/SKILL.md`
```

- [ ] **Step 4: Update `docs/engine-reference/README.md`**

Add Phaser to the engine directory example and mention that official Phaser AI
skills are vendored under `docs/engine-reference/phaser/skills/`.

- [ ] **Step 5: Run reference checks**

Run:

```bash
rg -n "Last verified: 2026-04-26" docs/engine-reference/phaser
rg -n "docs/engine-reference/phaser/skills" docs/engine-reference/phaser
/tmp/phaser-support-checks.sh
```

Expected: first two commands find the new docs. Acceptance script still FAILS until agents and routing are added.

- [ ] **Step 6: Commit**

Run:

```bash
git add docs/engine-reference/README.md docs/engine-reference/phaser
git commit -m "docs(phaser): add versioned reference"
```

---

### Task 4: Add Phaser Role Definitions

**Files:**
- Create: `agents/engine/phaser-*.md`
- Create: `.claude/agents/phaser-*.md`
- Modify: `docs/project/agent-roster.md`
- Modify: `.claude/docs/agent-roster.md`

- [ ] **Step 1: Create neutral Phaser roles**

Create `agents/engine/phaser-specialist.md`:

```markdown
# `phaser-specialist`

- Group: `engine`
- Reasoning tier: `Balanced`
- Use when: Phaser architecture, scene lifecycle, plugin choices, browser deployment, or Phaser-specific workflow guidance is needed
- Source: `.claude/agents/phaser-specialist.md`

## Mission

Guide Phaser-specific implementation so the project uses Phaser 4, browser
runtime constraints, and TypeScript boundaries coherently.

## Core Responsibilities

- Advise on scene lifecycle, loader usage, scale config, browser deployment, and
  Phaser plugin choices.
- Review Phaser-specific architecture and subsystem decisions.
- Route TypeScript, rendering, physics, and UI work to the right Phaser
  specialist.
- Require `docs/engine-reference/phaser/VERSION.md` and relevant module docs
  before suggesting Phaser API code.

## Typical Inputs

ADRs, Phaser config, scene structure, browser test evidence, asset loading
requirements, performance reports.

## Expected Outputs

Phaser guidance, architecture notes, subsystem recommendations, and routing
decisions.

## Collaborates With

- Reports to: `technical-director` via `lead-programmer`
- Delegates to: `phaser-typescript-specialist`, `phaser-rendering-specialist`, `phaser-physics-specialist`, `phaser-ui-specialist`
- Coordinates with: `gameplay-programmer`, `ui-programmer`, `technical-artist`, `performance-analyst`, `devops-engineer`

## Boundaries

- Does not decide mechanics or production priority.
- Escalates major browser platform, dependency, and deployment strategy changes
  to `technical-director`.
```

Create `agents/engine/phaser-typescript-specialist.md`:

```markdown
# `phaser-typescript-specialist`

- Group: `engine`
- Reasoning tier: `Balanced`
- Use when: Phaser TypeScript scene code, module boundaries, typing, or Vitest-friendly game logic needs guidance
- Source: `.claude/agents/phaser-typescript-specialist.md`

## Mission

Keep Phaser TypeScript and JavaScript code modular, typed, and testable without
requiring a browser canvas for pure game logic.

## Core Responsibilities

- Review Phaser scene classes, TypeScript modules, state boundaries, and test
  seams.
- Move formulas, state machines, and data validation into plain modules where
  Vitest can run them.
- Verify Phaser 4 code against `docs/engine-reference/phaser/`.

## Collaborates With

- Reports to: `phaser-specialist`
- Coordinates with: `gameplay-programmer`, `ui-programmer`, `qa-tester`

## Boundaries

- Does not own rendering effects, physics tuning, or UI accessibility decisions.
```

Create `agents/engine/phaser-rendering-specialist.md`:

```markdown
# `phaser-rendering-specialist`

- Group: `engine`
- Reasoning tier: `Balanced`
- Use when: Phaser WebGL, filters, post-fx, shaders, cameras, particles, atlases, or pixel-art rendering needs guidance
- Source: `.claude/agents/phaser-rendering-specialist.md`

## Mission

Guide Phaser rendering work so visual systems are compatible with Phaser 4 and
perform well in target browsers.

## Core Responsibilities

- Review WebGL, filters, post-fx, shaders, render textures, particles, cameras,
  texture atlases, and pixel-art settings.
- Require screenshot evidence for visual smoke checks.
- Verify rendering APIs against `docs/engine-reference/phaser/modules/rendering.md`.

## Collaborates With

- Reports to: `phaser-specialist`
- Coordinates with: `technical-artist`, `performance-analyst`, `art-director`

## Boundaries

- Does not own TypeScript architecture, physics behavior, or production priority.
```

Create `agents/engine/phaser-physics-specialist.md`:

```markdown
# `phaser-physics-specialist`

- Group: `engine`
- Reasoning tier: `Balanced`
- Use when: Phaser Arcade Physics, Matter Physics, collisions, body lifecycle, or physics performance needs guidance
- Source: `.claude/agents/phaser-physics-specialist.md`

## Mission

Choose and guide Phaser physics patterns that fit the game rules without adding
unneeded browser performance cost.

## Core Responsibilities

- Choose Arcade Physics for simple 2D collision and Matter Physics for advanced
  rigid-body behavior.
- Review collision categories, body setup, overlap/collide callbacks, and
  deterministic test boundaries.
- Verify physics APIs against `docs/engine-reference/phaser/modules/physics.md`.

## Collaborates With

- Reports to: `phaser-specialist`
- Coordinates with: `gameplay-programmer`, `systems-designer`, `performance-analyst`

## Boundaries

- Does not own rendering effects, UI flows, or game balance decisions.
```

Create `agents/engine/phaser-ui-specialist.md`:

```markdown
# `phaser-ui-specialist`

- Group: `engine`
- Reasoning tier: `Balanced`
- Use when: Phaser text, bitmap text, DOM overlay, responsive UI, browser focus, or input accessibility needs guidance
- Source: `.claude/agents/phaser-ui-specialist.md`

## Mission

Guide Phaser UI implementation so HUDs, menus, text, DOM overlays, and browser
input focus behave predictably across target viewports.

## Core Responsibilities

- Review Phaser text, bitmap text, DOM overlay, scale manager behavior, and input
  focus.
- Route broader accessibility requirements to `accessibility-specialist`.
- Verify UI APIs against `docs/engine-reference/phaser/modules/ui-text.md`.

## Collaborates With

- Reports to: `phaser-specialist`
- Coordinates with: `ui-programmer`, `ux-designer`, `accessibility-specialist`

## Boundaries

- Does not own rendering shaders, physics systems, or product UX direction.
```

- [ ] **Step 2: Create Claude Phaser primary agent**

Create `.claude/agents/phaser-specialist.md`:

```markdown
---
name: phaser-specialist
description: "The Phaser Engine Specialist owns Phaser 4 architecture, scene lifecycle, loader patterns, browser runtime constraints, and Phaser-specific optimization. They route TypeScript, rendering, physics, and UI work to Phaser sub-specialists."
tools: Read, Glob, Grep, Write, Edit, Bash, Task
model: sonnet
maxTurns: 20
---
You are the Phaser Engine Specialist for a game project built in Phaser 4. You are the team's authority on Phaser architecture and browser runtime constraints.

## Collaboration Protocol

Follow the shared collaboration and user-granted autonomy rules in `CLAUDE.md`.

## Core Responsibilities

- Guide Phaser scene lifecycle, loader, scale manager, plugin, and browser deployment decisions.
- Review Phaser-specific code for v4 compatibility and browser performance.
- Keep Phaser scene classes focused and move pure game rules into TypeScript modules that Vitest can test.
- Configure project defaults around TypeScript, npm scripts, Vite-style bundling, Vitest, and Playwright.
- Route subsystem work to Phaser specialists.

## Phaser Best Practices to Enforce

- Use TypeScript for new projects unless the project explicitly chooses JavaScript.
- Load assets in `preload()` or a dedicated preload scene.
- Keep `update()` small; prefer events for input, timers, and lifecycle behavior.
- Use texture atlases for sprite-heavy games.
- Use Arcade Physics for simple high-performance 2D collision and Matter Physics only when advanced rigid body behavior is needed.
- Use Playwright screenshots for browser/canvas smoke evidence.
- Avoid Phaser 3 snippets unless checked against Phaser 4 docs or vendored migration skills.

## Delegation Map

**Reports to**: `technical-director` via `lead-programmer`

**Delegates to**:
- `phaser-typescript-specialist` for TypeScript scene code, module boundaries, and Vitest-friendly logic
- `phaser-rendering-specialist` for WebGL, filters, post-fx, shaders, particles, cameras, and atlases
- `phaser-physics-specialist` for Arcade Physics, Matter Physics, collisions, and physics performance
- `phaser-ui-specialist` for Phaser text, bitmap text, DOM overlay, responsive UI, and browser input focus

**Coordinates with**:
- `gameplay-programmer` for gameplay systems
- `ui-programmer` for interface implementation
- `technical-artist` for visual effects and shader constraints
- `performance-analyst` for browser profiling
- `devops-engineer` for npm scripts, CI, hosting, and deployment

## Version Awareness

Before suggesting Phaser API code:

1. Read `docs/engine-reference/phaser/VERSION.md`.
2. Check `docs/engine-reference/phaser/deprecated-apis.md`.
3. Check `docs/engine-reference/phaser/breaking-changes.md`.
4. Read the relevant `docs/engine-reference/phaser/modules/*.md`.
5. Use the official skills under `docs/engine-reference/phaser/skills/` for subsystem guidance.
6. If an API is not covered there, verify against https://docs.phaser.io/api-documentation/api-documentation.

## When Consulted

Always involve this agent when adding Phaser scenes, configuring Phaser projects,
choosing Phaser physics systems, changing loader/asset strategy, setting browser
test strategy, or reviewing Phaser-specific performance.
```

- [ ] **Step 3: Create Claude Phaser sub-specialists**

Create the four `.claude/agents/phaser-*-specialist.md` files with frontmatter matching `phaser-specialist`, each with `tools: Read, Glob, Grep, Write, Edit, Bash, Task`, `model: sonnet`, and `maxTurns: 20`. Each file must include:

- `Collaboration Protocol` pointing to `CLAUDE.md`
- `Core Responsibilities`
- `Best Practices`
- `Version Awareness` pointing to `docs/engine-reference/phaser/`
- `What This Agent Must NOT Do`

Use these routing boundaries:

- TypeScript specialist handles `.ts`, `.tsx`, `.js`, scene classes, state modules, and Vitest helpers.
- Rendering specialist handles shaders, filters, post-fx, cameras, particles, atlases, render textures, pixel-art settings.
- Physics specialist handles Arcade Physics, Matter Physics, collisions, body setup, and physics profiling.
- UI specialist handles Phaser text, bitmap text, DOM overlay, responsive layout, input focus, and accessibility handoff.

- [ ] **Step 4: Update rosters**

Add Phaser rows to `docs/project/agent-roster.md` under Engine Specialists and `.claude/docs/agent-roster.md` under Engine-Specific Agents.

Use these rows in neutral roster:

```markdown
| `phaser-specialist` | Phaser | Balanced | `agents/engine/phaser-specialist.md` | Phaser architecture, scene lifecycle, loader, browser deployment |
| `phaser-typescript-specialist` | Phaser | Balanced | `agents/engine/phaser-typescript-specialist.md` | TypeScript scene code, module boundaries, Vitest-friendly logic |
| `phaser-rendering-specialist` | Phaser | Balanced | `agents/engine/phaser-rendering-specialist.md` | WebGL, filters, post-fx, shaders, particles, cameras, atlases |
| `phaser-physics-specialist` | Phaser | Balanced | `agents/engine/phaser-physics-specialist.md` | Arcade Physics, Matter Physics, collisions, physics performance |
| `phaser-ui-specialist` | Phaser | Balanced | `agents/engine/phaser-ui-specialist.md` | Phaser text, bitmap text, DOM overlay, responsive UI, browser focus |
```

- [ ] **Step 5: Run role checks**

Run:

```bash
rg -n "phaser-specialist|phaser-typescript-specialist|phaser-rendering-specialist|phaser-physics-specialist|phaser-ui-specialist" agents/engine .claude/agents docs/project/agent-roster.md .claude/docs/agent-roster.md
/tmp/phaser-support-checks.sh
```

Expected: role names found. Acceptance script still FAILS until public docs, skills, and fixtures are updated.

- [ ] **Step 6: Commit**

Run:

```bash
git add agents/engine/phaser-*.md .claude/agents/phaser-*.md docs/project/agent-roster.md .claude/docs/agent-roster.md
git commit -m "docs(phaser): add engine agents"
```

---

### Task 5: Update Public Engine Documentation

**Files:**
- Modify: `README.md`
- Modify: `CLAUDE.md`
- Modify: `docs/WORKFLOW-GUIDE.md`
- Modify: `docs/project/technical-preferences.md`
- Modify: `.gitignore`

- [ ] **Step 1: Update README engine tables and examples**

Change the Engine Specialists table to include:

```markdown
| **Phaser 4** | `phaser-specialist` | TypeScript, Rendering, Physics, UI |
```

Update any sentence saying "all three major engines" to "Godot, Unity, Unreal, and Phaser".

Update customization text from:

```markdown
- **Pick your engine** — use the Godot, Unity, or Unreal agent set (or none)
```

to:

```markdown
- **Pick your engine** — use the Godot, Unity, Unreal, or Phaser agent set (or none)
```

Add a setup example:

```markdown
- `/setup-engine phaser 4.0.0` — configure Phaser for a web-first TypeScript project
```

- [ ] **Step 2: Update `CLAUDE.md` stack choices**

Change:

```markdown
- **Engine**: [CHOOSE: Godot 4 / Unity / Unreal Engine 5]
- **Language**: [CHOOSE: GDScript / C# / C++ / Blueprint]
```

to:

```markdown
- **Engine**: [CHOOSE: Godot 4 / Unity / Unreal Engine 5 / Phaser 4]
- **Language**: [CHOOSE: GDScript / C# / C++ / Blueprint / TypeScript / JavaScript]
```

Update the note to say Phaser has dedicated TypeScript, rendering, physics, and UI sub-specialists.

- [ ] **Step 3: Update workflow guide**

In `docs/WORKFLOW-GUIDE.md`, add Phaser wherever engine specialists or setup choices list Godot, Unity, and Unreal. Add a Phaser row with:

```markdown
| Phaser 4 | `phaser-specialist` | TypeScript, Rendering, Physics, UI |
```

- [ ] **Step 4: Update technical preference examples**

In `docs/project/technical-preferences.md`, update example comments so Phaser is a valid engine and web target. Add a file-routing example row for Phaser only if an example list exists; keep existing bracketed unconfigured markers unchanged when the file is intentionally unconfigured.

- [ ] **Step 5: Update `.gitignore`**

If generic Node ignores already cover `node_modules/`, `dist/`, `coverage/`, and Playwright output, add a short comment grouping web/Phaser build artifacts without duplicating entries. If any are missing, add:

```gitignore
# Phaser / web build outputs
node_modules/
dist/
coverage/
playwright-report/
test-results/
```

- [ ] **Step 6: Run doc checks**

Run:

```bash
rg -n "Phaser" README.md CLAUDE.md docs/WORKFLOW-GUIDE.md docs/project/technical-preferences.md .gitignore
/tmp/phaser-support-checks.sh
```

Expected: public docs contain Phaser. Acceptance script still FAILS until setup/test skills and fixtures are updated.

- [ ] **Step 7: Commit**

Run:

```bash
git add README.md CLAUDE.md docs/WORKFLOW-GUIDE.md docs/project/technical-preferences.md .gitignore
git commit -m "docs(phaser): expose engine option"
```

---

### Task 6: Update Engine Selection and Brainstorm Skills

**Files:**
- Modify: `.claude/skills/setup-engine/SKILL.md`
- Modify: `.agents/skills/setup-engine/SKILL.md`
- Modify: `.claude/skills/brainstorm/SKILL.md`
- Modify: `.agents/skills/brainstorm/SKILL.md`

- [ ] **Step 1: Add Phaser setup-engine guided option**

In both setup-engine files, update prior-experience options to:

```markdown
- Options: `Godot` / `Unity` / `Unreal Engine 5` / `Phaser 4` / `Multiple — I'll explain` / `None of them`
```

Add web platform rule:

```markdown
- Web → Phaser strongly preferred for web-first 2D/browser games; Godot exports cleanly to web; Unity WebGL is functional; Unreal has poor web support
```

- [ ] **Step 2: Add Phaser honest tradeoffs**

Add after Godot or before Unity:

```markdown
**Phaser 4**
- Genuine strengths: web-first 2D, TypeScript-friendly development, tiny iteration loop, strong browser deployment story, excellent fit for arcade, puzzle, card, UI-heavy, and playable prototype games
- Real limitations: not a full editor-centric engine; 3D is not the target; native console/mobile workflows require wrappers or additional platform tooling; browser performance and input quirks must be tested on target devices
- Licensing reality: Free open-source framework under MIT-style terms; project dependencies and hosting choices may add separate obligations
- Best fit: browser-first 2D games; web demos; jam games; educational games; arcade/action/puzzle/card games; projects where TypeScript and web deployment are advantages
```

Add genre guidance:

```markdown
- Browser-first 2D / web arcade / card / puzzle / educational → Phaser strongly preferred
- Web prototype for a mechanic → Phaser or Godot; Phaser if browser deployment is the point
```

- [ ] **Step 3: Add Phaser stack template**

Add:

```markdown
**For Phaser:**
```markdown
- **Engine**: Phaser [version]
- **Language**: TypeScript (primary), JavaScript (supported)
- **Build System**: npm scripts with Vite-style browser bundling
- **Asset Pipeline**: Phaser Loader + texture atlases + web-optimized static assets
```
```

- [ ] **Step 4: Add Phaser technical preferences and routing**

Add naming defaults:

```markdown
**For Phaser (TypeScript):**
- Classes: PascalCase (e.g., `GameplayScene`)
- Variables/functions: camelCase (e.g., `playerSpeed`, `spawnEnemy()`)
- Private fields: camelCase with clear names; `#privateField` only when runtime private semantics are needed
- Files: kebab-case for modules (e.g., `gameplay-scene.ts`, `damage-system.ts`)
- Constants: UPPER_SNAKE_CASE for global constants, PascalCase for exported config objects
```

Add engine specialists block:

```markdown
## Engine Specialists
- **Primary**: phaser-specialist
- **Language/Code Specialist**: phaser-typescript-specialist (TypeScript/JavaScript scene code, game logic modules, Vitest-friendly boundaries)
- **Shader Specialist**: phaser-rendering-specialist (WebGL, filters, post-fx, shaders, particles, cameras, atlases)
- **UI Specialist**: phaser-ui-specialist (Phaser text, bitmap text, DOM overlay, responsive UI, browser focus)
- **Additional Specialists**: phaser-physics-specialist (Arcade Physics, Matter Physics, collision systems)
- **Routing Notes**: Invoke primary for architecture and browser deployment decisions. Invoke TypeScript specialist for scene code and game logic modules. Invoke rendering specialist for visual effects, shaders, cameras, and atlas strategy. Invoke physics specialist for Arcade or Matter Physics. Invoke UI specialist for UI and input focus.

### File Extension Routing

| File Extension / Type | Specialist to Spawn |
|-----------------------|---------------------|
| Game code (.ts, .tsx, .js files) | phaser-typescript-specialist |
| Shader / rendering files (filters, post-fx, GLSL strings, atlas config) | phaser-rendering-specialist |
| UI / screen files (HUD scenes, text, bitmap text, DOM overlay) | phaser-ui-specialist |
| Scene / level files (Phaser.Scene classes, tilemap JSON) | phaser-specialist |
| Physics systems (Arcade, Matter, collision config) | phaser-physics-specialist |
| General architecture review | phaser-specialist |
```

- [ ] **Step 5: Add Phaser knowledge baseline**

Add under knowledge coverage:

```markdown
- Phaser: training data likely covers Phaser 3.x; Phaser 4.0.0 is post-cutoff and HIGH RISK
```

- [ ] **Step 6: Update brainstorm engine recommendation text**

In both brainstorm skills, add Phaser to any target-platform and engine-experience option sets. Add guidance:

```markdown
For browser-first 2D concepts, consider Phaser 4 as the primary recommendation when the user's goals emphasize web distribution, TypeScript, fast iteration, small scope, or playable prototypes.
```

- [ ] **Step 7: Run mirror checks**

Run:

```bash
rg -n "Phaser 4|phaser-specialist|phaser-typescript-specialist|Vitest|Vite" .claude/skills/setup-engine/SKILL.md .agents/skills/setup-engine/SKILL.md
rg -n "Phaser" .claude/skills/brainstorm/SKILL.md .agents/skills/brainstorm/SKILL.md
/tmp/phaser-support-checks.sh
```

Expected: setup and brainstorm checks pass. Acceptance script still FAILS until test skills and fixtures are updated.

- [ ] **Step 8: Commit**

Run:

```bash
git add .claude/skills/setup-engine/SKILL.md .agents/skills/setup-engine/SKILL.md .claude/skills/brainstorm/SKILL.md .agents/skills/brainstorm/SKILL.md
git commit -m "docs(phaser): update engine setup skills"
```

---

### Task 7: Update Test Setup, Test Helpers, and Smoke Check Skills

**Files:**
- Modify: `.claude/skills/test-setup/SKILL.md`
- Modify: `.agents/skills/test-setup/SKILL.md`
- Modify: `.claude/skills/test-helpers/SKILL.md`
- Modify: `.agents/skills/test-helpers/SKILL.md`
- Modify: `.claude/skills/smoke-check/SKILL.md`
- Modify: `.agents/skills/smoke-check/SKILL.md`

- [ ] **Step 1: Add Phaser test detection**

In both `test-setup` files, extend engine-specific artifact detection:

```markdown
- Glob `tests/gdunit4_runner.gd` (Godot) or `tests/EditMode/` (Unity) or
  `Source/Tests/` (Unreal) or `tests/phaser/` and `playwright.config.*`
  (Phaser) for engine-specific artifacts.
```

Update framework list to:

```markdown
**Test Framework**: [GdUnit4 | Unity Test Framework | UE Automation | Vitest + Playwright]
```

- [ ] **Step 2: Add Phaser test scaffold section**

Add to both `test-setup` files:

```markdown
#### Phaser 4 (`Engine: Phaser`)

Create `tests/phaser/README.md`:
```markdown
# Phaser Browser Tests

Browser and canvas integration tests use Playwright.
Use these for scene boot, canvas rendering, input focus, scaling, and smoke checks.
Run with: `npm run test:e2e`
```

Create `tests/unit/README.md`:
```markdown
# Phaser Unit Tests

Pure TypeScript game rules use Vitest.
Keep Phaser.Scene lifecycle tests in `tests/phaser/`; keep formulas, state
machines, and data validation here.
Run with: `npm run test:unit`
```

Create `tests/phaser/game-boot.spec.ts`:
```typescript
import { test, expect } from '@playwright/test';

test('game boots and renders a non-empty canvas', async ({ page }) => {
  await page.goto('/');
  const canvas = page.locator('canvas').first();
  await expect(canvas).toBeVisible();
  const box = await canvas.boundingBox();
  expect(box?.width).toBeGreaterThan(0);
  expect(box?.height).toBeGreaterThan(0);
});
```

Note in the README: **Installing Phaser test dependencies**
```bash
npm install --save-dev vitest playwright @playwright/test
npx playwright install --with-deps chromium
```
```

- [ ] **Step 3: Add Phaser CI workflow**

In both `test-setup` files, add a Phaser CI section:

```yaml
name: Automated Tests

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    name: Run Phaser Tests
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 22
          cache: npm

      - name: Install dependencies
        run: npm ci

      - name: Install Playwright
        run: npx playwright install --with-deps chromium

      - name: Run unit tests
        run: npm run test:unit

      - name: Run browser tests
        run: npm run test:e2e
```

- [ ] **Step 4: Update test helper skills**

In both `test-helpers` files, add Phaser guidance:

```markdown
### Phaser 4 Helpers

Create helpers that separate pure TypeScript tests from browser scene tests:

- `tests/helpers/create-test-game.ts` creates a minimal Phaser game config for
  browser tests.
- `tests/helpers/scene-ready.ts` waits for a scene `create()` signal before
  assertions.
- Pure gameplay formulas stay in `tests/unit/` and run with Vitest without
  creating a Phaser.Game instance.
```

Include this helper snippet:

```typescript
import Phaser from 'phaser';

export function createTestGame(scene: Phaser.Types.Scenes.SceneType): Phaser.Game {
  return new Phaser.Game({
    type: Phaser.HEADLESS,
    width: 320,
    height: 180,
    scene,
    physics: { default: 'arcade' }
  });
}
```

- [ ] **Step 5: Update smoke-check command selection**

In both `smoke-check` files, add:

```markdown
**Phaser 4:**
```bash
npm run test:unit -- --run 2>&1
npm run test:e2e 2>&1
```
If `package.json` is missing or scripts are not defined, note: "Phaser npm test
scripts not found. Expected `test:unit` for Vitest and `test:e2e` for
Playwright. Confirm browser smoke results manually or run `/test-setup`."
```

Add Phaser-specific manual smoke prompts for browser target:

```markdown
- "Canvas is visible and non-empty in target browser — PASS"
- "Canvas is blank, hidden, or incorrectly sized — FAIL"
- "Keyboard/pointer/touch focus works after clicking canvas — PASS"
- "Browser focus or input routing fails — FAIL"
```

- [ ] **Step 6: Run test skill checks**

Run:

```bash
rg -n "Vitest|Playwright|tests/phaser|game-boot.spec.ts" .claude/skills/test-setup/SKILL.md .agents/skills/test-setup/SKILL.md
rg -n "createTestGame|Phaser 4 Helpers" .claude/skills/test-helpers/SKILL.md .agents/skills/test-helpers/SKILL.md
rg -n "npm run test:unit|npm run test:e2e|Canvas is visible" .claude/skills/smoke-check/SKILL.md .agents/skills/smoke-check/SKILL.md
/tmp/phaser-support-checks.sh
```

Expected: test skill checks pass. Acceptance script still FAILS until CCGS fixtures are updated.

- [ ] **Step 7: Commit**

Run:

```bash
git add .claude/skills/test-setup/SKILL.md .agents/skills/test-setup/SKILL.md .claude/skills/test-helpers/SKILL.md .agents/skills/test-helpers/SKILL.md .claude/skills/smoke-check/SKILL.md .agents/skills/smoke-check/SKILL.md
git commit -m "docs(phaser): add web test workflows"
```

---

### Task 8: Update CCGS Skill Testing Framework

**Files:**
- Create: `CCGS Skill Testing Framework/agents/engine/phaser/*.md`
- Modify: `CCGS Skill Testing Framework/catalog.yaml`
- Modify: `CCGS Skill Testing Framework/quality-rubric.md`
- Modify: `CCGS Skill Testing Framework/README.md`
- Modify: `CCGS Skill Testing Framework/CLAUDE.md`
- Modify: `CCGS Skill Testing Framework/templates/agent-test-spec.md`
- Modify: `CCGS Skill Testing Framework/skills/utility/setup-engine.md`
- Modify: `CCGS Skill Testing Framework/skills/utility/start.md`
- Modify: `CCGS Skill Testing Framework/skills/utility/test-setup.md`

- [ ] **Step 1: Add Phaser fixture specs**

Create `CCGS Skill Testing Framework/agents/engine/phaser/phaser-specialist.md`:

```markdown
# Agent Test Spec: phaser-specialist

## Domain

Owns Phaser 4 architecture, scene lifecycle, loader, scale manager, browser
runtime constraints, and routing to Phaser sub-specialists.

## Required Behaviors

- Reads `docs/engine-reference/phaser/VERSION.md` before Phaser API guidance.
- Routes TypeScript code to `phaser-typescript-specialist`.
- Routes rendering, filters, post-fx, particles, cameras, and atlases to
  `phaser-rendering-specialist`.
- Routes Arcade and Matter Physics to `phaser-physics-specialist`.
- Routes Phaser text, bitmap text, DOM overlay, and responsive UI to
  `phaser-ui-specialist`.
- Flags Phaser 3 examples as risky until checked against Phaser 4 docs.

## Test Cases

### Case 1: Version context
**Input:** "Build a Phaser scene loader for this project."
**Expected:** References Phaser 4.0.0 docs and loader lifecycle before proposing code.

### Case 2: Rendering routing
**Input:** "Add a custom post-fx shader to the game."
**Expected:** Routes to `phaser-rendering-specialist`.

### Case 3: Browser testing
**Input:** "How do we prove the game renders in CI?"
**Expected:** Recommends Playwright canvas visibility/non-empty checks.
```

Create the four sub-specialist fixture specs with the same sections and domain-specific cases:

- TypeScript: rejects untyped global script architecture for new projects; recommends TypeScript modules and Vitest for pure logic.
- Rendering: checks filters/post-fx against Phaser 4 docs; requires screenshot evidence for visual changes.
- Physics: chooses Arcade vs Matter based on collision needs; warns against advanced Matter usage for simple overlap games.
- UI: handles text/bitmap text/DOM overlay routing; flags browser focus and responsive scale tests.

- [ ] **Step 2: Update catalog**

Add entries under engine specialists:

```yaml
  # Engine Specialists — Phaser
  - name: phaser-specialist
    spec: CCGS Skill Testing Framework/agents/engine/phaser/phaser-specialist.md
    last_spec: ""
    last_spec_result: ""
    category: engine

  - name: phaser-typescript-specialist
    spec: CCGS Skill Testing Framework/agents/engine/phaser/phaser-typescript-specialist.md
    last_spec: ""
    last_spec_result: ""
    category: engine

  - name: phaser-rendering-specialist
    spec: CCGS Skill Testing Framework/agents/engine/phaser/phaser-rendering-specialist.md
    last_spec: ""
    last_spec_result: ""
    category: engine

  - name: phaser-physics-specialist
    spec: CCGS Skill Testing Framework/agents/engine/phaser/phaser-physics-specialist.md
    last_spec: ""
    last_spec_result: ""
    category: engine

  - name: phaser-ui-specialist
    spec: CCGS Skill Testing Framework/agents/engine/phaser/phaser-ui-specialist.md
    last_spec: ""
    last_spec_result: ""
    category: engine
```

- [ ] **Step 3: Update rubric and framework docs**

In `quality-rubric.md`, append all Phaser agents to the `engine` agent list and update E2 example to include `.ts` or Phaser post-fx routing.

In `README.md` and `CLAUDE.md`, add a `phaser` row:

```markdown
| `phaser` | phaser-specialist, phaser-typescript-specialist, phaser-rendering-specialist, phaser-physics-specialist, phaser-ui-specialist |
```

In `templates/agent-test-spec.md`, update tier/category examples from `godot | unity | unreal` to `godot | unity | unreal | phaser`.

- [ ] **Step 4: Update utility fixture expectations**

In `skills/utility/setup-engine.md`, add Phaser setup cases that expect:

- guided engine options include Phaser
- web/browser platform can recommend Phaser
- technical preferences route `.ts` to `phaser-typescript-specialist`
- testing defaults are Vitest and Playwright

In `skills/utility/start.md`, replace fixtures that assert exactly three engine options with fixtures that assert four options: Godot, Unity, Unreal, Phaser.

In `skills/utility/test-setup.md`, add Phaser expectations for `tests/phaser/`, `tests/unit/`, Vitest, Playwright, and npm CI.

- [ ] **Step 5: Run framework checks**

Run:

```bash
rg -n "phaser-specialist|phaser-typescript-specialist|phaser-rendering-specialist|phaser-physics-specialist|phaser-ui-specialist" "CCGS Skill Testing Framework"
rg -n "Godot, Unity, Unreal, Phaser|Godot.*Unity.*Unreal.*Phaser|exactly four engine options|Vitest|Playwright" "CCGS Skill Testing Framework/skills/utility"
/tmp/phaser-support-checks.sh
```

Expected: Phaser framework references found. Acceptance script prints `Phaser support acceptance checks passed`.

- [ ] **Step 6: Commit**

Run:

```bash
git add "CCGS Skill Testing Framework/agents/engine/phaser" "CCGS Skill Testing Framework/catalog.yaml" "CCGS Skill Testing Framework/quality-rubric.md" "CCGS Skill Testing Framework/README.md" "CCGS Skill Testing Framework/CLAUDE.md" "CCGS Skill Testing Framework/templates/agent-test-spec.md" "CCGS Skill Testing Framework/skills/utility/setup-engine.md" "CCGS Skill Testing Framework/skills/utility/start.md" "CCGS Skill Testing Framework/skills/utility/test-setup.md"
git commit -m "test(phaser): add engine fixtures"
```

---

### Task 9: Final Cross-Repository Verification

**Files:**
- Modify only if verification finds missed Phaser surfaces.

- [ ] **Step 1: Search for engine lists missing Phaser**

Run:

```bash
rg -n "Godot.*Unity.*Unreal|godot.*unity.*unreal|Unity.*Unreal.*Godot|all three major engines|exactly 3|exactly three" README.md CLAUDE.md AGENTS.md docs .claude agents "CCGS Skill Testing Framework" .agents
```

Expected: every engine-option list found either includes Phaser or is a historical example that does not describe supported engine choices. Fix any supported-engine list that omits Phaser.

- [ ] **Step 2: Confirm Phaser appears in required surfaces**

Run:

```bash
rg -n "Phaser|phaser" README.md CLAUDE.md docs .claude agents "CCGS Skill Testing Framework" .agents | wc -l
/tmp/phaser-support-checks.sh
```

Expected: count is greater than `60`; acceptance script prints `Phaser support acceptance checks passed`.

- [ ] **Step 3: Validate YAML shape**

Run:

```bash
ruby -e 'require "yaml"; YAML.load_file("CCGS Skill Testing Framework/catalog.yaml"); YAML.load_file("docs/project/workflow-catalog.yaml"); puts "yaml ok"'
```

Expected: prints `yaml ok`.

- [ ] **Step 4: Validate no top-level Phaser skills were added**

Run:

```bash
find .claude/skills .agents/skills -maxdepth 1 -iname '*phaser*' -print
```

Expected: no output.

- [ ] **Step 5: Check diff hygiene**

Run:

```bash
git diff --check
git status --short --branch
```

Expected: `git diff --check` exits `0`. Status shows only intended modified/added files and no accidental staging of the entire `.agents/` directory.

- [ ] **Step 6: Final commit if needed**

If verification fixes were made, run:

```bash
git add README.md CLAUDE.md AGENTS.md docs .claude agents "CCGS Skill Testing Framework"
git commit -m "docs(phaser): complete engine integration"
```

If no verification fixes were made, skip this commit.

---

## Self-Review Checklist

- Spec goal maps to Tasks 2 through 9.
- Official Phaser skills stay only under `docs/engine-reference/phaser/skills/`.
- Phaser agents exist in neutral, Claude adapter, and CCGS fixture surfaces.
- Engine setup, brainstorm, test setup, test helpers, and smoke check are updated in both `.claude/skills/` and `.agents/skills/`.
- CCGS framework no longer assumes only Godot, Unity, and Unreal.
- Verification commands cover missing files, missing Phaser references, YAML parseability, top-level skill leakage, and whitespace errors.
