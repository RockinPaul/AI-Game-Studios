# Phaser Input Notes

Last verified: 2026-04-20

- Treat keyboard/mouse, touch, and gamepad as separate UX layers even when using one Phaser scene.
- 3.88.0 fixed `InputPlugin.processDragUpEvent` world-space coordinates; remove local-space workarounds if they were added for older builds.
- DOM overlays need explicit focus-management design; Phaser canvas input alone will not give browser accessibility semantics.
- Gamepad support is partial compared with native engines. Test menu navigation and prompt swapping explicitly.
- Pointer-heavy games should validate browser scaling math after 3.90.0 `EXPAND` clamp changes.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
