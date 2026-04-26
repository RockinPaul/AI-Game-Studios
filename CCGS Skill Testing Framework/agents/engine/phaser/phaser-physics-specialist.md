# Agent Test Spec: phaser-physics-specialist

## Agent Summary
Domain: Phaser 4 Arcade Physics and Matter Physics selection, body configuration, collision routing, overlap behavior, constraints, sensors, and deterministic physics test guidance.
Does NOT own: TypeScript project structure (phaser-typescript-specialist), rendering/post-fx work (phaser-rendering-specialist), UI implementation (phaser-ui-specialist), or general engine routing (phaser-specialist).
Model tier: Sonnet (default).
No gate IDs assigned.

---

## Static Assertions (Structural)

- [ ] `description:` field is present and domain-specific (references Phaser 4 physics / Arcade Physics / Matter Physics / collisions)
- [ ] `allowed-tools:` list includes Read, Write, Edit, Bash, Glob, Grep
- [ ] Model tier is Sonnet (default for specialists)
- [ ] Agent definition references `docs/engine-reference/phaser/VERSION.md` as the authoritative Phaser physics API source
- [ ] Agent definition routes pure collision rules to unit tests and runtime physics proof to Playwright without defining top-level Phaser slash skills

---

## Test Cases

### Case 1: Arcade vs Matter
**Input:** "Our platformer only needs tile collisions, collectibles, and enemy overlap triggers."
**Expected behavior:**
- Recommends Arcade Physics for simple tile collisions, collectibles, and overlap triggers
- Warns that Matter would add unnecessary complexity for this case
- Explains the collision needs that would justify revisiting Matter later

### Case 2: Advanced simulation
**Input:** "We need chains, compound bodies, and rotating polygon collisions."
**Expected behavior:**
- Recommends Matter Physics for constraints, compound bodies, and polygon collisions
- Explains the added setup and performance trade-offs
- Checks relevant Matter APIs against Phaser 4 docs before giving implementation guidance

### Case 3: Runtime proof
**Input:** "How do we prove the player cannot pass through walls in CI?"
**Expected behavior:**
- Recommends deterministic scene setup with Playwright runtime checks
- Separates pure collision rule tests from browser physics simulation proof
- Includes enough setup guidance to make the check repeatable

### Case 4: Simple overlap warning
**Input:** "Use Matter sensors for coin pickups in a basic Arcade-style game."
**Expected behavior:**
- Warns against advanced Matter usage for simple overlap games
- Recommends Arcade overlap behavior unless requirements justify Matter
- Does NOT add Matter solely because it is more powerful

### Case 5: Visual evidence routing
**Input:** "The debug bodies look misaligned with sprites."
**Expected behavior:**
- Handles physics body configuration and collision implications
- Routes visual screenshot evidence needs to `phaser-rendering-specialist`
- Keeps TypeScript-only scene structure questions routed to `phaser-typescript-specialist`

---

## Protocol Compliance

- [ ] Stays within declared domain (Phaser 4 Arcade Physics, Matter Physics, body configuration, collisions, deterministic tests)
- [ ] Reads `docs/engine-reference/phaser/VERSION.md` before Phaser physics API guidance
- [ ] Chooses Arcade vs Matter based on collision and simulation needs
- [ ] Warns against advanced Matter usage for simple overlap or tile collision games
- [ ] Routes TypeScript-only structure questions to `phaser-typescript-specialist`
- [ ] Routes visual collision debugging evidence to `phaser-rendering-specialist` when screenshots are required
- [ ] Recommends focused unit tests for pure collision rules and Playwright checks for runtime physics behavior
- [ ] Does not create or request top-level Phaser slash skills

---

## Coverage Notes
- Arcade vs Matter cases cover both simple and advanced physics selection
- Runtime proof (Case 3) confirms browser physics behavior is verified in Playwright
- Visual routing (Case 5) checks collaboration with rendering evidence workflows
