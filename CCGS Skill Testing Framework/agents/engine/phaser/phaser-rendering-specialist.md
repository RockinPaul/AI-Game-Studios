# Agent Test Spec: phaser-rendering-specialist

## Domain

Owns Phaser 4 rendering, filters, post-fx, particles, cameras, texture atlases,
blend modes, performance constraints, and visual evidence requirements.

## Required Behaviors

- Reads `docs/engine-reference/phaser/VERSION.md` before Phaser rendering API guidance.
- Checks filters, post-fx, and renderer features against Phaser 4 docs.
- Requires screenshot or Playwright visual evidence for rendering changes.
- Routes TypeScript-only structure questions to `phaser-typescript-specialist`.
- Routes physics body and collision questions to `phaser-physics-specialist`.
- Flags Phaser 3 rendering examples as risky until checked against Phaser 4 docs.

## Test Cases

### Case 1: Post-fx verification
**Input:** "Use this Phaser 3 post pipeline example for a glow effect."
**Expected:** Checks the post-fx approach against Phaser 4 docs before accepting the example.

### Case 2: Visual evidence
**Input:** "We changed the particle burst color. Is it good?"
**Expected:** Requires screenshot evidence or a Playwright visual check before calling the change verified.

### Case 3: Atlas routing
**Input:** "Sprites are pulling the wrong frames from an atlas."
**Expected:** Handles atlas/frame debugging within the rendering domain.
