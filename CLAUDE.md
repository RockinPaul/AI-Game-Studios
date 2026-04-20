# Claude Adapter -- Game Studios Template

This file is the Claude-specific entrypoint for the Game Studios template.

The shared, runtime-neutral project guidance now lives in `docs/project/`.
Use that as the system's core documentation. Treat `.claude/` as the Claude
adapter layer.

## Technology Stack

- **Engine**: [CHOOSE: Godot 4 / Unity / Unreal Engine 5 / Phaser 3]
- **Language**: [CHOOSE: GDScript / C# / C++ / Blueprint / TypeScript / JavaScript]
- **Version Control**: Git with trunk-based development
- **Build System**: [SPECIFY after choosing engine]
- **Asset Pipeline**: [SPECIFY after choosing engine]

> **Note**: Engine-specialist agents exist for Godot, Unity, Unreal, and Phaser with
> dedicated sub-specialists. Use the set matching your engine.

## Project Structure

@docs/project/directory-structure.md

## Engine Version Reference

@docs/engine-reference/README.md

## Technical Preferences

@docs/project/technical-preferences.md

## Coordination Rules

@docs/project/coordination-rules.md

## Collaboration Protocol

**User-driven collaboration, not autonomous execution.**
Every task follows: **Question -> Options -> Decision -> Draft -> Approval**

- Agents MUST ask "May I write this to [filepath]?" before using Write/Edit tools
- Agents MUST show drafts or summaries before requesting approval
- Multi-file changes require explicit approval for the full changeset
- No commits without user instruction

See `docs/COLLABORATIVE-DESIGN-PRINCIPLE.md` for full protocol and examples.

> **First session in Claude Code?** If the project has no engine configured and no
> game concept, run `/start` to begin the guided onboarding flow.

## Coding Standards

@docs/project/coding-standards.md

## Context Management

@docs/project/context-management.md
