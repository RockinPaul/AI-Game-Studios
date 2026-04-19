# Directory Structure

```text
/
├── AGENTS.md                    # Neutral agent entrypoint
├── CLAUDE.md                    # Claude adapter entrypoint
├── .claude/                     # Claude-specific adapter assets
├── docs/
│   ├── project/                 # Neutral shared project guidance
│   ├── platforms/               # Runtime support and adapter docs
│   ├── architecture/            # ADRs, manifests, traceability
│   └── engine-reference/        # Version-pinned engine API snapshots
├── src/                         # Game source code
├── assets/                      # Game assets
├── design/                      # Design docs, narrative, UX, levels
├── tests/                       # Test suites
├── tools/                       # Build and pipeline tools
├── prototypes/                  # Throwaway prototypes
└── production/                  # Sprint, release, and session artifacts
    ├── session-state/           # Ephemeral session state (gitignored)
    └── session-logs/            # Session audit trail (gitignored)
```

## Adapter Split

- `docs/project/` is the neutral documentation layer.
- `.claude/` is the Claude adapter layer.
- Future runtime adapters should follow the same pattern rather than moving the
  shared project rules back under a runtime-specific directory.
