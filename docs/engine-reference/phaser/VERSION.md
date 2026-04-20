# Phaser Engine — Version Reference

Last verified: 2026-04-20

| Field | Value |
|-------|-------|
| **Engine Version** | Phaser 3.90.0 |
| **Release Date** | 2025-05-23 |
| **Project Pinned** | 2026-04-20 |
| **Last Docs Verified** | 2026-04-20 |
| **LLM Knowledge Cutoff** | May 2025 |

## Knowledge Gap Warning

The LLM's training data likely covers Phaser 3 up to roughly the late 3.8x
line, but Phaser 3.90.0 landed just after the cutoff and Phaser 4.0.0 shipped
later in 2026. Always cross-reference this directory before suggesting Phaser
API calls, scaling behavior, DOM UI setup, or browser-audio work.

## Scope Note

This template pins Phaser **3.90.0** as the stable Phaser choice. Phaser 4.0.0
exists, but it is a major-architecture jump and should be treated as separate
future work rather than an in-place swap for Phaser 3 projects.

## Post-Cutoff Version Timeline

| Version | Release | Risk Level | Key Theme |
|---------|---------|------------|-----------|
| 3.88.0 | 2025-02-11 | MEDIUM | RenderTexture `forceEven`, earlier WebAudio unlock, iOS audio resume, text and DOM fixes |
| 3.88.1 | 2025-02-12 | LOW | Patch release |
| 3.88.2 | 2025-02-13 | LOW | Patch release |
| 3.90.0 | 2025-05-23 | MEDIUM | Rounded `Rectangle`, safer `EXPAND` scaling, DOM-object config errors, Firefox WebAudio fallback |
| 4.0.0 | 2026-04-10 | HIGH | New render-node architecture, unified filters, major migration outside pinned scope |

## Verified Sources

- Phaser 3.90.0 release: https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- Phaser 3.88.0 release: https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- Phaser 4.0.0 release: https://github.com/phaserjs/phaser/releases/tag/v4.0.0
- API docs: https://docs.phaser.io/
- New docs portal: https://newdocs.phaser.io/
- Examples: https://phaser.io/examples
