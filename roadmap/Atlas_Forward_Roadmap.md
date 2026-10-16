# Atlas Forward Roadmap

This roadmap starts after ATLAS-037. Statuses describe planning readiness, not implementation
authorization. ExoTools website and Aria 2.0 launch work takes priority over noncritical Atlas
refinement; ATLAS-039 and ATLAS-040 are not launch prerequisites unless production evidence
establishes a blocker.

## ATLAS-038 — Movie Synthesis & Tutorial Companion Movies

**Status: Accepted / Closed (2026-10-15).** Slices 038A → 038B → 038C and the authorized corrective pass are accepted and integrated into published Atlas `main` / `origin/main`. Implementation checkpoint: `ac230c7c960d3e1f61ec70556c470096d2b2514d`; accepted, published closeout checkpoint: `64f436f705caae5c65800865e7abd1bb0081ab3c`. Subsequent repository consolidation is [complete](../maintenance/2026-10-15-post-038-consolidation.md).
See [ATLAS-038](../milestones/ATLAS-038.md) for scope, slices, dependencies, boundaries, and
acceptance criteria.

## ATLAS-039 — Application Layout Presets & Recording Consistency

**Status: Proposed — planning review only; implementation not authorized.** Define reusable Project-level Application Layout Presets for predictable Movie execution and capture. Reuse existing Application Launch Profiles without duplicating startup configuration. Atlas owns generic layout lifecycle and preset selection; approved application providers and extensions declare supported layout capabilities, property editors, apply/inspect/verify/restore operations, and validated user-configurable properties. Maya 2025 with Aria 2.0 is the initial acceptance environment, not a hardcoded product boundary; other applications may expose distinct capabilities. Include Launch Profile defaults, Movie-specific overrides, readiness verification before recording, and optional restoration. Review infrastructure and the former Aria tutorial harness as a functional reference before authorizing implementation. Defer Movie Presentation Settings, bumper/slate/audio work, general Movie Studio redesign, performance optimization, and hosting/credential migrations.

The broader Aria 2.0 content-production refinements previously listed under ATLAS-039 remain deferred, unnumbered candidate work; they are not silently included in this milestone.

## ATLAS-040 — Performance & Optimization

**Status: Provisional.** Focus on project opening, harvesting, Knowledge/Tutorial/Movie loading,
synthesis context preparation, and Projection responsiveness. Use measured production workloads
to prioritize changes; this is not an authorization for a broad architecture redesign.

## Future directions — unnumbered

- Atlas setup, design, and implementation workflow.
- Atlas-native LLM integration and provider experience.
- Broader Knowledge and publication refinements not essential to the initial Aria 2.0 launch.

These directions have no milestone number, dependency, or implementation authorization yet.
