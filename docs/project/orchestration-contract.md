# Orchestration Contract

This document defines how work is delegated and reviewed in runtime-neutral
terms.

## Delegation Modes

### Inline role handoff
One session stays active and deliberately switches into another role.

### In-process child agent
The runtime can spawn a child task/subagent inside the same session.

### Parallel agent session
The runtime can run separate agents in parallel and reconcile outputs later.

## Required Behaviors

1. **Scope the task clearly** -- objective, owned files, acceptance criteria.
2. **Preserve boundaries** -- do not let two agents edit the same files in parallel.
3. **Use approval gates** -- the user approves major decisions and file writes.
4. **Return explicit status** -- done, needs context, blocked, or concerns.
5. **Review before closure** -- verify that outputs match the intended workflow step.

## Parallelism Rule

Parallel work is safe only when:
- the tasks are independent
- they do not need each other's output to begin
- they do not edit the same files

## Claude Adapter Note

Claude team skills often express this contract using `Task` and
`AskUserQuestion`. Those are adapter implementations of the same underlying
coordination rules.
