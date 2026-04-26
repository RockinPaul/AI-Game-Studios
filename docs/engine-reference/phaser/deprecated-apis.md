# Phaser — Deprecated or Risky Patterns

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

| Avoid | Use Instead | Reason |
|---|---|---|
| Unverified Phaser 3 tutorial snippets | Phaser 4 docs plus vendored v4 skills | Phaser 4 is a major post-cutoff release |
| Global `Phaser` script-tag architecture for app projects | TypeScript modules with explicit imports | Keeps project testable and compatible with modern bundlers |
| Polling every input in broad `update()` loops | Phaser input events or scoped update logic | Reduces frame work and makes tests easier |
| Loading assets inside active gameplay logic | Scene `preload()` and Loader events | Keeps loading lifecycle deterministic |
| Recreating text, particles, or temporary sprites each frame | Reuse, pool, or update existing game objects | Avoids browser GC spikes |
