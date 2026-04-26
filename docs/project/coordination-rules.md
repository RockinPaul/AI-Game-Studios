# Agent Coordination Rules

## Role Delegation

1. **Vertical delegation**: leadership roles delegate to domain leads, who delegate to specialists.
2. **Horizontal consultation**: same-tier roles may advise each other but should not make binding cross-domain decisions alone.
3. **Conflict resolution**: escalate unresolved design conflicts to the creative lead and technical conflicts to the technical lead.
4. **Change propagation**: when one decision affects multiple domains, a coordinating producer/project lead should manage the rollout.
5. **No unilateral cross-domain changes**: a role should not modify another domain's files without explicit delegation, user approval, or a current user instruction granting autonomy for that scope.

## User-Granted Autonomy

If the user explicitly tells the runtime to act without repeated approvals for a
task, session, or workflow stage, agents may proceed through normal approval
checkpoints across all stages inside that scope. Treat that instruction as
standing approval for file writes and routine decisions covered by the request.

This does not authorize destructive operations, commits, pushes, deployments,
external purchases, credential changes, or major product-direction changes unless
the user explicitly includes those actions. If requirements are ambiguous or an
approved artifact would be contradicted, pause and surface the decision.

## Reasoning Tiers

Use runtime-neutral reasoning tiers rather than provider-specific model names:

| Tier | When to use |
|------|-------------|
| **Fast** | Read-only status checks, formatting, narrow lookups |
| **Balanced** | Normal implementation, system-level design, focused analysis |
| **Deep** | Cross-system synthesis, architecture, high-stakes review |

Runtime adapters can map these tiers to their own concrete model names.

## Orchestration Patterns

This template supports multiple orchestration styles depending on the runtime:

### Inline Role Handoff
One agent stays in the main session and switches role context deliberately.

### In-Process Subagents
The runtime can spawn child agents or tasks inside the same session.

### Parallel Agent Sessions
The runtime can coordinate multiple independent agent sessions in parallel.

## Parallel Work Rule

Only parallelize work when the tasks are independent:

1. The work does not require another branch of analysis to finish first.
2. The tasks will not modify the same files at the same time.
3. The user can still review the outputs at clear checkpoints.
