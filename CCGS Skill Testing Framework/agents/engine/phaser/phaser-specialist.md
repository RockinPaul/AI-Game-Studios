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
