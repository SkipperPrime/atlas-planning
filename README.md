# Atlas Milestone Planning

Atlas-only planning and governance for the Atlas implementation repository. This repository
tracks milestone intent, status, dependencies, authorization, acceptance, and checkpoint pointers;
the implementation repository remains authoritative for code, technical ADRs, audits, and
acceptance artifacts.

## Structure

```text
roadmap/Atlas_Master_Milestones.md   Canonical milestone registry and lifecycle rules
roadmap/Atlas_Forward_Roadmap.md     Prospective work after ATLAS-037
milestones/historical/Atlas_001-037_History.md  Evidence-based historical index
milestones/ATLAS-PLANNING-001.md    Governance bootstrap record
milestones/ATLAS-038.md             Movie synthesis milestone
decisions/README.md                 Planning conventions and links to technical ADRs
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
- Next proposed milestone: ATLAS-039 — Application Layout Presets & Recording Consistency; planning review only, no implementation authorization. See the [forward roadmap](roadmap/Atlas_Forward_Roadmap.md).
- Canonical implementation: [Atlas](https://github.com/SkipperPrime/atlas).
- Technical architecture decisions: [Atlas ADR index](https://github.com/SkipperPrime/atlas/blob/main/docs/adr/README.md).

ATLAS-038 was subsequently accepted, integrated, published, and closed. The [post-038 repository consolidation](maintenance/2026-10-15-post-038-consolidation.md) is complete. No ATLAS-039 implementation is authorized by this README or roadmap.
