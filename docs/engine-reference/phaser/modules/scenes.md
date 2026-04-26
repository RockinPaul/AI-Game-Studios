# Phaser Module — Scenes

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

- Use scenes for lifecycle boundaries: boot, preload, menu, gameplay, HUD, and
  result screens.
- Keep game rules in plain TypeScript modules when possible.
- Pass scene data explicitly; avoid global mutable state unless documented.
- Keep `update()` small and event-driven behavior outside the hot path.

Official skill: `docs/engine-reference/phaser/skills/scenes/SKILL.md`
