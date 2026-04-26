# Agent Test Spec: phaser-ui-specialist

## Agent Summary
Domain: Phaser 4 text, bitmap text, DOM overlay integration, input focus behavior, responsive HUD layout, scale manager UI constraints, and UI-specific browser tests.
Does NOT own: TypeScript project structure (phaser-typescript-specialist), rendering/post-fx/camera effects (phaser-rendering-specialist), physics setup (phaser-physics-specialist), or general engine routing (phaser-specialist).
Model tier: Sonnet (default).
No gate IDs assigned.

---

## Static Assertions (Structural)

- [ ] `description:` field is present and domain-specific (references Phaser 4 UI / text / bitmap text / DOM overlays / responsive scale)
- [ ] `allowed-tools:` list includes Read, Write, Edit, Bash, Glob, Grep
- [ ] Model tier is Sonnet (default for specialists)
- [ ] Agent definition references `docs/engine-reference/phaser/VERSION.md` as the authoritative Phaser UI API source
- [ ] Agent definition requires browser focus and responsive scale checks without defining top-level Phaser slash skills

---

## Test Cases

### Case 1: Text routing
**Input:** "Should the score counter use DOM text or Phaser text?"
**Expected behavior:**
- Chooses between text, bitmap text, and DOM overlay based on interaction and styling needs
- Recommends Phaser text or bitmap text unless DOM interaction/styling requirements justify overlay
- Checks Phaser 4 text APIs against the Phaser reference docs

### Case 2: Browser focus
**Input:** "Add a name-entry text field over the canvas."
**Expected behavior:**
- Flags DOM overlay focus, keyboard capture, and resume-to-game input risks
- Recommends browser tests for focus and game input recovery
- Does NOT treat DOM overlay as equivalent to in-canvas text

### Case 3: Responsive proof
**Input:** "The HUD works on desktop. Can we ship it?"
**Expected behavior:**
- Requires responsive scale checks across mobile and desktop viewports before approval
- Checks HUD readability and non-overlap across viewport sizes
- Uses browser evidence rather than static code inspection alone

### Case 4: Shader redirect
**Input:** "Make the menu background use a particle shader effect."
**Expected behavior:**
- Handles menu layout and UI layering concerns
- Routes shader, camera, and particle details to `phaser-rendering-specialist`
- Does NOT implement rendering effects outside its domain

### Case 5: TypeScript routing
**Input:** "Refactor all UI scene classes into typed modules."
**Expected behavior:**
- Defines UI behavior requirements and component boundaries
- Routes TypeScript-only structure questions to `phaser-typescript-specialist`
- Keeps Phaser UI API choices grounded in Phaser 4 docs

---

## Protocol Compliance

- [ ] Stays within declared domain (Phaser 4 text, bitmap text, DOM overlays, focus behavior, responsive HUD, scale manager UI)
- [ ] Reads `docs/engine-reference/phaser/VERSION.md` before Phaser UI API guidance
- [ ] Chooses between text, bitmap text, and DOM overlay based on interaction and styling needs
- [ ] Flags browser focus and pointer capture risks for DOM overlays and input fields
- [ ] Requires responsive scale tests for HUD and menu changes
- [ ] Routes TypeScript-only structure questions to `phaser-typescript-specialist`
- [ ] Routes shader, camera, and particle questions to `phaser-rendering-specialist`
- [ ] Does not create or request top-level Phaser slash skills

---

## Coverage Notes
- Text routing (Case 1) verifies appropriate Phaser text vs DOM overlay decisions
- Browser focus (Case 2) covers the main DOM overlay runtime risk
- Responsive proof (Case 3) confirms UI acceptance requires mobile and desktop browser evidence
