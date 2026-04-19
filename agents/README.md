# Neutral Role Library

This directory is the runtime-neutral role library for the Game Studios
template. It mirrors the existing role roster without relying on
`.claude/agents/`.

Use this library when a runtime needs to:
- discover available roles
- pick a role for delegation, review, or escalation
- understand role boundaries and collaboration paths
- map runtime-specific agent features onto shared project roles

## Discovery Order

1. Read `docs/project/agent-roster.md` for grouped navigation and file paths.
2. Open the matching role file under `agents/directors/`, `agents/leads/`,
   `agents/specialists/`, or `agents/engine/`.
3. Use `agents/templates/role-spec.md` when adding or normalizing more roles.

## Reasoning Tiers

- `Fast`: narrow execution, checklist work, simple verification, focused status capture
- `Balanced`: normal role depth for design, implementation, review, and coordination
- `Deep`: high-stakes direction, arbitration, system strategy, or cross-discipline trade-offs

## Notes

- These files preserve the existing role taxonomy and names from the template.
- `.claude/agents/` remains an adapter-specific source, but this directory is the
  neutral navigation surface for non-Claude runtimes.
- Engine-specific roles stay grouped under `agents/engine/`.
