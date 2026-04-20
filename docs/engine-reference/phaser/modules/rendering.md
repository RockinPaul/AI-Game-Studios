# Phaser Rendering Notes

Last verified: 2026-04-20

- Phaser 3 remains **WebGL-first** with Canvas fallback; profile both startup and resize behavior in real browsers.
- `Scale.EXPAND` changed in 3.90.0 to clamp oversized canvases on ultra-wide displays.
- `DynamicTexture` / `RenderTexture` default `forceEven: true` since 3.88.0 for cleaner output. Opt out only when exact odd sizing is required.
- `GameObjects.Rectangle.setRounded(radius)` is new in 3.90.0; do not write to `radius` directly.
- `Grid` WebGL `lineWidth` rendering was fixed in 3.90.0.
- Keep atlases tight and batch-friendly; avoid many single-use textures.
- For advanced effects, use custom pipelines or PostFX carefully; verify mobile/WebGL2 fallback.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
