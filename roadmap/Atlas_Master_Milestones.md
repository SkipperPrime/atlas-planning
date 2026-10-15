# Atlas Master Milestones

This is the canonical planning index for Atlas milestones. Historical facts link to the
implementation repository; prospective scope and governance live here.

## Status snapshot

| Range | Registry disposition |
|---|---|
| ATLAS-001–014 | Historical foundations and implementation sequences; see qualifications and evidence gaps in the [historical index](../milestones/historical/Atlas_001-037_History.md). |
| ATLAS-015–026 | Semantic and Knowledge research/product milestones; outcomes range from completed architecture/product proof to explicitly failed or qualified experiments. |
| ATLAS-027–034 | Knowledge/Tutorial integration, production, and Projection work; several records retain human-review, deferred, or partial status. |
| ATLAS-035–037 | Closed/accepted product milestones; ATLAS-036 and ATLAS-037 checkpoints are verified below. |
| ATLAS-PLANNING-001 | Accepted / Closed; original planning checkpoint `419dae60ceb24137d0535a01926c2266c2355680`. |
| ATLAS-038 | Accepted / Closed 2026-10-15. 038A → 038B → 038C and corrective pass accepted. Atlas `main` implementation checkpoint `ac230c7c960d3e1f61ec70556c470096d2b2514d`; closeout record `64f436f705caae5c65800865e7abd1bb0081ab3c`. |

## Verified recent implementation checkpoints

| Milestone | Checkpoint | Evidence |
|---|---|---|
| ATLAS-036 | `6096d0a786029fcfd7af85d725e8544c3ce4a7bf` | [Movie closeout](https://github.com/SkipperPrime/atlas/blob/main/docs/audits/ATLAS-036-CLOSEOUT.md) |
| ATLAS-037 | `da47e71f3bac50a61f8c597dfb4358793ed27103` | [Projection closeout](https://github.com/SkipperPrime/atlas/blob/main/docs/audits/ATLAS-037-CLOSEOUT.md) |

The later maintenance checkpoint `d15cce1f7ac7b166f320c8db2bd44d5ea00c946c` consolidates the
accepted history on implementation `main`; it is not the ATLAS-037 acceptance checkpoint.

## Lifecycle

Prospective lifecycle:

**Proposed → Authorized → In Progress → Verification → Accepted → Closed**

Explicit alternate states are **Blocked**, **Deferred**, **Superseded**, and **Cancelled**. A
milestone has one lifecycle state at a time. Dependencies and blockers are recorded separately;
they explain readiness and do not silently substitute for a lifecycle state.

Track evidence independently from lifecycle:

- **Implementation completed** — authorized implementation scope is present.
- **Tests documented** — commands and results are recorded, with their scope and failures.
- **Freshly verified** — required checks were run against the identified checkpoint.
- **Live validated** — required behavior was demonstrated in the named real or acceptance environment.
- **Human accepted** — explicit acceptance or another recorded disposition exists.
- **Closed and checkpointed** — closure requirements below are met and a checkpoint is traceable.

Do not infer one evidence state from another. In particular, passing tests do not establish live
validation or human acceptance.

## Required milestone record

Each prospective milestone document states:

1. Objective, scope, exclusions, and authorization boundary.
2. Lifecycle state, evidence state, dependencies, and blockers as separate fields.
3. Acceptance criteria and the evidence required to satisfy each one.
4. Canonical technical ADR links and source milestone/audit links.
5. Intended implementation branch; actual branch and checkpoint at closeout.
6. Verification commands/results, live environment when relevant, human disposition, and deferred work.

Historical records preserve only facts supported by surviving Atlas evidence. Unknown titles,
dates, branch names, checkpoint SHAs, and acceptance outcomes remain explicitly unknown.

## Authorization and closeout

Planning a milestone does not authorize implementation. The milestone record must identify the
authorized scope and any restricted data, external-system, or publication boundary before work
starts. Changes outside that boundary require a separate authorization.

A milestone closes when:

1. Authorized scope is complete, or its outcome is explicitly qualified.
2. Verification evidence and its limits are recorded.
3. Human acceptance or another explicit disposition is recorded.
4. The authoritative implementation checkpoint is identified where available.
5. The planning registry and milestone record agree on status.
6. Development worktrees are reviewed and obsolete ones are removed after safe integration.

Worktree cleanup is review, not automatic deletion: preserve unmerged commits, unique branches,
stashes, valuable data, and dirty or active work until safely reconciled. Never rewrite accepted
history as part of routine closeout.

## Traceability and technical decisions

Implementation branch names and full commit SHAs are recorded only when verified in Git or an
authoritative audit. A branch name is not itself evidence of acceptance. Checkpoint SHA from an
implementation repository is distinct from a planning bootstrap commit.

Technical ADRs live only in Atlas at [`docs/adr/`](https://github.com/SkipperPrime/atlas/tree/main/docs/adr/).
Planning records link to the governing ADRs and retain amendments and supersession history; they
do not copy or supersede technical decisions. Planning-specific conventions are indexed in
[`decisions/README.md`](../decisions/README.md).

The [historical registry](../milestones/historical/Atlas_001-037_History.md) is an index, not a
replacement for implementation audits. The [forward roadmap](Atlas_Forward_Roadmap.md) begins at
ATLAS-038 and remains subordinate to explicit milestone authorization.
