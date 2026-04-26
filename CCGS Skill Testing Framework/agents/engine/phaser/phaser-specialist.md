# Agent Test Spec: phaser-specialist

## Agent Summary
Domain: Phaser 4 architecture, scene lifecycle, loader, scale manager, browser runtime constraints, and routing to Phaser sub-specialists.
Does NOT own: TypeScript implementation details (phaser-typescript-specialist), rendering/post-fx work (phaser-rendering-specialist), physics setup (phaser-physics-specialist), or UI implementation (phaser-ui-specialist).
Model tier: Sonnet (default).
No gate IDs assigned.

---

## Static Assertions (Structural)

- [ ] `description:` field is present and domain-specific (references Phaser 4 architecture / scene lifecycle / browser runtime decisions)
- [ ] `allowed-tools:` list includes Read, Write, Edit, Bash, Glob, Grep
- [ ] Model tier is Sonnet (default for specialists)
- [ ] Agent definition references `docs/engine-reference/phaser/VERSION.md` as the authoritative Phaser API source
- [ ] Agent definition routes Phaser subdomains to Phaser specialists and does not define top-level Phaser slash skills

---

## Test Cases

### Case 1: Version context
**Input:** "Build a Phaser scene loader for this project."
**Expected behavior:**
- Reads or references `docs/engine-reference/phaser/VERSION.md` before Phaser API guidance
- References Phaser 4.0.0 docs and loader lifecycle before proposing code
- Flags Phaser 3 examples as risky until checked against Phaser 4 docs

### Case 2: Rendering routing
**Input:** "Add a custom post-fx shader to the game."
**Expected behavior:**
- Routes rendering, filters, post-fx, particles, cameras, and atlases to `phaser-rendering-specialist`
- Does NOT produce the shader implementation directly
- Notes that the rendering specialist must verify Phaser 4 post-fx APIs

### Case 3: Browser testing
**Input:** "How do we prove the game renders in CI?"
**Expected behavior:**
- Recommends Playwright canvas visibility/non-empty checks
- Distinguishes browser runtime proof from pure logic tests
- Routes TypeScript-only test structure to `phaser-typescript-specialist` if needed

### Case 4: Physics routing
**Input:** "Set up collision behavior for platforms and pickups."
**Expected behavior:**
- Routes Arcade and Matter Physics decisions to `phaser-physics-specialist`
- Does NOT choose a physics system without collision requirements
- Notes that the physics specialist owns runtime collision proof

### Case 5: UI routing
**Input:** "Build a responsive score HUD and name-entry overlay."
**Expected behavior:**
- Routes Phaser text, bitmap text, DOM overlay, and responsive UI to `phaser-ui-specialist`
- Flags browser focus risk for DOM overlays
- Notes that responsive scale behavior needs browser viewport checks

---

## Protocol Compliance

- [ ] Stays within declared domain (Phaser 4 architecture, scene lifecycle, browser constraints, specialist routing)
- [ ] Reads `docs/engine-reference/phaser/VERSION.md` before Phaser API guidance
- [ ] Routes TypeScript code to `phaser-typescript-specialist`
- [ ] Routes rendering, filters, post-fx, particles, cameras, and atlases to `phaser-rendering-specialist`
- [ ] Routes Arcade and Matter Physics to `phaser-physics-specialist`
- [ ] Routes Phaser text, bitmap text, DOM overlay, and responsive UI to `phaser-ui-specialist`
- [ ] Flags Phaser 3 examples as risky until checked against Phaser 4 docs
- [ ] Does not create or request top-level Phaser slash skills

---

## Coverage Notes
- Version context (Case 1) verifies Phaser 4 docs take priority over training data
- Routing cases verify this generalist delegates implementation to Phaser sub-specialists
- Browser testing (Case 3) confirms CI proof uses Playwright canvas evidence
