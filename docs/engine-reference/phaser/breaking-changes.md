# Phaser — Breaking Changes

Last verified: 2026-04-20

## 3.88.0

- `DynamicTexture` / `RenderTexture` now default `forceEven` to `true`.
  - Risk: code that relied on odd-sized render textures may get rounded-up dimensions.
  - Response: pass `forceEven: false` only when exact odd sizes are required.

## 3.90.0

- `Scale.EXPAND` now clamps created canvas size on ultra-wide displays.
  - Risk: projects that relied on unbounded canvas growth may see different maximum canvas sizes.
  - Response: validate layout using real browser resize cases; do not assume unlimited width.

- Creating a DOM Game Object without correct DOM configuration now throws an error.
  - Risk: older projects may fail at runtime instead of silently misbehaving.
  - Response: enable DOM container support in game config before using DOM UI.

## 3.x → 4.0.0

- Phaser 4 is a major renderer rewrite, not a drop-in upgrade.
- Filters, renderer internals, and many architecture assumptions changed.
- Treat Phaser 4 migration as a separate ADR and upgrade project.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://github.com/phaserjs/phaser/releases/tag/v4.0.0
