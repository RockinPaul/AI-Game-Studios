# Phaser UI Notes

Last verified: 2026-04-20

- Use canvas UI for low-latency HUD and in-world elements; use DOM overlays for forms, browser accessibility, and layout-heavy screens.
- 3.90.0 now throws when DOM Game Objects are created without correct DOM config. Configure DOM support before using DOM UI.
- `BitmapText#setDisplaySize` landed in 3.90.0; useful for scale-driven UI without hand-rolled math.
- 3.88.0 added `letterSpacing` to `Phaser.Types.GameObjects.Text.TextStyle` and fixed text wrapping with letter spacing.
- 3.88.0 also fixed DOMElement display sizing to respect scale values rather than raw `getBoundingClientRect()` behavior.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
