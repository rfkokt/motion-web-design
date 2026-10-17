---
name: motion-web-design
description: Design, implement, or audit purposeful website motion including scroll storytelling, kinetic typography, SVG paths, pinned horizontal sections, media reveals, and interactive physics. Use for animation-rich websites, motion references, or improving and testing web animation. Adapt to the existing stack and product; do not impose elaborate effects on ordinary static pages. Excludes standalone video production and native app animation.
---

# Web Motion Design

Build a readable, usable website whose motion explains hierarchy, relationships, or progress. Transfer choreography from references into an original design; preserve the site's content, identity, and established architecture.

## Workflow

1. **Understand the brief and baseline.** Inspect the existing site, stack, assets, audience, and controls. Keep semantic content, links, and navigation usable before animation initializes. When analyzing a reference, separate observed behavior, delivered code, and inference. Never claim an effect was tested from source inspection alone.
2. **Plan the scenes.** Describe each major scene's purpose, trigger, animated properties, duration or scroll range, responsive behavior, and fallback. Prefer a coherent visual motif and a few meaningful transitions. Do not require physics, smooth scrolling, or a particular library.
3. **Choose the rendering technique.** Read [motion patterns](references/motion-patterns.md) for the decision matrix and recipes. Reuse existing dependencies when appropriate. Treat video, Lottie, SVG, DOM, canvas, and WebGL as different tools with different costs.
4. **Implement one scene end to end.** Establish the semantic/static state first, then enhance it. Verify geometry after relevant fonts and media are ready. Support reverse scrolling, repeated activation, resize, breakpoint changes, and route teardown. Give each scene explicit ownership of animations, event listeners, observers, and render loops.
5. **Add responsive and accessible alternatives.** Respect the OS reduced-motion preference and any existing user override. Keep essential information visible. Replace desktop pinning with native flow or swipe when space is limited. Keep keyboard navigation, focus, and scroll behavior predictable.
6. **Verify before reporting.** Use [verification](references/verification.md). Test user-visible outcomes rather than merely successful automation commands. Fix reproducible defects within the authorized scope, then rerun affected checks. State unavailable browsers, devices, or measurements clearly.

## Working rules

- Animate transforms and opacity where suitable. Avoid layout measurement inside every frame; cache dimensions and refresh when layout changes.
- Add optional smooth scrolling only after native scrolling works. Synchronize its clock; avoid competing scroll controllers.
- Load heavy scenes/media when needed, reserve asset dimensions, and pause inactive work. Do not invent performance numbers.
- Avoid essential content hidden until JavaScript runs. Expose enhancement-only controls only after their functionality is ready.
- Do not copy proprietary reference assets, branding, or paid fonts. Use original, user-provided, or appropriately licensed assets.
- Follow the user's publishing intent and the active hosting workflow. This skill grants no extra permission to publish or change access.

For evidence and transferable lessons behind this skill, read [the reference study](references/reference-study.md) when analyzing a similar reference. It is not a required technology stack.

When delivering work, explain the resulting behavior, relevant verification, and remaining limitations. Keep internal library details out of product UI unless they help its users.
