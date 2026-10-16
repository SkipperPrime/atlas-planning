# Atlas Planning Decisions and ADR References

## Authority boundary

Milestone architecture decisions, roadmap scope, and deferred-capability decisions are
authoritative in this planning repository. Implementation-level technical contracts, amendments,
and supersession history remain authoritative in the Atlas implementation repository’s
[`docs/adr/`](https://github.com/SkipperPrime/atlas/tree/main/docs/adr/), indexed by its
[ADR README](https://github.com/SkipperPrime/atlas/blob/main/docs/adr/README.md). Planning ADRs
record approved direction and boundaries; they do not copy implementation details or replace
Atlas technical ADRs. Milestone records link to both applicable planning decisions and technical
evidence.

The implementation ADR set currently runs from ADR-0001 through ADR-0064. Planning ADRs continue
the shared identifier sequence, with their planning-only location and authority stated in each
record. The Atlas ADR index remains authoritative for implementation ADRs; this index is
authoritative for planning ADRs. The historical registry provides milestone-level cross-links.

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
genuinely new durable implementation contract, first evaluate whether an amendment or clarification
to an existing Atlas ADR is sufficient and follow the Atlas ADR convention.

## Planning ADR index

| ADR | Status | Decision |
|---|---|---|
| [ADR-0065](0065-application-layout-providers-and-project-layout-presets.md) | Accepted planning decision | Separate application startup, provider-owned layout mechanisms, Project-owned desired-state presets, explicit application, and ordered Movie execution. |
| [ADR-0066](0066-application-layout-deferred-authoring-providers-and-automation.md) | Accepted deferred-decision record | Keep broader providers, visual authoring, automation, learning, and advanced execution capabilities discoverable and deferred. |

ATLAS-039 is governed by [ADR-0065](0065-application-layout-providers-and-project-layout-presets.md)
and links the separate [deferred-capabilities record](0066-application-layout-deferred-authoring-providers-and-automation.md).
