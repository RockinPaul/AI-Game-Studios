# ADR-[NNNN]: [Title]

## Status

[Proposed | Accepted | Deprecated | Superseded by ADR-XXXX]

## Date

[YYYY-MM-DD — when this ADR was written]

## Last Verified

[YYYY-MM-DD — when this ADR was last confirmed accurate against the current
engine version and design.]

## Decision Makers

[Who was involved in this decision]

## Summary

[2 sentences: what problem this ADR solves, and what was decided.]

## Engine Compatibility

| Field | Value |
|-------|-------|
| **Engine** | [e.g. Godot 4.6 / Unity 6 / Unreal Engine 5.4 / Phaser 3.90.0] |
| **Domain** | [Physics / Rendering / UI / Audio / Navigation / Animation / Networking / Core / Input / Scripting] |
| **Knowledge Risk** | [LOW / MEDIUM / HIGH] |
| **References Consulted** | [engine-reference files used] |
| **Post-Cutoff APIs Used** | [Specific APIs, or "None"] |
| **Verification Required** | [Concrete behaviors to test, or "None"] |

## ADR Dependencies

| Field | Value |
|-------|-------|
| **Depends On** | [ADR-NNNN or "None"] |
| **Enables** | [ADR-NNNN or "None"] |
| **Blocks** | [Epic/Story name or "None"] |
| **Ordering Note** | [Sequencing note] |

## Context

### Problem Statement

[What problem are we solving?]

### Current State

[How does the system work today?]

### Constraints

- [Technical constraints]
- [Timeline constraints]
- [Resource constraints]
- [Compatibility requirements]

### Requirements

- [Functional requirement 1]
- [Functional requirement 2]
- [Performance requirement]
- [Scalability requirement]

## Decision

[The specific technical decision.]

### Architecture

```
[ASCII diagram showing components, data flow, and interfaces]
```

### Key Interfaces

```
[Pseudocode or interface definitions]
```

### Implementation Guidelines

[Specific guidance for implementers]

## Alternatives Considered

### Alternative 1: [Name]

- **Description**: [How this approach would work]
- **Pros**: [What is good about this approach]
- **Cons**: [What is bad about this approach]
- **Estimated Effort**: [Relative effort]
- **Rejection Reason**: [Why it was not chosen]

### Alternative 2: [Name]

[Same structure as above]

## Consequences

### Positive

- [Good outcomes]

### Negative

- [Trade-offs and costs]

### Neutral

- [Changes that are neither good nor bad]

## Risks

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|-----------|

## Performance Implications

| Metric | Before | Expected After | Budget |
|--------|--------|---------------|--------|
| CPU (frame time) | [X]ms | [Y]ms | [Z]ms |
| Memory | [X]MB | [Y]MB | [Z]MB |
| Load Time | [X]s | [Y]s | [Z]s |
| Network (if applicable) | [X]KB/s | [Y]KB/s | [Z]KB/s |

## Migration Plan

1. [Step 1]
2. [Step 2]
3. [Step 3]

**Rollback plan**: [How to revert if this decision proves wrong]

## Validation Criteria

- [ ] [Measurable criterion 1]
- [ ] [Measurable criterion 2]
- [ ] [Performance criterion]

## GDD Requirements Addressed

| GDD Document | System | Requirement | How This ADR Satisfies It |
|-------------|--------|-------------|--------------------------|
| [e.g. `design/gdd/combat.md`] | [e.g. Combat] | [requirement] | [how the ADR satisfies it] |

## Related

- [Related ADRs]
- [Relevant code files once implemented]
