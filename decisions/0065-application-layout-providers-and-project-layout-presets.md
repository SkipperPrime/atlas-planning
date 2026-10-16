# ADR-0065: Application Layout Providers and Project Layout Presets

- Status: Accepted planning architecture decision
- Recorded: 2026-10-16
- Scope: ATLAS-039 planning and implementation boundary
- Extends: Atlas ADR-0029, ADR-0059, ADR-0064
- Deferred capabilities: [ADR-0066](0066-application-layout-deferred-authoring-providers-and-automation.md)

## Context

ATLAS-038 closed Movie synthesis and companion-Movie work with Application Launch Profiles and
the Maya + Aria runtime. Authors need a repeatable desired arrangement after launching an
application and opening its working documents. Startup configuration, application-specific window
control, desired layout state, procedural Tasks, and Movie composition have different owners and
must remain distinct. ATLAS-039 is bounded to a Maya + Aria capture/apply proof so the remaining
Bumper, Slate, Audio, and final Movie acceptance work can continue promptly.

## Decision

### Application Launch Profile

An Application Launch Profile defines how an application starts: executable, approved
configuration, and associated application layout provider. It may display compatible Project
Layout Presets. Launching through a profile starts the application only; it never applies a Layout
Preset implicitly.

### Application Layout Provider

Atlas owns a small provider contract and execution orchestration. A provider owns the
application-specific mechanisms to inspect supported layout state, capture it, apply desired
state, and verify the result. Provider capability and compatibility are explicit. ATLAS-039
implements only Maya + Aria; it does not establish a speculative provider framework or implement
other applications.

### Project Layout Preset

A Layout Preset is a named, reusable Project resource describing desired application layout state.
It is not a Task, Scenario, or Launch Profile. An author creates it by capturing an existing
supported arrangement, saves and selects it as a Project resource, associates it with a compatible
Launch Profile/provider, and explicitly executes it. The preset stores desired state; the provider
supplies the means to achieve it. Atlas provides basic inspection and verification of application
results.

### Explicit Apply Layout Preset operation

Applying a preset is an explicit meta-operation that can be invoked on demand or at a selected
point in Movie execution. It is not a canonical Task or Scenario and does not launch the
application. Authors can launch Maya, open a scene, open Aria and required windows, apply the
selected preset, then continue Tasks, Scenarios, or Movie recording.

Inspection of the current Movie model shows that ordered segment units currently admit authored
content, TaskUse, and ScenarioUse; the forward execution planner expands and executes those units
through the existing Movie runtime. ATLAS-039 should represent Apply Layout Preset as a typed,
Movie-owned execution directive in that ordered composition. The directive references a
Project-owned preset and is dispatched through the existing host/runtime execution path. It does
not enter the Task/Scenario catalog or create a second workflow engine. A manual invocation uses
the same provider operation and result contract outside a Movie sequence.

### Capture, application, and safety

The Maya + Aria provider demonstrates the round trip:

**Arrange → Capture → Save → Change Layout → Apply → Verify.**

Use existing Maya and Aria APIs, scripting, and window-management facilities where available;
authors do not write scripts to define a preset. The first implementation prioritizes reliable
placement and sizing of supported Maya and Aria windows. Panel arrangement or docking is included
only if the existing APIs make it straightforward and reliable. Application must not change scene
contents, documents, or unrelated session state. Unsupported, unavailable, or ambiguous state
fails with actionable diagnostics rather than silently claiming success.

## Verified implementation discovery

Discovery was performed read-only against Atlas `main` at `64f436f705caae5c65800865e7abd1bb0081ab3c`.

| Area | Existing reusable infrastructure | ATLAS-039 gap / integration point |
|---|---|---|
| Launch Profiles | `src/runners/application-launch-profile.ts` validates/fingerprints approved profiles; `src/host/application-inventory.ts` reads trusted host configuration; `src/ui/studio/ApplicationSelection.tsx` exposes compatible profiles in launch authoring. | Profiles are host configuration loaded from `ATLAS_APPLICATION_LAUNCH_PROFILES`, not Project resources. Add a compatible provider association and preset discovery display without making launch execute a preset. |
| Launch execution | `task.launch-application` references a profile identity; `src/host/application-operation-host.ts`, `src/runners/aria-maya/application-operations.ts`, and `src/runners/aria-maya/process-bridge.ts` own admission, launch, and session setup. | Reuse the owned application session and provider selection after launch. Layout remains a separately invoked operation. |
| Maya + Aria control | `src/runners/aria-maya/runtime/atlas_aria_runtime/application_operations.py` resolves the owned Maya main window and floating Aria host through application APIs and reports frame geometry; the bridge already opens scenes and Aria windows. `src/runners/aria-maya/runtime/atlas_aria_runtime/visual.py::apply_aria` can float/show and resize the owned Aria host while preserving its current position. | Reuse Aria host sizing where reliable. There is no saved desired geometry, position-setting operation, or Maya main-window placement operation; no general preset capture/apply/verify contract exists. Add only required Maya + Aria operations. |
| Window geometry and displays | Movie recording admits exact owned windows and retains bounds, display origin/scale, native identity, and geometry changes in `src/runners/recording/recorder.swift`, `src/core/movie-capture-evidence.ts`, and Movie runtime evidence. | This is observational capture evidence; it does not persist desired arrangements or move/resize windows. Reuse identity/geometry validation where suitable, with a separate preset model. |
| Project resources | Project persistence patterns exist for Tasks/Scenarios and Movies (`src/project/`, `src/host/movies.ts`). Movies already use Project-owned records and explicit read/write boundaries. | No Project Layout Preset persistence or authoring UI exists. Add a narrowly scoped store and named preset selection/management. |
| Movie composition | `src/core/movie.ts` admits ordered content, TaskUse, and ScenarioUse units; `src/host/generic-movie-runtime.ts` and `src/host/movie-execution-host.ts` validate and execute the flattened sequence. | No meta-operation unit exists. Add a typed Movie-owned directive at the composition boundary and dispatch it through the existing host/runtime. Keep canonical Tasks and Scenarios unchanged. |
| Manual execution | The same host and application-operation runtime is used for forward Task execution and Movie execution. | No standalone Apply Layout Preset invocation or result surface exists. Expose on-demand invocation through the existing application operation host, with basic inspect/verify and failure reporting. Do not route this meta-operation through authored Python Tasks or create a second executor. |

The current Movie runtime requires an authored Launch Application occurrence before application
operations. This decision preserves that startup requirement where applicable while allowing the
layout directive only after the author has launched the application and opened required content.

## Consequences and boundaries

- Launch Profile, Layout Provider, Layout Preset, Apply Layout Preset, Task/Scenario, and Movie
  remain separate authorities.
- Presets are reusable Project resources; they do not duplicate startup configuration or
  procedural instruction.
- Manual and Movie invocation share provider behavior and host orchestration.
- The first acceptance is reliable Maya + Aria window placement/sizing, including independent
  application and an explicit Movie invocation point.
- Broader provider registration, visual layout authoring, advanced application control, and
  automation are deferred in ADR-0066.
- This planning ADR defines approved direction. It does not authorize implementation or modify
  Atlas runtime behavior.

## Acceptance boundary

ATLAS-039 closes after an existing Maya scene and Aria windows can be arranged, captured, saved,
deliberately changed, and restored through independent preset application with verified results,
including invocation at the intended point in Movie execution. Bumper, Slate, Audio, and final
end-to-end Movie acceptance remain subsequent Movie roadmap work.
