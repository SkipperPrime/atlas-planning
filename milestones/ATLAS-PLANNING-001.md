# ATLAS-PLANNING-001 — Canonical Milestone Governance Bootstrap

**Status:** Verification complete; awaiting human acceptance
**Scope:** Atlas planning repository only
**Implementation repository:** Read-only historical authority
**Planning checkpoint:** The commit containing this record; resolve from planning Git history after commit.

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

This record is ready for human review. On acceptance, update its status and the master registry to
**Accepted / Closed**, retaining this commit as the planning checkpoint. ATLAS-038 remains
**Proposed** until separately authorized for implementation. No implementation changes or remote
push are part of this bootstrap.

## Human review items

- Review the historical qualifications and the explicitly listed evidence gaps, especially for
  milestones without one consolidated closeout record.
- Accept the planning lifecycle and closeout conventions.
- Review ATLAS-038 scope and its one-day bounded-effort target before any later implementation
  authorization.
