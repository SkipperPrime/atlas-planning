# Atlas Planning Decisions and ADR References

## Authority boundary

Technical architecture decisions remain authoritative in the Atlas implementation repository’s
[`docs/adr/`](https://github.com/SkipperPrime/atlas/tree/main/docs/adr/), indexed by its
[ADR README](https://github.com/SkipperPrime/atlas/blob/main/docs/adr/README.md). This repository
does not copy technical ADRs, create competing implementation decisions, or rewrite their
amendment/supersession history. Milestone records link to the applicable ADR and implementation
audit.

The canonical technical ADR set currently runs from ADR-0001 through ADR-0064. The Atlas ADR
index and each ADR are the authoritative inventory for individual titles, status, amendments,
clarifications, and supersession. The historical registry provides milestone-level cross-links.

## Planning governance conventions

The prospective lifecycle and closeout rules are recorded in the [master milestone registry](../roadmap/Atlas_Master_Milestones.md).
They govern planning metadata only. They do not change product architecture, implementation
authorization, or historical acceptance.

Planning records distinguish:

- lifecycle from dependencies and blockers;
- implementation completion from test evidence, fresh verification, live validation, human
  acceptance, and closure;
- planning checkpoint from implementation checkpoint;
- accepted historical scope from later roadmap interpretation.

The implementation branch, commit SHA, audit, and acceptance artifact are recorded only where
primary Atlas evidence establishes them. When evidence is absent or ambiguous, the record says so.

## Relevant accepted technical decisions for ATLAS-038

ATLAS-038 should link to, not amend without cause:

- ADR-0014 and ADR-0015 — separate execution evidence from presentation composition; managed,
  replaceable tutorial media runtime.
- ADR-0018 and ADR-0019 — unified Tutorial source of truth and authoring views/projections.
- ADR-0021 — reusable canonical Task and Scenario authority.
- ADR-0025 and ADR-0026 — Tutorial composition and shared embedded authored-content model.
- ADR-0028 and ADR-0029 — Task/Scenario authoring and execution contracts.
- ADR-0059 and ADR-0060 — project-authored application operations and Tutorial lifecycle/rendering.
- ADR-0064 — independently authored Movies and reviewed product relations.

This list is scoped guidance, not an exhaustive ADR inventory. If implementation discovers a
genuinely new durable decision, first evaluate whether an amendment or clarification to an
existing ADR is sufficient and follow the Atlas ADR convention.
