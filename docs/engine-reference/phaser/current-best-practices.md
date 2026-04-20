# Phaser — Current Best Practices

Last verified: 2026-04-20

## Core Guidance

- Prefer **TypeScript** with strict mode for new Phaser projects.
- Build around **scene lifecycle** (`init` / `preload` / `create` / `update`) but keep long-lived game state in explicit services, not ad-hoc globals.
- Prefer **texture atlases** or packed sprite sheets over many loose files.
- Use **object pooling** for bullets, particles, and frequently spawned enemies.
- Keep **input, scene state, and UI state** decoupled. Do not let UI objects own gameplay rules.
- Use **DOM overlays** when you need browser accessibility, form controls, or rich responsive layout. Use canvas UI for in-world and low-latency HUD elements.

## Post-Cutoff Notes

- `Scale.EXPAND` is safer on ultra-wide displays because 3.90.0 clamps huge canvas growth.
- DOM object creation is stricter in 3.90.0; configure DOM support up front.
- WebAudio handling improved in 3.88.0 and 3.90.0, but browser-specific resume/unlock behavior still needs real-device testing.
- `RenderTexture` / `DynamicTexture` now default `forceEven: true`; keep that default unless exact odd dimensions matter more than filtering quality.

## Browser-First Rules

- Budget for **GPU upload, texture memory, and bundle size** early.
- Validate **suspend/resume** flows on iOS Safari, Chrome, and Firefox.
- Treat **Phaser 4** as separate future work; do not blend v4 examples into v3 projects.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
- https://phaser.io/examples
