# Engine Setup Workflow

This guide defines the neutral meaning of engine selection and version pinning.
Runtime adapters may provide different UX, but they should all produce same
artifacts and decision record.

## Goal

Pick engine that fits project, pin exact version, document language/tooling
defaults, and create version-aware engine reference docs before downstream
architecture and UX work expand.

## Required Outputs

- `docs/project/technical-preferences.md`
  Condition: engine, language, rendering, physics, input/platform, naming, and specialist routing are filled in.
- `docs/engine-reference/<engine>/VERSION.md`
- `docs/engine-reference/<engine>/breaking-changes.md`
- `docs/engine-reference/<engine>/deprecated-apis.md`
- `docs/engine-reference/<engine>/current-best-practices.md`

## Supported Engine Choices

### Godot 4

- Best fit: 2D, indie 3D, fast iteration, open-source workflow
- Trade-offs: thinner 3D ecosystem, console export friction, smaller hiring/tutorial surface
- Language choices: GDScript, C#, or mixed

### Unity 6

- Best fit: mobile, mid-scope 3D, console targets, broad asset/tutorial ecosystem
- Trade-offs: heavier editor, licensing trust concerns, more setup overhead than Godot
- Language choices: C#

### Unreal Engine 5

- Best fit: high-end 3D, photoreal, open world, AAA-style pipeline
- Trade-offs: steepest learning curve, heavy editor/toolchain, weak web/mobile fit
- Language choices: C++, Blueprint, or mixed

### Phaser 3

- Best fit: browser-first 2D, HTML5 portals, educational games, jams, PWAs, mobile web
- Trade-offs: 2D only, no built-in editor, native store releases need wrappers, Phaser 4 migration is separate future work
- Language choices: TypeScript (recommended) or JavaScript

## Decision Guidance

1. Prior experience matters first. Existing engine fluency usually beats abstract scoring.
2. Platform target can eliminate weak fits:
   - Web / Browser -> Phaser strongly preferred; Godot viable; Unity WebGL workable; Unreal poor
   - Mobile -> Unity preferred; Godot viable for simpler scope; Phaser viable for mobile web/PWA; Unreal usually poor
   - Console -> Unity or Unreal preferred; Godot requires extra publishing support; Phaser requires wrapper strategy and is rarely first choice
   - PC only -> all engines viable; genre, art, and team experience decide
3. Match engine to content type:
   - 2D browser-first -> Phaser or Godot
   - 2D native-first -> Godot
   - 3D mid-scope -> Unity
   - 3D high-end / photoreal / open world -> Unreal
4. Prefer smallest engine that honestly covers project needs.

## Execution Guidance

1. Identify target platforms, input methods, team experience, and genre constraints.
2. Choose engine and language stack.
3. Pin exact engine version, not just major line.
4. Populate `docs/project/technical-preferences.md`.
5. Create or refresh `docs/engine-reference/<engine>/` so agents do not rely on stale model memory.
6. Update any adapter-specific mirror files after neutral files are correct.

## Review Points

- Engine choice matches platform and scope reality, not aspirational overreach.
- Version is explicit and backed by engine-reference docs.
- Technical preferences are detailed enough for UX, testing, and implementation routing.
- Adapter files mirror neutral choices instead of redefining them.

## Next Step

After engine setup is complete, continue concept work in `concept.md` or proceed
to downstream workflow that depends on populated technical preferences.
