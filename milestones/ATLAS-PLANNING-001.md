# ATLAS-PLANNING-001 — Canonical Milestone Governance Bootstrap

**Status:** Accepted / Closed
**Scope:** Atlas planning repository only
**Implementation repository:** Read-only historical authority
**Planning checkpoint:** `419dae60ceb24137d0535a01926c2266c2355680` (published bootstrap; preserved).

## Objective and delivered scope

Establish an Atlas-only planning repository with a canonical milestone registry, evidence-based
history through ATLAS-037, lifecycle and closeout conventions, ADR cross-references, a forward
roadmap, and the proposed ATLAS-038 planning document.

The bootstrap does not authorize ATLAS-038 implementation. The planning repository is the only
write target. Atlas implementation files, branches, and history were read-only.

## Baselines verified

- Atlas implementation `main`: `d15cce1f7ac7b166f320c8db2bd44d5ea00c946c`; clean and descended from accepted ATLAS-036 `6096d0a786029fcfd7af85d725e8544c3ce4a7bf` and ATLAS-037 `da47e71f3bac50a61f8c597dfb4358793ed27103`.
- Atlas planning `main` before bootstrap: `d5ec3f1c30c5d2cfacbbccb3370f437f94f8376d`; clean; remote `origin` is the Atlas planning repository.
- Historical milestone audits and technical ADRs remain in the implementation repository and are linked rather than copied.

## Acceptance criteria and verification

| Criterion | Evidence |
|---|---|
| Registry covers every identifier ATLAS-001 through ATLAS-037. | [Historical index](historical/Atlas_001-037_History.md) has one row for each sequential identifier; reviewed with an explicit sequence check before commit. |
| Historical status/acceptance distinctions and evidence limits are retained. | Rows quote qualified outcomes and link canonical audit/ADR sources; evidence gaps are called out rather than filled by inference. |
| Lifecycle, authorization, dependency/blocker, ADR, branch, checkpoint, and closeout conventions are defined. | [Master registry](../roadmap/Atlas_Master_Milestones.md) and [planning decisions](../decisions/README.md). |
| ATLAS-038 planning scope, slices, dependencies, boundaries, and acceptance are captured without implementation authorization. | [ATLAS-038](ATLAS-038.md). |
| Forward roadmap follows the agreed post-037 priorities. | [Forward roadmap](../roadmap/Atlas_Forward_Roadmap.md). |
| Planning repository contains no unrelated product content and validates cleanly. | Exact changed-file review; `git diff --check`; staged diff review; commit scope limited to this governance structure. |

## Closeout disposition

Human acceptance was explicitly recorded in the ATLAS-038 Authorization and Implementation
Kickoff instruction. ATLAS-PLANNING-001 is Accepted / Closed at its original published planning
checkpoint `419dae60ceb24137d0535a01926c2266c2355680`. Historical qualifications and evidence gaps
remain unchanged. No development worktree was created for this planning-only milestone.

The same instruction separately authorizes ATLAS-038 implementation, limited to the published
milestone specification. This acceptance does not change ATLAS-039 or ATLAS-040.
