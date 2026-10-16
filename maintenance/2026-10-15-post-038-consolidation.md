# Atlas post-ATLAS-038 repository consolidation

- Recorded: 2026-10-15 (America/New_York).
- Type: repository maintenance; not a new product milestone.
- Disposition: **PARTIAL — archive backup and hosted dependency verification pending**.
- Authorization: human instruction “ATLAS — Final Repository Consolidation and Production Baseline,” following the authorized Pass 1 branch cleanup.
- Implementation baseline: `64f436f705caae5c65800865e7abd1bb0081ab3c`, unchanged on local and advertised remote `main`.
- Planning baseline before this record: `dc03631f346193dcc737fa4ebc0bb9e91877d0ff`, clean and synchronized with advertised remote `main`.
- Planning checkpoint: the commit introducing this record; identify with `git log -1 --format=%H -- maintenance/2026-10-15-post-038-consolidation.md`. This checkpoint is local only; publication is not authorized by this maintenance instruction.
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

## Remaining local references and worktrees

| Local branch | Tip | Disposition |
|---|---|---|
| main | 64f436f705caae5c65800865e7abd1bb0081ab3c | Accepted production baseline. |
| architecture/atlas-knowledge-synthesis | bc66ebcc11c8fa18f5dc0bffb7e6ea3ac8f29b38 | Three unique historical experiment commits; archive verified, independent backup pending; branch retained. |
| docs/aria-knowledge-synthesis | dfbfcc87011f451f9da564bf01b7b3c1ae45e3b9 | One unique historical documentation/export commit; archive verified, independent backup pending; branch retained. |

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

**Independent-copy gate remains open.** No approved independent storage destination has been
provided or verified. A second local folder on the same disk is not claimed as a durable backup.
Both experimental branch refs and both stashes therefore remain intact. Copy the complete archive
to approved independent storage, verify its checksums and recovery, and record that location before
retiring the remaining historical refs.

## Stash reconciliation

| Stash identity | Findings | Disposition |
|---|---|---|
| 579c2608f2b1bba6aed9c4417fa1a9968926dc63 | No tracked edits. Its 2,322,747-byte compressed sidecar is byte-identical to accepted main:docs/audits/atlas-021/sidecar.json.gz. Full stash object history is also bundled. | Retained pending independent archive backup. |
| a0e5dc3e24a64af8f1fea59e860c8a311debf650 | Modified docs/aria/README.md and docs/aria/ShapeNetwork.md, plus untracked docs/aria/api/ShapeNetwork.md and docs/aria/guides/shape-networks.md. All four content hashes verified after bundle recovery. | Retained pending independent archive backup; never applied to production. |

Sidecar SHA-256: `cd98dcdfa8dcfd8aba8a6d9b1d42f46f0cae8dcf27ba556d8180bf71741cbbd5`.

Bundle refs are `refs/archive/stashes/evidence-sidecar` and `refs/archive/stashes/aria-docs`.
Identify stashes by commit IDs when resuming, because positional indices can change.

## Remote branches and hosted verification

All nine advertised branch tips still match the prior audit and local remote-tracking refs.
All eight historical tips are ancestors of both accepted local `main` and `origin/main`.

| Remote branch | Advertised tip |
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

GitHub verification found:

- Default branch: `main`; Pages disabled.
- No open pull requests; no GitHub Actions workflow runs.
- No `.github/workflows` files in any of the nine branch-tip trees.
- Branch-list API reports all candidates unprotected.
- Detailed branch-protection API returns 403, “Resource not accessible by integration.”
- Ruleset API returns 403, “Upgrade to GitHub Pro or make this repository public to enable this feature.”
- The connector does not support the workflow-definition, deployment, or webhook endpoints.
- GitHub CLI is not installed. The already-installed browser automation interface was tried read-only:
  the Atlas branch-settings page returned “Page not found,” with “Sign in” visible. The temporary
  browser tab was closed. No sign-in, credential retrieval, or settings changes were attempted.

The unavailable detail does not establish an active restriction. It also does not satisfy the
human-required dependency verification gate. **All eight historical remote deletions remain blocked**;
no remote branch was deleted and no stale tracking ref required pruning.

Shortest administrator follow-up: in SkipperPrime/atlas, inspect Settings → Branches,
Rules → Rulesets, Environments, Pages, and Webhooks; confirm no protection/rule, deployment,
webhook, or external automation requires any of the eight historical branch names in the table.
Confirm external CI dependencies with their owner where applicable. Provide that confirmation;
then revalidate current tips, PRs/default branch and ancestry before authorized deletion. Do not
change protections or credentials to force deletion through.

## Integrity and preservation

- `git fsck --full --no-dangling`: exit 0, no diagnostics, in both repositories.
- Accepted ATLAS-036 `6096d0a786029fcfd7af85d725e8544c3ce4a7bf`,
  ATLAS-037 `da47e71f3bac50a61f8c597dfb4358793ed27103`, and ATLAS-038
  `64f436f705caae5c65800865e7abd1bb0081ab3c` remain reachable from implementation main.
- Implementation main, all accepted implementation files/ADRs, and remote refs are unchanged.
- Protected experimental refs and both stash commits, parents, and content-tree IDs remain unchanged.
- Before/after file-metadata inventories cover implementation `.atlas-projects`,
  `docs/audits`, and the entire `/Users/tim/Documents/Atlas Projects/Aria Human Review`
  directory, including acceptance evidence: paths, modes, sizes, and modification times unchanged.
  This is metadata preservation verification, not a new media-render acceptance run.
- Implementation remains clean; planning changes are limited to this maintenance record and its
  README index entry. No product tests/builds were rerun for reference/archive/documentation work.
- No HTTP tracing, credential changes, history rewriting, garbage collection, project-data
  deletion, or ATLAS-039 implementation occurred.

## Remaining acceptance gates

1. Provide and verify an independent archive copy; then retire the two historical branches and stashes.
2. Obtain administrator hosted-dependency confirmation; then delete the eight historical remote refs
   and prune only stale refs resulting from those deletions.
3. Reverify main, ancestry, preservation, refs, and repository integrity; update this record with the
   achieved final inventory.
4. Planning publication remains a separate authorization boundary.

The requested one-local-branch, one-remote-branch, zero-stash target has **not** yet been reached.
