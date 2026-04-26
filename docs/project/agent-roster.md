# Agent Roster

The shared, runtime-neutral role library lives under `agents/`. Runtime adapters
may package or expose these roles differently, but the role names and boundaries
stay the same.

## How To Use

1. Start at `agents/README.md` for neutral navigation.
2. Pick a role from the grouped tables below.
3. Open the linked file in `agents/directors/`, `agents/leads/`,
   `agents/specialists/`, or `agents/engine/`.

## Reasoning Tiers

- `Fast`: narrow execution, focused checks, concise status or review work
- `Balanced`: standard depth for most design, implementation, and coordination
- `Deep`: arbitration, strategy, architecture, or major cross-discipline decisions

## Directors

| Role | Domain | Tier | File | When to Use |
|------|--------|------|------|-------------|
| `creative-director` | High-level vision | Deep | `agents/directors/creative-director.md` | Major creative decisions, pillar conflicts, tone and direction |
| `technical-director` | Technical vision | Deep | `agents/directors/technical-director.md` | Architecture decisions, engine strategy, technical risk, performance direction |
| `producer` | Production management | Deep | `agents/directors/producer.md` | Sprint planning, milestone tracking, sequencing, coordination, risk management |
| `art-director` | Visual direction | Balanced | `agents/directors/art-director.md` | Style guides, art bible, asset standards, UI visual direction |
| `audio-director` | Audio direction | Balanced | `agents/directors/audio-director.md` | Music direction, sound palette, audio implementation strategy |
| `narrative-director` | Story and writing | Balanced | `agents/directors/narrative-director.md` | Story arcs, world-building, character framing, dialogue strategy |

## Leads

| Role | Domain | Tier | File | When to Use |
|------|--------|------|------|-------------|
| `game-designer` | Game design | Balanced | `agents/leads/game-designer.md` | Mechanics, systems, progression, economy, balancing |
| `lead-programmer` | Code architecture | Balanced | `agents/leads/lead-programmer.md` | System design, code review, API design, refactoring |
| `qa-lead` | Quality assurance | Balanced | `agents/leads/qa-lead.md` | Test strategy, bug triage, release readiness, regression planning |
| `release-manager` | Release pipeline | Balanced | `agents/leads/release-manager.md` | Build management, versioning, changelogs, deployment, rollbacks |
| `localization-lead` | Internationalization | Balanced | `agents/leads/localization-lead.md` | String externalization, translation pipeline, locale testing |

## Specialists

| Role | Domain | Tier | File | When to Use |
|------|--------|------|------|-------------|
| `systems-designer` | Systems design | Balanced | `agents/specialists/systems-designer.md` | Specific mechanic implementation, formula design, loops |
| `level-designer` | Level design | Balanced | `agents/specialists/level-designer.md` | Level layouts, pacing, encounter design, flow |
| `economy-designer` | Economy and balance | Balanced | `agents/specialists/economy-designer.md` | Resource economies, loot tables, progression curves |
| `gameplay-programmer` | Gameplay code | Balanced | `agents/specialists/gameplay-programmer.md` | Feature implementation, gameplay systems code |
| `engine-programmer` | Engine systems | Balanced | `agents/specialists/engine-programmer.md` | Core engine, rendering hooks, physics-facing code, memory-sensitive systems |
| `ai-programmer` | AI systems | Balanced | `agents/specialists/ai-programmer.md` | Behavior trees, pathfinding, NPC logic, state machines |
| `network-programmer` | Networking | Balanced | `agents/specialists/network-programmer.md` | Netcode, replication, lag compensation, matchmaking |
| `tools-programmer` | Developer tools | Balanced | `agents/specialists/tools-programmer.md` | Editor extensions, pipeline tools, debug utilities |
| `ui-programmer` | UI implementation | Balanced | `agents/specialists/ui-programmer.md` | UI framework, screens, widgets, data binding |
| `technical-artist` | Tech art | Balanced | `agents/specialists/technical-artist.md` | Shaders, VFX, optimization, art pipeline tools |
| `sound-designer` | Sound design | Fast | `agents/specialists/sound-designer.md` | SFX design docs, audio event lists, mixing notes |
| `writer` | Dialogue and lore | Balanced | `agents/specialists/writer.md` | Dialogue writing, lore entries, item descriptions |
| `world-builder` | World and lore design | Balanced | `agents/specialists/world-builder.md` | World rules, faction design, history, geography |
| `qa-tester` | Test execution | Fast | `agents/specialists/qa-tester.md` | Test cases, bug reports, smoke and checklist execution |
| `performance-analyst` | Performance | Balanced | `agents/specialists/performance-analyst.md` | Profiling, optimization recommendations, memory analysis |
| `devops-engineer` | Build and deploy | Fast | `agents/specialists/devops-engineer.md` | CI/CD, build scripts, environment workflow |
| `analytics-engineer` | Telemetry | Balanced | `agents/specialists/analytics-engineer.md` | Event tracking, dashboards, experiment instrumentation |
| `ux-designer` | UX flows | Balanced | `agents/specialists/ux-designer.md` | User flows, wireframes, accessibility, input handling |
| `prototyper` | Rapid prototyping | Balanced | `agents/specialists/prototyper.md` | Throwaway prototypes, mechanic testing, feasibility validation |
| `security-engineer` | Security | Balanced | `agents/specialists/security-engineer.md` | Anti-cheat, exploit prevention, save integrity, network security |
| `accessibility-specialist` | Accessibility | Fast | `agents/specialists/accessibility-specialist.md` | WCAG-informed checks, remapping, text scaling, readability |
| `live-ops-designer` | Live operations | Balanced | `agents/specialists/live-ops-designer.md` | Seasons, events, retention, live economy |
| `community-manager` | Community | Fast | `agents/specialists/community-manager.md` | Patch notes, player feedback, crisis communications, community health |

## Engine Specialists

Use the engine-specific role set that matches the current project.

| Role | Engine | Tier | File | When to Use |
|------|--------|------|------|-------------|
| `godot-specialist` | Godot | Balanced | `agents/engine/godot-specialist.md` | Godot architecture, scene patterns, plugin and workflow choices |
| `godot-gdscript-specialist` | Godot | Balanced | `agents/engine/godot-gdscript-specialist.md` | GDScript structure, signals, scene scripting |
| `godot-csharp-specialist` | Godot | Balanced | `agents/engine/godot-csharp-specialist.md` | Godot C# integration, tooling, mixed-language architecture |
| `godot-shader-specialist` | Godot | Balanced | `agents/engine/godot-shader-specialist.md` | Godot shaders, materials, renderer trade-offs |
| `godot-gdextension-specialist` | Godot | Balanced | `agents/engine/godot-gdextension-specialist.md` | Native bindings, GDExtension, low-level integration |
| `unity-specialist` | Unity | Balanced | `agents/engine/unity-specialist.md` | Unity architecture, package choices, rendering, input |
| `unity-ui-specialist` | Unity | Balanced | `agents/engine/unity-ui-specialist.md` | UI Toolkit, uGUI, HUD, Unity UI stack decisions |
| `unity-shader-specialist` | Unity | Balanced | `agents/engine/unity-shader-specialist.md` | Unity shaders, SRP, material workflows |
| `unity-dots-specialist` | Unity | Balanced | `agents/engine/unity-dots-specialist.md` | DOTS, ECS, Jobs, Burst architecture |
| `unity-addressables-specialist` | Unity | Balanced | `agents/engine/unity-addressables-specialist.md` | Addressables, asset loading, content packaging |
| `unreal-specialist` | Unreal | Balanced | `agents/engine/unreal-specialist.md` | Unreal framework, module layout, plugin choices |
| `ue-gas-specialist` | Unreal | Balanced | `agents/engine/ue-gas-specialist.md` | Gameplay Ability System, attributes, effects |
| `ue-replication-specialist` | Unreal | Balanced | `agents/engine/ue-replication-specialist.md` | Unreal replication, authority flow, multiplayer behavior |
| `ue-umg-specialist` | Unreal | Balanced | `agents/engine/ue-umg-specialist.md` | UMG, HUD, Unreal UI architecture |
| `ue-blueprint-specialist` | Unreal | Balanced | `agents/engine/ue-blueprint-specialist.md` | Blueprint architecture, Blueprint and C++ boundaries |
| `phaser-specialist` | Phaser | Balanced | `agents/engine/phaser-specialist.md` | Phaser architecture, scene lifecycle, loader, browser deployment |
| `phaser-typescript-specialist` | Phaser | Balanced | `agents/engine/phaser-typescript-specialist.md` | TypeScript scene code, module boundaries, Vitest-friendly logic |
| `phaser-rendering-specialist` | Phaser | Balanced | `agents/engine/phaser-rendering-specialist.md` | WebGL, filters, post-fx, shaders, particles, cameras, atlases |
| `phaser-physics-specialist` | Phaser | Balanced | `agents/engine/phaser-physics-specialist.md` | Arcade Physics, Matter Physics, collisions, physics performance |
| `phaser-ui-specialist` | Phaser | Balanced | `agents/engine/phaser-ui-specialist.md` | Phaser text, bitmap text, DOM overlay, responsive UI, browser focus |
