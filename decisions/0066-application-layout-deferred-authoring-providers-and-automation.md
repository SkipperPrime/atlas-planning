# ADR-0066: Application Layout System — Deferred Authoring, Providers & Automation

- Status: Accepted deferred-decision record
- Recorded: 2026-10-16
- Governing milestone: [ATLAS-039](../milestones/ATLAS-039.md)
- Bounded architecture: [ADR-0065](0065-application-layout-providers-and-project-layout-presets.md)

## Decision

ATLAS-039 establishes only the minimal provider contract and Project preset lifecycle needed for
reliable Maya + Aria window placement and sizing, explicit application, and basic verification.
The capabilities below remain visible planning items but are excluded from ATLAS-039. No delivery
dates or milestone identifiers are assigned here. A future candidate name is not authorization.

| Deferred capability | Intended value | Why excluded from ATLAS-039 | Likely dependency | Classification and future candidate |
|---|---|---|---|---|
| Photoshop, Nuke, Mari, Houdini, and other DCC providers | Reuse named layouts across production applications. | The Maya + Aria proof must first establish the smallest useful contract; each application has distinct control APIs and reliability limits. | Proven provider contract; application/version-specific discovery and validation. | Planned future enhancement. Candidate: Application Layout Expansion, unnumbered and considered after 039. |
| Third-party provider registration and extensibility | Let external developers integrate applications without Atlas-specific code changes. | No second provider yet proves stable capability discovery, compatibility, or ownership boundaries. | At least one additional first-party provider; versioned provider API and trust model. | Exploratory idea pending evidence from multiple providers. No milestone candidate yet. |
| Interactive drag-and-drop layout editor, workspace preview, and Atlas-side window/panel resizing | Author layouts visually and review them before application. | Capture of a live arrangement is enough for the initial round trip; an editor introduces a separate visual authoring surface and interaction model. | Preset data model; reliable geometry capture; display and application capability metadata. | Planned future enhancement. Candidate: Layout Authoring, unnumbered after the basic preset lifecycle is proven. |
| Monitor-aware visual arrangement and capture/compare workflows | Make layouts understandable and portable across multi-display workstations. | ATLAS-039 validates supported bounds on the target environment without building a monitor composition tool. | Display enumeration, scaling/coordinate policy, and portability semantics. | Planned future enhancement; likely grouped with Layout Authoring. |
| Application-specific panel discovery, docking/undocking, workspace switching, and complex app-owned UI arrangements | Restore richer native workspaces beyond top-level window placement. | These behaviors vary widely and must not compromise scene/document state; include only if Maya + Aria APIs make a specific behavior straightforward and reliable. | Provider-specific API research, state ownership and preservation guarantees. | Planned future enhancement where supported. Candidate: Provider Control Depth, unnumbered after concrete application demand. |
| Accessibility-based UI control and supported fallback interaction automation | Reach application controls that lack stable public APIs. | Fallback automation has application, OS, accessibility, and focus failure modes that are unnecessary for the initial window geometry proof. | Provider capability declaration, consent/trust boundaries, robust observation and diagnostics. | Exploratory idea until an API gap justifies a bounded fallback. No milestone candidate yet. |
| Developer-created providers using a published provider API | Support maintained adapters outside Atlas core. | A public API should follow evidence from a second provider and stable internal contract. | Multiple provider implementations, compatibility/version policy, extension trust and packaging. | Planned future enhancement if provider demand is established; candidate: Provider SDK, unnumbered after provider expansion. |
| Recorded interaction analysis and Atlas-assisted provider development | Reduce effort to discover and maintain app-specific mechanisms. | This is tooling for provider authors, not required by capture/apply. | Provider API, trace format, replayable evidence and safety review. | Exploratory idea; no milestone candidate. |
| LLM-assisted synthesis and validation of application adapters | Accelerate adapter authoring while checking proposed behavior. | Reliability and safety need proven provider contracts and evidence before generative assistance is useful. | Provider API, constrained generation, executable validation and human review. | Exploratory idea; no milestone candidate. |
| Layout difference/reconciliation and conditional application | Explain partial drift and apply only selected changes. | Initial acceptance needs whole-preset apply and basic verification, not policy or merge semantics. | Stable inspectable state model and more than one real provider/preset workflow. | Planned future enhancement if partial updates become necessary; candidate: Layout Reconciliation, unnumbered. |
| Robust state restoration | Return the application to its exact prior state after failure or user cancellation. | ATLAS-039 must avoid unrelated state changes and report failure; comprehensive restoration requires explicit rollback capabilities per provider. | Provider-declared reversible operations and durable before/after evidence. | Planned future enhancement, prioritized if first implementation exposes material restoration gaps; no assigned milestone. |
| Cross-display portability and application-version compatibility | Reuse presets on changed monitors and supported application releases. | The first proof targets one known Maya + Aria environment; cross-environment transforms and compatibility policy are separate contracts. | Display model, provider capability versions, migration/compatibility checks. | Planned future enhancement after one-provider acceptance; candidate: Layout Portability, unnumbered. |
| More sophisticated execution diagnostics | Explain capability mismatch, partial apply, and provider-level recovery. | Basic actionable failures are required now; richer telemetry, histories, and diagnostic presentation need broader usage evidence. | Provider result contract and accumulated execution evidence. | Planned future enhancement as operational evidence justifies it; candidate: Layout Execution Diagnostics, unnumbered. |

## Discovery and review

The verified reuse points and immediate gaps are recorded in ADR-0065 and the ATLAS-039 milestone.
This record is the discoverable planning register for deferred application-layout capabilities.
Future milestone assignment requires a separate roadmap decision based on observed provider,
authoring, portability, or execution needs. Bumper, Slate, Audio, and final end-to-end Movie
acceptance retain priority after the ATLAS-039 Maya + Aria proof.
