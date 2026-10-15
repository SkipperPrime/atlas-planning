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
milestones/ATLAS-038.md             Proposed Movie synthesis milestone
decisions/README.md                 Planning conventions and links to technical ADRs
templates/milestone.md              Prospective milestone template
```

Historical records in Atlas remain authoritative. The registry links to them and does not
rewrite or duplicate their detailed evidence. Lifecycle and evidence labels are separate:
implementation completion alone does not imply fresh verification, live validation, human
acceptance, or closure.

## Current baseline

- Historical coverage: ATLAS-001 through ATLAS-037; see the [historical index](milestones/historical/Atlas_001-037_History.md).
- Current milestone: [ATLAS-PLANNING-001](milestones/ATLAS-PLANNING-001.md), awaiting human acceptance of this bootstrap.
- Forward work: [ATLAS-038 onward](roadmap/Atlas_Forward_Roadmap.md).
- Canonical implementation: [Atlas](https://github.com/SkipperPrime/atlas).
- Technical architecture decisions: [Atlas ADR index](https://github.com/SkipperPrime/atlas/blob/main/docs/adr/README.md).

This bootstrap authorizes planning ATLAS-038 only. It does not authorize its implementation.
