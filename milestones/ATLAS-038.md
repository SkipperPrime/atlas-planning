# ATLAS-038 — Movie Synthesis & Tutorial Companion Movies

**Status:** Accepted / Closed
**Authorization:** Human-authorized implementation in the ATLAS-038 Authorization and Implementation Kickoff instruction; scope fixed by planning commit `419dae60ceb24137d0535a01926c2266c2355680`.
**Verified baseline:** Atlas `main` at `d15cce1f7ac7b166f320c8db2bd44d5ea00c946c`.
**Source implementation branch:** `feature/atlas-038-movie-synthesis` (fully integrated; historical branch reference subsequently retired during post-038 consolidation).
**Implementation integration checkpoint:** Atlas `main` at `ac230c7c960d3e1f61ec70556c470096d2b2514d`.
**Atlas closeout checkpoint:** `64f436f705caae5c65800865e7abd1bb0081ab3c`.
**Atlas remote publication:** Published to `origin/main`; verified checkpoint
`64f436f705caae5c65800865e7abd1bb0081ab3c` (2026-10-15).
**Acceptance:** Human accepted 2026-10-15; closed after verification and integration.
**Effort target:** Approximately one development day, subject to reuse of existing infrastructure.
**Dependencies:** Existing provider-neutral synthesis/candidate lifecycle; canonical Movie and
Tutorial authorities; existing Task/Scenario and project Application Launch Profile models;
existing Movie runtime. Confirm exact source interfaces during implementation planning.

## Objective

Extend Atlas’s established synthesis and Tutorial editorial workflows to create reviewable,
canonical structured Movies, including companion Movies derived from Tutorial-authored annotation
candidates. The LLM returns a structured Movie object, never pixels or generated video. Accepted
Movies continue through the existing execution, composition, and rendering runtime.

## 038A — Structured LLM Movie Synthesis

Extend the provider-neutral synthesis pipeline to return canonical structured Movie candidates.
Reuse context selection, provider dispatch, validation, candidate review, acceptance, and revision
mechanisms. A candidate is inspectable and editable and may reference supported canonical Task
and Scenario uses, annotations, callouts/highlights, composition/presentation properties, source
references, and provenance. Preserve stable identities and current Movie validation rules.

Acceptance: one LLM-produced Movie candidate is admitted through the shared provider path, reviewed
and edited in its component structure, and accepted as a new canonical Movie revision with source
provenance. No provider produces video or image pixels.

## 038B — Tutorial Annotation Candidates

Extend the shared Tutorial editor so an author can mark selected prose as an annotation candidate.
The mark is Tutorial editorial data with stable identity, source provenance, and association to
the relevant prose; it survives save, reload, and revision and can be edited or removed. Marking
text does not create a timed rendered annotation. Movie timing, screen geometry, and presentation
remain Movie-owned properties.

Acceptance: mark prose, save/reload it across a Tutorial revision, verify stable identity and
association, edit and remove the mark, and confirm ordinary prose remains unchanged when unmarked.

## 038C — Tutorial Companion Movie Generation

Generate a structured companion Movie from an existing Tutorial by composing its Task/Scenario
uses, selected marked annotation prose, referenced project Application Launch Profiles, and
existing launch/open-scene or working-document Tasks with appropriate Movie presentation
components. Use generic project-level launch configuration for applications such as Maya, Nuke,
and Mari. Use the established Maya/Aria project for live acceptance. Do not duplicate launch
definitions or introduce arbitrary executable startup code.

Preserve source Tutorial identity and revision; consumed annotation candidate identities;
Task/Scenario references and relevant effective values; launch/setup references; and independent
Movie identity and revision history. Detect when relevant Tutorial or dependency changes make a
companion Movie out of sync. Offer regeneration as a reviewable new Movie revision; preserve prior
accepted revisions and authored edits. Never automatically overwrite an accepted Movie.

Acceptance: generate and review a companion Movie from a prose Tutorial containing Tasks and
Scenarios; verify approved launch setup reuse; change a consumed Tutorial/dependency and observe
out-of-sync state; regenerate to a new reviewable revision; confirm prior accepted revisions and
editorial changes remain; execute and render the accepted revision through the existing Movie
runtime.

## Shared constraints and exclusions

- Reuse the existing provider-neutral synthesis, candidate review/acceptance, Tutorial editor,
  Application Launch Profile, revision, and Movie execution/rendering pipelines.
- Do not create a Movie-specific synthesis architecture, redesign Movie Studio, introduce video
  generation, duplicate application launch configuration, or generalize beyond the three slices.
- Do not automatically accept, overwrite, or regenerate canonical Movies.
- Trace inputs and consumed source revisions sufficiently to determine companion out-of-sync
  state; keep Movie identity/revision independent from Tutorial identity/revision.

## Verification and authorization boundary

Required acceptance evidence:

1. An LLM-generated structured Movie candidate, inspected and edited before acceptance.
2. Persistent Tutorial annotation candidates with save/reload/revision/edit/remove proof.
3. A companion Movie generated from Tutorial prose plus Task/Scenario uses and approved launch setup.
4. Dependency-aware out-of-sync detection and regeneration into a new reviewable revision.
5. Existing Movie runtime execution and rendering of the accepted result.
6. Preservation checks for prior Movie revisions, Tutorial content, source Task/Scenario data, and
   project launch configuration.

The kickoff authorizes sequential implementation of 038A, 038B, and 038C on the branch above.
Use focused contract, persistence, editor, dependency/revision, and host tests; typecheck and build;
then demonstrate provider synthesis and the Maya/Aria execution/render path. Preserve original
source data and accepted Movies. Link applicable technical ADRs rather than creating a planning duplicate:
ADR-0014/0015 (evidence and media runtime), ADR-0018/0019 (Tutorial source and views), ADR-0021
(Task/Scenario reuse), ADR-0025/0026 (Tutorial and embedded authored content), ADR-0028/0029
(Movie components and execution), ADR-0059 (application operations), ADR-0060 (Tutorial lifecycle),
and ADR-0064 (independent authored Movies and reviewed relations).

## Implementation start

Authorization was recorded in planning commit `07b25728b6f08cc280e23852071245d6b6e98270`.
Implementation begins on `feature/atlas-038-movie-synthesis` from verified main
`d15cce1f7ac7b166f320c8db2bd44d5ea00c946c`. The existing instructional synthesis
contract, shared prose editor, Movie registry/revision boundary and execution runtime
are the reuse points. Human acceptance remains pending.


## Implementation checkpoints and verification — 2026-10-15 (pre-closeout snapshot)

At the time this verification snapshot was recorded, the three authorized slices were implemented
on `feature/atlas-038-movie-synthesis`, with human acceptance and integration still pending. The
subsequent acceptance and integration outcome is recorded in the closeout section below.

| Checkpoint | Implementation SHA |
| --- | --- |
| 038A — shared structured Movie synthesis | `561e263f442f6dc0793434be37dab6246eafdc85` |
| 038B — persistent Tutorial annotation marks | `d53c0ffea16c7321ba5e352faa9f1785dece0a2b` |
| 038C — companion provenance and reviewed regeneration | `d9c3476718cc8022a48b63822329bc09074ff444` |
| Live verification and evidence | `6f5c58213e5ded0704e4d55f482b7690d13a3e5c` |

Canonical technical evidence remains in the implementation repository:
[`docs/audits/ATLAS-038-MOVIE-SYNTHESIS.md`](https://github.com/SkipperPrime/atlas/blob/64f436f705caae5c65800865e7abd1bb0081ab3c/docs/audits/ATLAS-038-MOVIE-SYNTHESIS.md).
The immutable implementation checkpoint above identifies the historical verification snapshot. ADR-0026 and ADR-0064 amendments describe the bounded
editorial-mark and companion provenance extensions without duplicating technical authority here.

Verified results:
- The existing configured Codex provider returned a structured Movie candidate. Studio reopened,
  edited and explicitly accepted it through the existing guarded Movie save boundary.
- Browser-selected Tutorial prose was marked, saved and reloaded with stable identity. A guarded
  Tutorial revision edited the prose while preserving the mark and original-text provenance.
  Browser removal left prose intact; Cancel retained the saved mark. Automated persistence tests
  additionally verify saved removal and reload.
- A companion Movie reused 12 existing Task occurrences and one Scenario, including the approved
  Maya/Aria launch profile. Source changes produced an out-of-sync state. Reviewed regeneration
  created another Movie revision, preserving the entire first accepted revision and authored title.
- The existing runtime completed all 13 steps, retained a native 3840 × 1600 capture, and rendered
  the accepted composition at 30 fps (394 frames, 13.133333 seconds). Browser playback and seeking
  passed; the host reports current artifact and companion-source states.
- All nine original Movies, five original Tutorials, the first companion revision, and 14 preflight
  file hashes remained unchanged, including source Tasks/Scenarios, approved launch configuration
  and prior media. New acceptance products and evidence are project-owned additions.
- 324 focused tests across 17 files, TypeScript check and production build passed. The final
  persistence-test extension passed all 19 tests in the focused derivation file. Independent review
  findings were fixed and rechecked; whitespace checks passed.

Qualifications and remaining review:
- A broad Aria synthesis request exceeded the existing exposure cap; a narrower canonical subject
  succeeded. The cap was preserved.
- The first live execution failed native window matching at Start Recording and cleaned up without
  a finalized capture. An isolated retry succeeded with the unchanged runtime and profile. The
  exact transient matching condition is not established; both receipts are retained in the audit.
- Large-project preparation remains slow and the build retains its existing large-chunk warning.
  No ATLAS-040 optimization work was undertaken.
- No blocking implementation issue remains in the exercised path. Human review and acceptance,
  implementation publication/merge, and eventual closeout remain separate authorization gates.

ATLAS-039 and ATLAS-040 remain Provisional. No development in either milestone is authorized here.

## Human acceptance and closeout — 2026-10-15

Human acceptance is recorded for 038A, 038B, 038C, and the subsequent Studio lifecycle, Tutorial
reader, capture-free Movie, and companion annotation-default corrections. The authoritative
implementation audit is [ATLAS-038-MOVIE-SYNTHESIS](https://github.com/SkipperPrime/atlas/blob/main/docs/audits/ATLAS-038-MOVIE-SYNTHESIS.md).

The implementation branch was fast-forwarded into Atlas `main` from
`d15cce1f7ac7b166f320c8db2bd44d5ea00c946c` to code checkpoint
`ac230c7c960d3e1f61ec70556c470096d2b2514d`. The audit closeout is recorded at
`64f436f705caae5c65800865e7abd1bb0081ab3c`; ATLAS-036 and ATLAS-037 accepted checkpoints remain
ancestors. Atlas `main` was published to `origin/main` by a normal fast-forward push using temporary
HTTP/1.1 and a 5 MiB post buffer. A subsequent fetch verified local and remote `main` both at
`64f436f705caae5c65800865e7abd1bb0081ab3c`. The source branch is retained for later cleanup
review.

Final post-integration verification passed 265 focused tests across 23 files, `npm run check`,
`npm run build`, and `git diff --check` using Node 24.13.0. The production build retains its known
large-chunk warning. Real provider synthesis, Studio review/edit/acceptance, persistent Tutorial
annotations, companion Movie regeneration, 13-step Maya/Aria execution, native 3840 × 1600 capture,
30 fps rendering, playback, fullscreen, tab navigation, and preservation checks are documented in
the implementation audit. No Maya execution was repeated for closeout.

The existing `tests/studio-project-switching.test.ts` baseline remains 16/19: the Tutorial hash
expectation retains `tutorialId`; the Knowledge-render test has an unmocked Knowledge-generation
read and serializes a React tree rather than matching rendered text; the empty-project test expects
the obsolete `studio-product-workspace` class and has the same missing request mock. All three
failures reproduce from pre-correction checkpoint `6f5c58213e5ded0704e4d55f482b7690d13a3e5c` and
are deferred for independent fixture/expectation maintenance. They do not reproduce in the accepted
real-Aria navigation flow.

Deferred work: Application Layout Presets; project-level Movie Presentation Settings; bumpers,
slates, narration, audio tracks, and mixing; initial Project-opening and large-project preparation
performance; and the three baseline switching-test follow-ups. ATLAS-039 and ATLAS-040 remain
Provisional and unauthorized.

## Post-closeout repository housekeeping — 2026-10-15

The separately authorized [post-038 consolidation](../maintenance/2026-10-15-post-038-consolidation.md) retired the fully integrated `feature/atlas-038-movie-synthesis` branch reference along with other obsolete local and remote branches. Atlas `main` / `origin/main` remain at the accepted checkpoint `64f436f705caae5c65800865e7abd1bb0081ab3c`. This administrative update does not change acceptance, implementation evidence, or the dated pre-closeout snapshots above. ATLAS-039 remains proposed and unauthorized for implementation.
