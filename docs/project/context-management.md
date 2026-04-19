# Context Management

Context is a limited resource in any agent session. Manage it actively.

## File-Backed State

**The file is the memory, not the conversation.** Keep durable state on disk.

### Session State File

Maintain `production/session-state/active.md` as a living checkpoint. Update it
after significant milestones:

- design section approved and written to file
- architecture decision made
- implementation milestone reached
- test results obtained

The state file should contain the current task, progress checklist, key
decisions, files being worked on, and open questions.

### Structured Status Block

For Production, Polish, and Release work, include a structured status block in
`active.md` so adapter-specific tooling can parse it if available:

```markdown
<!-- STATUS -->
Epic: Combat System
Feature: Melee Combat
Task: Implement hitbox detection
<!-- /STATUS -->
```

## Incremental File Writing

When creating multi-section documents:

1. Create the file immediately with a skeleton.
2. Draft one section at a time.
3. Write approved sections as you go.
4. Update session state after each section.

## Compaction and Session Resets

- Compact or clear context proactively between unrelated tasks.
- After any disruption, read `production/session-state/active.md` first.
- Re-read partially completed files before resuming.

## Delegation Guidance

Use separate roles, child agents, or parallel sessions when exploration would
consume substantial context and can be cleanly summarized.
