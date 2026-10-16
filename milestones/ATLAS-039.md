# ATLAS-039 — Application Layout Providers & Project Layout Presets

**Status:** Proposed
**Planning decision:** Accepted in planning commit recorded at closeout
**Authorization:** Planning and architecture only; implementation is not authorized by this record
**Owner/reviewer:** Not assigned
**Implementation branch:** Not started
**Implementation checkpoint:** Not established
**Planning checkpoint:** Recorded by the planning commit
**Dependencies:** Accepted Movie runtime and Project Application Launch Profiles; Maya + Aria
application operation provider; existing application window inspection and capture geometry
**Blockers:** None identified for planning; implementation readiness requires a separate kickoff

## Objective

Enable authors to capture, save, inspect, select, and explicitly reapply a named Project Layout
Preset for Maya + Aria, including at a chosen point in Movie execution, while keeping application
startup, provider behavior, desired layout state, canonical Tasks/Scenarios, and Movie composition
separate.

## Scope and boundaries

Governed by [ADR-0065](../decisions/0065-application-layout-providers-and-project-layout-presets.md).
Broader capabilities are discoverable in
[ADR-0066](../decisions/0066-application-layout-deferred-authoring-providers-and-automation.md).

- An Application Launch Profile defines executable, approved configuration, and associated
  provider. It may display compatible presets. Launch never applies a preset automatically.
- A minimal Atlas-owned provider contract covers inspection, capture, application, and verification;
  the concrete provider is Maya + Aria only.
- A Layout Preset is a named Project resource describing desired layout state, not a Task,
  Scenario, or Launch Profile. Capture creates it from an existing supported arrangement.
- Apply Layout Preset is an explicit meta-operation, available manually/on demand and as a typed
  Movie-owned execution directive at an explicit place in ordered Movie composition. It is not a
  canonical Task or Scenario. Reuse the existing host/runtime execution path.
- Prioritize reliable placement and sizing for supported Maya and Aria windows. Include panel
  arrangement or docking only where existing application mechanisms make it straightforward and
  reliable.
- Do not change scene contents, application documents, or unrelated session state. Report
  unsupported, ambiguous, unavailable, or failed application with actionable diagnostics.
- Exclude other application providers, a generic provider framework, visual layout authoring,
  accessibility/fallback automation, complex application panel control, and advanced portability,
  reconciliation, or restoration. See ADR-0066.
- This plan does not authorize implementation or modify runtime behavior. It does not absorb
  Bumper, Slate, Audio, or final Movie acceptance.

## 039A — Provider and Preset Foundation

Define only the provider contract needed by the vertical slice. Add Project-owned preset
persistence and integrate the Maya + Aria provider with existing application operation/session
authority. Preserve the Launch Profile boundary and compatible preset association.

**Acceptance:** A Maya + Aria preset can be represented and persisted as a validated named Project
resource; the provider exposes inspect, capture, apply, and verify through existing host/runtime
boundaries; launching a compatible profile does not apply the preset.

## 039B — Capture and Authoring

Capture an existing supported Maya + Aria window arrangement. Allow the author to name, save,
select, inspect, and manage presets, and display compatible presets with associated Launch Profiles.

**Acceptance:** A captured arrangement survives Project close/reopen; a compatible profile shows
the preset; unsupported or incompatible state is reported and cannot be represented as a successful
capture.

## 039C — Independent Layout Execution

Add explicit Apply Layout Preset invocation on demand and at a selected point in Movie execution.
Use the existing execution infrastructure and basic state verification; report failures with a
clear cause and affected window where known.

**Acceptance:** Manual apply works independently of application launch. An ordered Movie can launch
Maya, open a scene, open Aria/windows, explicitly apply the preset, and continue later Tasks,
Scenarios, or recording. The meta-operation is absent from canonical Task/Scenario catalogs.

## 039D — End-to-End Acceptance

Demonstrate the complete round trip on the established Maya + Aria project:

1. Launch Maya and open an existing scene.
2. Open Aria and required windows; arrange supported windows.
3. Capture and save a named Layout Preset.
4. Deliberately change the arrangement.
5. Apply the preset independently of launch and verify restored supported layout state.
6. Demonstrate the same preset invoked at the intended point during Movie execution.

**Acceptance:** The saved supported geometry is restored and verified, application documents and
scene contents remain intact, and the independent Movie invocation is evidenced. Any unsupported
panel/docking behavior is explicitly reported and excluded from the accepted preset.

## Acceptance criteria

| Criterion | Required evidence | Status |
|---|---|---|
| Provider and preset foundation respects ownership boundaries | Project persistence readback; Maya + Aria provider operations; launch-without-apply evidence | Not started |
| Capture and authoring persist reusable named presets | Capture/save/reopen/select/manage evidence from an existing arrangement | Not started |
| Explicit application works independently and inside Movie order | Manual apply receipt and Movie execution evidence showing operation at authored position | Not started |
| End-to-end round trip restores supported window layout | Arrange → Capture → Save → Change → Apply → Verify, plus scene/document preservation | Not started |

## Canonical decisions and evidence

- Planning ADRs: [ADR-0065](../decisions/0065-application-layout-providers-and-project-layout-presets.md),
  [ADR-0066](../decisions/0066-application-layout-deferred-authoring-providers-and-automation.md).
- Governing implementation ADRs: Atlas ADR-0029 (built-in Task operation and runtime resolution),
  ADR-0059 (Project-authored application operations and target confirmation), ADR-0064 (Movie
  ownership and execution/presentation boundaries).
- Prior milestone: [ATLAS-038](ATLAS-038.md), Accepted / Closed.
- Verified implementation discovery: summarized in ADR-0065; full repository inspection was against
  Atlas `main` at `64f436f705caae5c65800865e7abd1bb0081ab3c`.
- Implementation branch/checkpoint: Not established.

## Verification and disposition

- Implementation completed: No; planning only.
- Tests documented: Not applicable to this planning pass.
- Freshly verified: Planning references, identifiers, worktree state, and planning diff at closeout.
- Live validated: No; no application code was run or changed.
- Human accepted / other disposition: Planning direction approved in the ATLAS-039 kickoff; later
  implementation acceptance remains separate.
- Deferred work: All capabilities in ADR-0066; Movie Bumper, Slate, Audio, and final end-to-end
  Movie acceptance remain on the forward roadmap after the bounded 039 proof.

## Closeout

This planning-only kickoff closes when its documentation is committed in `atlas-planning`. The
milestone remains Proposed and implementation unauthorized. Record the resulting planning
checkpoint and leave Atlas code, branches, and canonical data untouched.
