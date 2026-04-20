# Phaser Animation Notes

Last verified: 2026-04-20

- Keep animation ownership explicit: scene loads data, game objects play named animations, gameplay systems decide state changes.
- 3.90.0 fixed `AnimationFrame` duration handling when frame duration is set.
- 3.88.0 fixed `AnimationState.play` to prioritize `frameRate` from `PlayAnimationConfig` over stale external data.
- If animation timing felt inconsistent in older builds, remove bespoke compensation code before carrying it forward.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
