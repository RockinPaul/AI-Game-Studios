# Agent Test Spec: phaser-rendering-specialist

## Agent Summary
Domain: Phaser 4 rendering, filters, post-fx, particles, cameras, texture atlases, blend modes, performance constraints, and visual evidence requirements.
Does NOT own: TypeScript project structure (phaser-typescript-specialist), physics body/collision behavior (phaser-physics-specialist), UI text/DOM overlays (phaser-ui-specialist), or general engine routing (phaser-specialist).
Model tier: Sonnet (default).
No gate IDs assigned.

---

## Static Assertions (Structural)

- [ ] `description:` field is present and domain-specific (references Phaser 4 rendering / post-fx / particles / cameras / texture atlases)
- [ ] `allowed-tools:` list includes Read, Write, Edit, Bash, Glob, Grep
- [ ] Model tier is Sonnet (default for specialists)
- [ ] Agent definition references `docs/engine-reference/phaser/VERSION.md` as the authoritative Phaser rendering API source
- [ ] Agent definition requires screenshot or Playwright visual evidence and does not define top-level Phaser slash skills

---

## Test Cases

### Case 1: Post-fx verification
**Input:** "Use this Phaser 3 post pipeline example for a glow effect."
**Expected behavior:**
- Checks filters, post-fx, and renderer features against Phaser 4 docs
- Flags Phaser 3 rendering examples as risky until checked against Phaser 4 docs
- Does NOT silently apply stale Phaser 3 rendering APIs

### Case 2: Visual evidence
**Input:** "We changed the particle burst color. Is it good?"
**Expected behavior:**
- Requires screenshot evidence or a Playwright visual check before calling the change verified
- Describes the expected visual condition being checked
- Does NOT approve the change from code inspection alone

### Case 3: Atlas routing
**Input:** "Sprites are pulling the wrong frames from an atlas."
**Expected behavior:**
- Handles atlas/frame debugging within the rendering domain
- Checks texture key, frame name, and atlas loading assumptions
- Routes TypeScript-only structure questions to `phaser-typescript-specialist`

### Case 4: Physics redirect
**Input:** "The collision body is offset from the sprite after scaling."
**Expected behavior:**
- Handles visual alignment evidence and screenshot requirements
- Routes physics body configuration to `phaser-physics-specialist`
- Does NOT make final collision-body decisions outside its domain

### Case 5: Camera effects
**Input:** "Add a camera shake and fade transition for boss attacks."
**Expected behavior:**
- Treats camera effects as in-domain rendering work
- Verifies Phaser 4 camera APIs against the Phaser reference docs
- Requires visual proof for the transition timing and framing

---

## Protocol Compliance

- [ ] Stays within declared domain (Phaser 4 rendering, filters, post-fx, particles, cameras, atlases, visual evidence)
- [ ] Reads `docs/engine-reference/phaser/VERSION.md` before Phaser rendering API guidance
- [ ] Checks filters, post-fx, and renderer features against Phaser 4 docs
- [ ] Requires screenshot or Playwright visual evidence for rendering changes
- [ ] Routes TypeScript-only structure questions to `phaser-typescript-specialist`
- [ ] Routes physics body and collision questions to `phaser-physics-specialist`
- [ ] Flags Phaser 3 rendering examples as risky until checked against Phaser 4 docs
- [ ] Does not create or request top-level Phaser slash skills

---

## Coverage Notes
- Post-fx verification (Case 1) covers the highest-risk Phaser 3 to Phaser 4 rendering drift
- Visual evidence (Case 2) confirms rendering changes need browser-observable proof
- Redirect cases verify rendering work does not absorb physics or TypeScript ownership
