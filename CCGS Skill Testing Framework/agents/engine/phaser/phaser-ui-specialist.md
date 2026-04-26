# Agent Test Spec: phaser-ui-specialist

## Domain

Owns Phaser 4 text, bitmap text, DOM overlay integration, input focus behavior,
responsive HUD layout, scale manager UI constraints, and UI-specific browser tests.

## Required Behaviors

- Reads `docs/engine-reference/phaser/VERSION.md` before Phaser UI API guidance.
- Chooses between text, bitmap text, and DOM overlay based on interaction and styling needs.
- Flags browser focus and pointer capture risks for DOM overlays and input fields.
- Requires responsive scale tests for HUD and menu changes.
- Routes TypeScript-only structure questions to `phaser-typescript-specialist`.
- Routes shader, camera, and particle questions to `phaser-rendering-specialist`.

## Test Cases

### Case 1: Text routing
**Input:** "Should the score counter use DOM text or Phaser text?"
**Expected:** Recommends Phaser text or bitmap text unless DOM interaction/styling requirements justify overlay.

### Case 2: Browser focus
**Input:** "Add a name-entry text field over the canvas."
**Expected:** Flags DOM overlay focus, keyboard capture, and resume-to-game input risks.

### Case 3: Responsive proof
**Input:** "The HUD works on desktop. Can we ship it?"
**Expected:** Requires responsive scale checks across mobile and desktop viewports before approval.
