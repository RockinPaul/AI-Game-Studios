# Phaser Networking Notes

Last verified: 2026-04-20

- Phaser does not ship an opinionated multiplayer stack. Browser networking normally means WebSockets or WebRTC wrappers layered beside Phaser.
- Treat networking as application architecture, not engine feature: scene code should consume replicated state, not own transport details.
- Common choices for browser-first games: Colyseus, Geckos.io, or raw WebSocket backends.
- No major post-cutoff Phaser 3 core networking API changes were identified in 3.88.x to 3.90.0 release notes.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
