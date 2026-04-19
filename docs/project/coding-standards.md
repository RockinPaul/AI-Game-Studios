# Coding Standards

- All game code must include doc comments on public APIs.
- Every system must have a corresponding architecture decision record in `docs/architecture/`.
- Gameplay values must be data-driven (external config), never hardcoded.
- All public methods must be unit-testable (prefer dependency injection over singletons).
- Commits should reference the relevant design document or task ID.
- Use verification-driven development: prove new behavior with tests, screenshots, or documented evidence before marking work complete.

# Design Document Standards

- All design docs use Markdown.
- Each mechanic has a dedicated document in `design/gdd/`.
- Documents must include these 8 required sections:
  1. **Overview**
  2. **Player Fantasy**
  3. **Detailed Rules**
  4. **Formulas**
  5. **Edge Cases**
  6. **Dependencies**
  7. **Tuning Knobs**
  8. **Acceptance Criteria**
- Balance values must link to their source formula or rationale.

# Testing Standards

## Test Evidence by Story Type

All stories should have appropriate test evidence before they are marked done:

| Story Type | Required Evidence | Location | Gate Level |
|---|---|---|---|
| **Logic** | Automated unit test — must pass | `tests/unit/[system]/` | BLOCKING |
| **Integration** | Integration test or documented playtest | `tests/integration/[system]/` | BLOCKING |
| **Visual/Feel** | Screenshot + lead sign-off | `production/qa/evidence/` | ADVISORY |
| **UI** | Manual walkthrough doc or interaction test | `production/qa/evidence/` | ADVISORY |
| **Config/Data** | Smoke check pass | `production/qa/smoke-[date].md` | ADVISORY |

## Automated Test Rules

- **Naming**: `[system]_[feature]_test.[ext]` for files; `test_[scenario]_[expected]` for functions.
- **Determinism**: tests must produce the same result every run.
- **Isolation**: each test sets up and tears down its own state.
- **No hardcoded data**: prefer fixtures or factories over inline magic numbers.
- **Independence**: unit tests should not call external APIs, databases, or file I/O.
