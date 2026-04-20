# Phaser Physics Notes

Last verified: 2026-04-20

- Default to **Arcade Physics** for most 2D action games; choose **Matter.js** only when you need rigid-body features Phaser Arcade does not provide.
- 3.90.0 added `collisionMask` and `collisionCategory` checks inside `Arcade.World.separate`, which matters for mixed-group collision setups.
- 3.90.0 fixed immovable circle push behavior; retest custom circle collision hacks before keeping them.
- 3.88.0 improved `Body.setGameObject` / `StaticBody.setGameObject`; dynamic body reassignment is safer than older patterns.
- Matter world update got a dormant-tab hang fix in 3.88.0; still test tab suspend/resume behavior for long-running browser sessions.

## Verified Sources

- https://github.com/phaserjs/phaser/releases/tag/v3.88.0
- https://github.com/phaserjs/phaser/releases/tag/v3.90.0
- https://docs.phaser.io/
