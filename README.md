# Atlas Milestone Planning

Atlas-only planning and governance for the Atlas implementation repository. This repository
tracks milestone intent, status, dependencies, authorization, acceptance, checkpoint pointers,
milestone architecture ADRs, roadmap entries, and deferred capabilities. The implementation
repository remains authoritative for code, implementation-level technical ADRs, audits, and
acceptance artifacts.

## Structure

```text
roadmap/Atlas_Master_Milestones.md   Canonical milestone registry and lifecycle rules
roadmap/Atlas_Forward_Roadmap.md     Prospective work after ATLAS-037
decisions/                           Planning architecture decisions and deferred capabilities
milestones/historical/Atlas_001-037_History.md  Evidence-based historical index
milestones/ATLAS-PLANNING-001.md    Governance bootstrap record
milestones/ATLAS-038.md             Movie synthesis milestone
milestones/ATLAS-039.md             Application layout milestone
decisions/README.md                 Planning ADR index and conventions
templates/milestone.md              Prospective milestone template
maintenance/2026-10-15-post-038-consolidation.md  Completed repository consolidation and archive evidence
```

Historical records in Atlas remain authoritative. The registry links to them and does not
rewrite or duplicate their detailed evidence. Lifecycle and evidence labels are separate:
implementation completion alone does not imply fresh verification, live validation, human
acceptance, or closure.

## Current baseline

- Historical coverage: ATLAS-001 through ATLAS-037; see the [historical index](milestones/historical/Atlas_001-037_History.md).
- Governance bootstrap: [ATLAS-PLANNING-001](milestones/ATLAS-PLANNING-001.md), Accepted / Closed.
- Most recently closed product milestone: [ATLAS-038](milestones/ATLAS-038.md), Accepted / Closed (2026-10-15); published Atlas checkpoint `64f436f705caae5c65800865e7abd1bb0081ab3c`.
- Current milestone: [ATLAS-039](milestones/ATLAS-039.md), Proposed; planning accepted, implementation not authorized.
- Forward work: [ATLAS-039 onward](roadmap/Atlas_Forward_Roadmap.md).
- Canonical implementation: [Atlas](https://github.com/SkipperPrime/atlas).
- Planning architecture and deferrals: [planning ADR index](decisions/README.md).
- Implementation technical decisions: [Atlas ADR index](https://github.com/SkipperPrime/atlas/blob/main/docs/adr/README.md).

Milestone architecture and deferred-capability ADRs are authoritative planning decisions here.
They do not authorize implementation. Implementation-level technical ADRs and acceptance evidence
remain in Atlas; link to those records rather than copying their technical authority.

ATLAS-038 was accepted, integrated, published, and closed. The [post-038 repository consolidation](maintenance/2026-10-15-post-038-consolidation.md) is complete. This README and roadmap do not themselves authorize implementation.
