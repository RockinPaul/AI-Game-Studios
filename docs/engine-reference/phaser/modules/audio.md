# Phaser Audio Notes

Last verified: 2026-04-20

- WebAudio remains browser-policy-sensitive. Always test first interaction, tab suspend/resume, and device mute-state behavior.
- 3.88.0 added earlier audio unlock on `mousedown` / `mouseup` and fixed iOS 17.5.1+ / iOS 18 Safari focus resume behavior.
- 3.90.0 added Firefox fallback for `AudioListener` positional fields used by follow logic.
- Keep music/SFX resume logic explicit; do not assume browser focus behavior is uniform across Safari, Chrome, and Firefox.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
