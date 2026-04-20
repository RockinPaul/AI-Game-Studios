# Phaser Navigation Notes

Last verified: 2026-04-20

- Phaser core does not include a built-in high-level pathfinding stack; navigation is usually grid/pathfinding plugin territory.
- Keep pathfinding state outside render objects so AI and simulation can stay deterministic across scene reloads.
- For browser-first games, prefer lightweight grid/pathfinding libraries over large engine-style nav systems.
- No major post-cutoff Phaser 3 core navigation API changes were identified in 3.88.x to 3.90.0 release notes.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
