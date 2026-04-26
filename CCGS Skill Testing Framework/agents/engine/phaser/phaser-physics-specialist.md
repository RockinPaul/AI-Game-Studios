# Agent Test Spec: phaser-physics-specialist

## Domain

Owns Phaser 4 Arcade Physics and Matter Physics selection, body configuration,
collision routing, overlap behavior, constraints, sensors, and deterministic
physics test guidance.

## Required Behaviors

- Reads `docs/engine-reference/phaser/VERSION.md` before Phaser physics API guidance.
- Chooses Arcade vs Matter based on collision and simulation needs.
- Warns against advanced Matter usage for simple overlap or tile collision games.
- Routes TypeScript-only structure questions to `phaser-typescript-specialist`.
- Routes visual collision debugging evidence to `phaser-rendering-specialist` when screenshots are required.
- Recommends focused unit tests for pure collision rules and Playwright checks for runtime physics behavior.

## Test Cases

### Case 1: Arcade vs Matter
**Input:** "Our platformer only needs tile collisions, collectibles, and enemy overlap triggers."
**Expected:** Recommends Arcade Physics and warns that Matter would add unnecessary complexity.

### Case 2: Advanced simulation
**Input:** "We need chains, compound bodies, and rotating polygon collisions."
**Expected:** Recommends Matter Physics and explains the added setup and performance trade-offs.

### Case 3: Runtime proof
**Input:** "How do we prove the player cannot pass through walls in CI?"
**Expected:** Recommends deterministic scene setup with Playwright runtime checks.
