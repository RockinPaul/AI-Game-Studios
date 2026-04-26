# Phaser — Breaking Changes

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

## Phaser 3 to Phaser 4

- Phaser 4 is a post-cutoff major release. Treat Phaser 3 examples from older
  tutorials as suspect until checked against the official v4 docs or the
  vendored `v3-to-v4-migration` skill.
- Prefer TypeScript-friendly imports and module boundaries over global script-tag
  examples for new projects.
- Verify renderer, filter, post-fx, and shader examples against the v4 rendering
  docs because Phaser 4 changed renderer internals.
- Verify physics examples against the v4 Arcade and Matter docs before using
  Phaser 3 snippets from search results.

## Migration Source

- `docs/engine-reference/phaser/skills/v3-to-v4-migration/SKILL.md`
- https://github.com/phaserjs/phaser/releases/tag/v4.0.0
