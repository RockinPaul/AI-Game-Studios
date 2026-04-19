# Source Guidelines

## Engine Version Warning

The LLM's training data may predate the pinned engine version.

**Always check `docs/engine-reference/` before using engine APIs.**

## Coding Standards

- Public APIs require doc comments.
- Gameplay values should be data-driven, never hardcoded.
- Prefer dependency injection over singletons for testability.
- Every new system should have a corresponding ADR in `docs/architecture/`.
- Commits should reference the relevant story ID or design document.

## File Routing

Match the engine-specialist role to the file type being written.
See `docs/project/technical-preferences.md` -> Engine Specialists -> File Extension Routing.

## Tests

- Tests live in `tests/`, not in `src/`.
- Every gameplay system should have unit tests covering formulas and edge cases.

## Verification-Driven Development

Write tests first when adding gameplay systems.
For UI changes, verify with screenshots or documented interaction evidence.
