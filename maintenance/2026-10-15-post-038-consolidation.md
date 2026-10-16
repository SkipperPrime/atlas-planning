# Atlas post-ATLAS-038 repository consolidation

- Recorded: 2026-10-15 (America/New_York).
- Type: repository maintenance; not a new product milestone.
- Disposition: **COMPLETE — repository consolidation verified**.
- Authorization: human instructions “ATLAS — Final Repository Consolidation and Production Baseline,” “ATLAS — Final Remote Branch Cleanup,” and “ATLAS — Final Historical Cleanup and Consolidation Closeout,” following the authorized Pass 1 cleanup.
- Implementation baseline: `64f436f705caae5c65800865e7abd1bb0081ab3c`, unchanged on local and advertised remote `main`.
- Planning baseline before this record: `dc03631f346193dcc737fa4ebc0bb9e91877d0ff`, clean and synchronized with advertised remote `main`.
- Initial maintenance checkpoint: `163779d4fca0630bf4bcc43f09546680770ac22e`, preserved in planning history.
- Final maintenance checkpoint: the commit finalizing this record; identify with `git log -1 --format=%H -- maintenance/2026-10-15-post-038-consolidation.md`. The final human instruction authorizes publishing both maintenance commits to existing planning `origin/main` by normal fast-forward push. Final advertised/local SHA equality is verified after publication and reported in the closeout response.
- Canonical product acceptance remains [ATLAS-038](../milestones/ATLAS-038.md), Accepted / Closed. No milestone status, roadmap priority, technical ADR, or implementation behavior changes here.

## Completed branch cleanup

The following 31 redundant local branches were removed during the preceding authorized passes.
All tips were verified reachable from both accepted `main` and `origin/main`; no branch was in
use by a worktree. The last two branches, ATLAS-008 and ATLAS-015, had their outdated upstream
associations unset under explicit authorization before normal `git branch -d`.
No force deletion or accepted-history rewrite occurred.

- `atlas-005/tutorial-studio`
- `atlas-006/tutorial-harness`
- `atlas-007/media-runtime`
- `atlas-008/content-model`
- `atlas-009/instructional-libraries`
- `atlas-010/studio-experience`
- `atlas-011/publishing-channels`
- `atlas-012/generic-semantic-ingestion`
- `atlas-013/studio-redux`
- `atlas-014/ordinary-semantic-interpretation`
- `atlas-015/semantic-products-and-knowledge-composition`
- `atlas-017/receiver-identity-model`
- `atlas-018/evidence-bounded-synthesis`
- `atlas-020/knowledge-architecture-restart`
- `atlas-022/corpus-knowledge-boundary`
- `atlas-023/corpus-bandwidth-recovery`
- `atlas-024/grounding-result-binding`
- `atlas-025/knowledge-product-design`
- `atlas-026/knowledge-reading-presentation`
- `atlas-027/knowledge-product-runtime`
- `atlas-028/full-aria-knowledge-round-trip`
- `atlas-030/instructional-product-generation`
- `atlas-031/executable-visual-tutorials`
- `atlas-033/knowledge-generation-review`
- `atlas-036/movie-product-foundation`
- `atlas-036/movie-execution-recording`
- `atlas-037/movie-projection`
- `atlas-integration/010-011`
- `atlas-integration/011-adr-reconciliation`
- `feature/atlas-038-movie-synthesis`
- `master`

This consolidation pass recognized these deletions and did not repeat them.

## Final local references and worktrees

| Local branch | Tip | Disposition |
|---|---|---|
| main | 64f436f705caae5c65800865e7abd1bb0081ab3c | Accepted production baseline. |

The two noncanonical experimental branch refs were retired after archive recovery and independent
backup verification. Their exact original tips remain in the archive and are recorded below.
Explicit force deletion was authorized only for those two unmerged historical refs; no content
was merged, no accepted history rewritten, and no other local branch force-deleted.

Exactly one registered worktree per repository remains:

- `/Users/tim/Dev/Atlas/atlas`, on implementation `main`.
- `/Users/tim/Dev/Atlas/atlas-planning`, on planning `main`.

`git worktree prune --dry-run --verbose --expire now` found no stale records in either repository.
No worktrees or arbitrary directories were removed.

## Historical archive and authority boundary

Primary local archive:

`/Users/tim/Dev/Atlas/atlas-historical-archives/post-038-2026-10-15/`

Files: `atlas-historical-knowledge.bundle`, `manifest.json`, `README.md`, and `SHA256SUMS`.
Bundle size: 11,018,413 bytes. The bundle is self-contained: it contains complete ancestral Git
history and all objects reachable from the two experimental branch tips and the two stash commits,
including stash index and untracked parents. It has no prerequisite repository.

| Archive file | SHA-256 |
|---|---|
| atlas-historical-knowledge.bundle | 46749a4cd072e969c00e121482307e9074e96627277581906c6798c0f53c80e4 |
| manifest.json | d7b063c9211e6b3dce7d73831bca57b818e60beca1aed0345c1c1918a326878b |
| README.md | 7e9bd43643833c4d14a8fc1c15225b33499bfc06232b9d7cb9af34e5daaee33d |

The manifest records original branch identities, original commit IDs, unique commit subjects,
stash provenance, content hashes, archive timestamp, recovery verification, and retention gate.

The discarded architecture experiment's unique commits are:

- `f52a84b107aa18560aef16a5cb16dab78e47aa40`
- `db6337f356af8f89d52a0955b1bd7a7299dee2cf`
- `bc66ebcc11c8fa18f5dc0bffb7e6ea3ac8f29b38`

The documentation/export experiment's unique commit is
`dfbfcc87011f451f9da564bf01b7b3c1ae45e3b9`.

These are **noncanonical historical evidence**. The architecture experiment was excluded from
architectural authority and ADR numbering by the [ATLAS-020 restart](https://github.com/SkipperPrime/atlas/blob/64f436f705caae5c65800865e7abd1bb0081ab3c/docs/audits/ATLAS-020-RESTART-CHECKPOINT.md).
The documentation/export trial is not accepted current product documentation. Neither was merged
into production. Frozen implementation audits were not edited.

### Recovery verification

A temporary bare staging repository received a read-only object pack of the four original commit
graphs. The bundle was created there; no archival refs were added to the implementation repository.
A second, empty temporary repository successfully:

1. Ran `git bundle verify`.
2. Fetched all four bundled refs, without using the source repository as an alternate.
3. Matched original tip IDs, complete parent graphs, recursive trees, and stash index/untracked trees.
4. Ran `git fsck --full --no-reflogs --no-dangling`.
5. Recovered and compared the four stashed documentation files and compressed sidecar bytes.

Scratch repositories were removed after verification. The archive README gives commands to verify
`SHA256SUMS`, fetch into a new isolated repository, inspect the original branch names, and apply
the documentation stash only in that disposable historical checkout.

### Independent backup and final retirement verification

Independent second copy: [Google Drive historical archive](https://drive.google.com/drive/folders/1tBQ-MX4OLJN9HQSwzYxB3UUiZ9sVYRrH).

Evidence supplied by the user in the final authorization: ChatGPT freshly downloaded the actual
11,018,413-byte bundle from Google Drive, verified bundle SHA-256
`46749a4cd072e969c00e121482307e9074e96627277581906c6798c0f53c80e4`
and the manifest checksum, restored all four refs in isolation, passed bundle/integrity checks,
and confirmed both branch tips and both stash commit IDs.

This local closeout did not claim a second Drive download. It freshly reverified the unchanged
local bundle and all accompanying checksums, recovered it into another empty repository, compared
all four tips, complete parent graphs, recursive content trees and stash index/untracked trees
against the live originals, and passed `git fsck --full --no-reflogs --no-dangling`.

The independent-copy gate is satisfied by the user's supplied Drive verification plus this fresh
local recovery. Only then were the two exact branch refs deleted and the two exact stashes dropped.
The original archive files remain byte-unchanged. Their as-created manifest/README describe the
initial pending gate; this closeout records its subsequent fulfillment without changing the
checksummed first or second copy.

## Stash reconciliation

| Stash identity | Findings | Disposition |
|---|---|---|
| 579c2608f2b1bba6aed9c4417fa1a9968926dc63 | No tracked edits. Its 2,322,747-byte compressed sidecar is byte-identical to accepted main:docs/audits/atlas-021/sidecar.json.gz. Full stash object history is also bundled. | Archived and dropped after verification; no application to main. |
| a0e5dc3e24a64af8f1fea59e860c8a311debf650 | Modified docs/aria/README.md and docs/aria/ShapeNetwork.md, plus untracked docs/aria/api/ShapeNetwork.md and docs/aria/guides/shape-networks.md. All four content hashes verified after bundle recovery. | Archived and dropped after verification; never applied to production. |

Sidecar SHA-256: `cd98dcdfa8dcfd8aba8a6d9b1d42f46f0cae8dcf27ba556d8180bf71741cbbd5`.

Bundle refs are `refs/archive/stashes/evidence-sidecar` and `refs/archive/stashes/aria-docs`.
Both stashes were identified by exact commit ID immediately before each drop. After dropping the
first stash, the second resolved to `stash@{0}` and was reverified against its audited hash.
The final stash inventory is empty.

## Remote branches and hosted verification

The eight historical branches below were deleted by one normal atomic push using explicit
branch-name deletions. Their last advertised tips matched the audit and were ancestors of both
accepted local `main` and `origin/main`. A subsequent fetch with pruning confirmed that only
`origin/main` remains. GitHub advertises only `main`, still its default branch.

| Remote branch | Last verified tip (historical branches deleted; main retained) |
|---|---|
| atlas-005/tutorial-studio | 0a4efdd9e5730f42a5ec265944c6c3aaadda150a |
| atlas-006/tutorial-harness | b0fb1b648b784b1fec1f8eb21a69fab147a38d6f |
| atlas-008/content-model | 711d1a5ceab9d495ae34a9f25610589ec0f233a9 |
| atlas-014/ordinary-semantic-interpretation | 6c94188f29ab625570f633989f4341fbe183a72c |
| atlas-015/semantic-products-and-knowledge-composition | 408282b053547a87dac6f9acd04bf4570d4454d0 |
| atlas-031/executable-visual-tutorials | aad81de6422bf6c3f15e993e55ecc78c816baeb5 |
| atlas-033/knowledge-generation-review | d77ef7097be756ce4f67e919bb16c1c7907ebc90 |
| main | 64f436f705caae5c65800865e7abd1bb0081ab3c |
| master | b0fb1b648b784b1fec1f8eb21a69fab147a38d6f |

Verification before the remote deletion found:

- Default branch: `main`; Pages disabled.
- No open pull requests; no GitHub Actions workflow runs.
- No `.github/workflows` files in any of the nine branch-tip trees.
- Branch-list API reports all candidates unprotected.
- A repository configuration/workflow reference search found historical audit mentions and one
  fixed report label in `scripts/audit-post-016-aria.ts`; no active dependency on the retired refs.
- Earlier API inspection lacked protection-detail access (403), and the available browser was
  signed out. The subsequent administrator-level inspection supplied by the user confirmed:
  no rulesets, classic branch-protection rules, webhooks, Environments, or Pages deployment.
  This explicit confirmation satisfied the hosted-settings gate; inaccessible APIs were not
  repeatedly retried or bypassed.
- All eight remote deletion results were `[deleted]`. No authentication failure occurred.
- No credential, protection, default-branch, ownership, or hosting settings changed.

The remote cleanup was completed before this final historical-reference retirement. Its accepted
main tip remains `64f436f705caae5c65800865e7abd1bb0081ab3c`.
No hosted verification blocker remains.

## Integrity and preservation

- `git fsck --full --no-dangling`: exit 0, no diagnostics, in both repositories.
- Accepted ATLAS-036 `6096d0a786029fcfd7af85d725e8544c3ce4a7bf`,
  ATLAS-037 `da47e71f3bac50a61f8c597dfb4358793ed27103`, and ATLAS-038
  `64f436f705caae5c65800865e7abd1bb0081ab3c` remain reachable from implementation main.
- Implementation main and all accepted implementation files/ADRs are unchanged; only authorized
  historical branch/stash refs were retired. All retained refs are unchanged.
- Both experimental histories and both stash commits, parents, and complete content trees remain
  recoverable from the verified local and independent Google Drive archives.
- Before/after file-metadata inventories cover implementation `.atlas-projects`,
  `docs/audits`, and the entire `/Users/tim/Documents/Atlas Projects/Aria Human Review`
  directory, including acceptance evidence: paths, modes, sizes, and modification times unchanged.
  This is metadata preservation verification, not a new media-render acceptance run.
- Implementation remains clean; planning changes are limited to this maintenance record and its
  README index entry. No product tests/builds were rerun for reference/archive/documentation work.
- No HTTP tracing, credential changes, history rewriting, garbage collection, project-data
  deletion, or ATLAS-039 implementation occurred.

## Final acceptance

| Gate | Result |
|---|---|
| 31 redundant local branches removed | PASS, earlier authorized passes. |
| Eight redundant remote branches removed | PASS, explicit named deletion and fetched inventory. |
| Two unique experimental branches archived and retired | PASS, exact tips and independent-copy verification. |
| Two historical stashes archived and retired | PASS, exact commit IDs and complete content recovery. |
| One Atlas local branch / one remote branch | PASS: `main` / `origin/main`. |
| Zero historical stashes | PASS. |
| No linked or stale worktrees | PASS in both repositories. |
| Accepted implementation main unchanged and synchronized | PASS: `64f436f705caae5c65800865e7abd1bb0081ab3c`. |
| Accepted ATLAS-036/037/038 ancestry and repository integrity | PASS. |
| Project data, acceptance evidence, source, and original archive preserved | PASS. |
| Planning scope | Maintenance record and its README index only; accepted milestone/ADR decisions unchanged. |

Planning publication is explicitly authorized by the final closeout instruction. The existing
remote was fetched and verified at `dc03631f346193dcc737fa4ebc0bb9e91877d0ff`, an ancestor of
the maintenance commits. Publication uses a normal push to existing `main`, with another
advertised-tip check immediately before pushing and fetched local/remote SHA equality afterward.
No force push, new product milestone, or ATLAS-039 implementation is part of this closeout.
