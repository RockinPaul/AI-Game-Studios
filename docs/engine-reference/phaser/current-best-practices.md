# Phaser — Current Best Practices

Last verified: 2026-04-26 | Engine: Phaser 4.0.0

## Project Shape

- Use TypeScript for new Phaser projects unless the project explicitly chooses
  plain JavaScript.
- Use Vite-style browser bundling for fast iteration and predictable CI.
- Keep Phaser scene classes thin; put game rules in plain TypeScript modules
  that Vitest can test without a browser canvas.

## Scene Lifecycle

- Load assets in `preload()`, construct world state in `create()`, and keep
  `update()` focused on per-frame behavior that cannot be event-driven.
- Use scene transitions deliberately. Document what data is passed through the
  registry, scene data, or a project-owned state module.

## Browser Runtime

- Test pure logic with Vitest and browser/canvas behavior with Playwright.
- Use stable canvas dimensions in smoke tests so screenshots and input positions
  are deterministic.
- Treat mobile browser, desktop browser, and embedded webview behavior as
  distinct platform targets when input or scaling matters.

## Performance

- Atlas sprites, reuse objects, and avoid allocations inside `update()`.
- Use Phaser cameras, groups, containers, and object pools deliberately; each has
  transform and traversal cost.
- Profile in browser dev tools and record the browser used for evidence.
