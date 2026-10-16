# Atlas Forward Roadmap

This roadmap starts after ATLAS-037. Statuses describe planning readiness, not implementation
authorization. ATLAS-039 is narrowly scoped to the Maya + Aria layout round trip. It must not delay
or absorb the remaining Movie priorities: Bumper, Slate, Audio, and final end-to-end Movie
acceptance. ATLAS-040 retains its existing Performance & Optimization candidate assignment.

## ATLAS-038 — Movie Synthesis & Tutorial Companion Movies

**Status: Accepted / Closed (2026-10-15).** Slices 038A → 038B → 038C and the authorized corrective pass are accepted and integrated into published Atlas `main` / `origin/main`. Implementation checkpoint: `ac230c7c960d3e1f61ec70556c470096d2b2514d`; accepted, published closeout checkpoint: `64f436f705caae5c65800865e7abd1bb0081ab3c`. Subsequent repository consolidation is [complete](../maintenance/2026-10-15-post-038-consolidation.md).
See [ATLAS-038](../milestones/ATLAS-038.md) for scope, slices, dependencies, boundaries, and
acceptance criteria.

## ATLAS-039 — Application Layout Providers & Project Layout Presets

**Status: Proposed; planning only.** Establish the minimal Maya + Aria provider, Project-owned
Layout Presets, capture/authoring, explicit independent application, and Movie execution point.
See [ATLAS-039](../milestones/ATLAS-039.md),
[ADR-0065](../decisions/0065-application-layout-providers-and-project-layout-presets.md), and the
discoverable [deferred capabilities register](../decisions/0066-application-layout-deferred-authoring-providers-and-automation.md).

After 039 closes, continue with the remaining Movie priorities. Their milestone identifiers remain
unassigned until a later planning decision; do not assign them ATLAS-040, which remains Performance
& Optimization.

The earlier [proposed recording-consistency scope](https://github.com/SkipperPrime/atlas-planning/blob/acecf77cd4cb9bbd54658117e67e0c411bdbed6c/roadmap/Atlas_Forward_Roadmap.md) is retained in history. Its broader provider/editor/restoration proposals are deferred under ADR-0066; the accepted ADR-0065 governs current scope and explicit application semantics. Broader Aria 2.0 content-production refinements remain deferred, unnumbered candidate work.

## ATLAS-040 — Performance & Optimization

**Status: Provisional.** Focus on project opening, harvesting, Knowledge/Tutorial/Movie loading,
synthesis context preparation, and Projection responsiveness. Use measured production workloads
to prioritize changes; this is not an authorization for a broad architecture redesign.

## Future directions — unnumbered

- Atlas setup, design, and implementation workflow.
- Atlas-native LLM integration and provider experience.
- Broader Knowledge and publication refinements not essential to the initial Aria 2.0 launch.

These directions have no milestone number, dependency, or implementation authorization yet.
