# ATLAS-038 — Movie Synthesis & Tutorial Companion Movies

**Status:** Proposed — ready for milestone review
**Authorization:** Planning only. Implementation requires separate explicit authorization.
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

Identify an implementation branch and a bounded focused test plan during the implementation
authorization review. Link applicable technical ADRs rather than creating a planning duplicate:
ADR-0014/0015 (evidence and media runtime), ADR-0018/0019 (Tutorial source and views), ADR-0021
(Task/Scenario reuse), ADR-0025/0026 (Tutorial and embedded authored content), ADR-0028/0029
(Movie components and execution), ADR-0059 (application operations), ADR-0060 (Tutorial lifecycle),
and ADR-0064 (independent authored Movies and reviewed relations).
