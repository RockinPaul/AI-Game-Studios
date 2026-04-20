# Phaser — Deprecated / Avoid Patterns

Last verified: 2026-04-20

Official Phaser 3.88.x to 3.90.0 release notes do not publish a large formal
deprecation list, but these are the important "don't use X -> use Y" rules for
the pinned Phaser 3 line.

| Don't use | Use instead | Why |
|-----------|-------------|-----|
| Setting `GameObjects.Rectangle.radius` directly | `GameObjects.Rectangle.setRounded(radius)` | `radius` is read-only in 3.90.0; `setRounded` is the supported API |
| Assuming DOM Game Objects work without DOM config | Enable DOM container support in `GameConfig` before `scene.add.dom()` | 3.90.0 now throws when DOM objects are created without correct config |
| Assuming unbounded `Scale.EXPAND` canvas growth | Test with clamped `EXPAND`, or choose explicit `FIT` / `RESIZE` strategy | 3.90.0 clamps canvas size on extreme displays |
| Forcing odd `RenderTexture` sizes by default | Accept `forceEven: true`, opt out only when exact odd size is required | 3.88.0 changed default for better render quality |
| Mixing Phaser 4 docs into Phaser 3 projects | Use Phaser 3.90.0 docs and examples | Phaser 4 APIs and renderer architecture are not drop-in replacements |

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
- https://newdocs.phaser.io/
