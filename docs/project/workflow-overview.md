# Workflow Overview

This is the neutral, runtime-independent summary of the template workflow.

## Canonical Source

The authoritative phase catalog is `docs/project/workflow-catalog.yaml`.

If a runtime adapter exposes slash commands, buttons, menus, or built-in tools,
those are adapter-specific entrypoints into the same workflow.

## The 7 Phases

1. **Concept** -- shape the idea into a documented concept, choose the engine,
   and map the major systems.
2. **Systems Design** -- author and review the system GDDs.
3. **Technical Setup** -- establish architecture, ADRs, manifests, and core technical rules.
4. **Pre-Production** -- define UX, prototype the core loop, create epics and stories, and plan the first sprint.
5. **Production** -- implement stories, review, QA, and run sprint cycles.
6. **Polish** -- improve performance, balance, assets, and playtest quality.
7. **Release** -- prepare patch notes, checklists, and launch readiness.

## Runtime-Neutral Rule

The workflow is defined by:
- required artifacts
- required review checkpoints
- handoff expectations between roles
- phase readiness conditions

It is **not** defined by any one runtime's command syntax.

## Claude Adapter Mapping

The Claude adapter currently exposes many of these workflow steps as slash
commands under `.claude/skills/`, but those are adapter implementations, not
the neutral definition of the workflow itself.
