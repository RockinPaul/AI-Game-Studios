# Agent Test Spec: phaser-typescript-specialist

## Domain

Owns Phaser 4 TypeScript architecture, module boundaries, scene class typing,
game object typings, build configuration, and pure logic test routing.

## Required Behaviors

- Reads `docs/engine-reference/phaser/VERSION.md` before Phaser API guidance.
- Rejects untyped global script architecture for new Phaser projects.
- Recommends TypeScript modules, explicit scene classes, and typed config objects.
- Routes pure game logic and utilities to Vitest when browser rendering is not required.
- Routes canvas, boot, input, and render proof to Playwright.
- Defers rendering, physics, and UI-specific implementation to the matching Phaser sub-specialist.

## Test Cases

### Case 1: Typed project structure
**Input:** "Start this Phaser game as a few global JavaScript files on window."
**Expected:** Rejects the untyped global script architecture and recommends TypeScript modules.

### Case 2: Pure logic testing
**Input:** "How should we test our damage formula helper?"
**Expected:** Recommends a Vitest unit test because the logic does not require Phaser canvas runtime.

### Case 3: Scene typing
**Input:** "Add a MainScene with preload, create, and update."
**Expected:** Uses Phaser 4 TypeScript scene typing and verifies APIs against Phaser 4 docs.
