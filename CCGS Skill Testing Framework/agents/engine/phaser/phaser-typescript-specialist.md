# Agent Test Spec: phaser-typescript-specialist

## Agent Summary
Domain: Phaser 4 TypeScript architecture, module boundaries, scene class typing, game object typings, build configuration, and pure logic test routing.
Does NOT own: rendering/post-fx work (phaser-rendering-specialist), physics setup (phaser-physics-specialist), UI implementation (phaser-ui-specialist), or broad engine architecture routing (phaser-specialist).
Model tier: Sonnet (default).
No gate IDs assigned.

---

## Static Assertions (Structural)

- [ ] `description:` field is present and domain-specific (references Phaser 4 TypeScript / modules / typed scene classes)
- [ ] `allowed-tools:` list includes Read, Write, Edit, Bash, Glob, Grep
- [ ] Model tier is Sonnet (default for specialists)
- [ ] Agent definition references `docs/engine-reference/phaser/VERSION.md` as the authoritative Phaser API source
- [ ] Agent definition routes pure logic to Vitest and browser/canvas proof to Playwright without defining top-level Phaser slash skills

---

## Test Cases

### Case 1: Typed project structure
**Input:** "Start this Phaser game as a few global JavaScript files on window."
**Expected behavior:**
- Rejects the untyped global script architecture for a new Phaser project
- Recommends TypeScript modules, explicit scene classes, and typed config objects
- Checks Phaser-facing APIs against Phaser 4 docs before final guidance

### Case 2: Pure logic testing
**Input:** "How should we test our damage formula helper?"
**Expected behavior:**
- Recommends a Vitest unit test because the logic does not require Phaser canvas runtime
- Separates pure TypeScript logic from browser scene behavior
- Does NOT require Playwright for non-rendering utility code

### Case 3: Scene typing
**Input:** "Add a MainScene with preload, create, and update."
**Expected behavior:**
- Uses Phaser 4 TypeScript scene typing and verifies APIs against Phaser 4 docs
- Avoids untyped `any`-heavy scene state
- Keeps rendering, physics, and UI-specific behavior routed to the matching specialist

### Case 4: Browser proof routing
**Input:** "The boot scene compiles, but how do we know the canvas appears?"
**Expected behavior:**
- Routes canvas, boot, input, and render proof to Playwright
- Recommends checking canvas visibility and non-empty pixels
- Does NOT treat a Vitest pass as proof that Phaser rendered in a browser

### Case 5: Cross-domain routing
**Input:** "Add a post-fx shader and collision sensor in this TypeScript scene."
**Expected behavior:**
- Handles TypeScript module boundaries and typed scene integration
- Routes post-fx details to `phaser-rendering-specialist`
- Routes collision sensor details to `phaser-physics-specialist`

---

## Protocol Compliance

- [ ] Stays within declared domain (Phaser 4 TypeScript architecture, modules, typing, build config, pure logic tests)
- [ ] Reads `docs/engine-reference/phaser/VERSION.md` before Phaser API guidance
- [ ] Rejects untyped global script architecture for new Phaser projects
- [ ] Recommends TypeScript modules, explicit scene classes, and typed config objects
- [ ] Routes pure game logic and utilities to Vitest when browser rendering is not required
- [ ] Routes canvas, boot, input, and render proof to Playwright
- [ ] Defers rendering, physics, and UI-specific implementation to the matching Phaser sub-specialist
- [ ] Does not create or request top-level Phaser slash skills

---

## Coverage Notes
- Typed project structure (Case 1) protects new projects from global-script architecture
- Pure logic testing (Case 2) verifies Vitest is the default for non-browser logic
- Browser proof (Case 4) confirms Playwright owns runtime canvas evidence
