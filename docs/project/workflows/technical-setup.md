# Technical Setup Workflow

Derived from the `technical-setup` phase in `docs/project/workflow-catalog.yaml`.

## Phase Goal

Translate approved design into technical direction: architecture, ADRs,
programmer control rules, and project-wide accessibility commitments.

## Required Artifacts

- `docs/architecture/architecture.md`
- `docs/architecture/adr-*.md`
  Condition: at least 3 ADRs.
- `docs/architecture/architecture-review-*.md`
- `docs/architecture/control-manifest.md`
- `design/accessibility-requirements.md`

## Optional Artifacts

- Additional ADRs beyond the minimum foundation set.
- Supplemental engine reference notes if the target engine version introduces
  knowledge risk.

## Review Points

- Review the architecture for completeness and consistency with the approved
  design set.
- Review ADR coverage so major technical decisions are explicit rather than
  implicit in code.
- Review the control manifest for direct implementation guidance.
- Review accessibility commitments before UX and feature work expand.

## Runtime-Neutral Execution Guidance

1. Write the master architecture document in `docs/architecture/architecture.md`
   using the approved concept and system design set as inputs.
2. Record major technical decisions as ADRs in `docs/architecture/adr-*.md`.
3. Perform an architecture review and save the output as
   `docs/architecture/architecture-review-*.md`.
4. Produce `docs/architecture/control-manifest.md` as the concise ruleset that
   implementers will follow during production.
5. Commit to a project-wide accessibility tier and feature matrix in
   `design/accessibility-requirements.md`.
6. Do not proceed until the architecture can clearly trace back to the designed
   systems and the implementation rules are understandable to a new contributor.

## Next Workflow

After architecture, ADRs, control rules, and accessibility requirements are in
place, continue to `pre-production.md`.
