# Reference study and transfer boundaries

This skill was distilled from inspection of [Motion by Zajno](https://motion.zajno.com/) and implementation/QA of an original portfolio in October 2026. These are observations of that captured version, not a promise about the current site or a required recipe.

## Delivered reference evidence

The delivered reference combined a Webflow/jQuery foundation with GSAP scroll/path utilities, Lenis, Splide, Matter, Lottie, inline SVG, and HTML video. DOM/SVG handled typography and paths; media carried some complex showcase visuals; physics supported manipulable objects. Delivered dependencies establish availability, not proof that every dependency executed in every scene.

Observed/reconstructed mechanisms included a marker moving along an SVG route, a pinned section translating a horizontal track, and circular media reveals. Transferable ideas are timeline composition, measured geometry, responsive alternatives, asset preparation, and playback lifecycle. Another stack can implement similar behavior.

## Lessons from implementation and testing

- Font loading changes chip geometry. Early physics measurements can mismatch visible labels and collision shapes.
- Static scrolling must be the default. Pin-only styles applied before the library initializes can make cards inaccessible when the vendor fails.
- Repeated toggles exercise cleanup. Own triggers, observers, handlers, and loops; late readiness callbacks must not resurrect disposed instances.
- Motion-off must account for CSS smooth scrolling as well as JavaScript animation.
- Desktop choreography needs a deliberate mobile layout. Large headline drama does not excuse unreadable metadata or tiny controls.
- Automation needs application readiness. A capture before deferred scripts executed was inconclusive; a rerun with explicit load and scene readiness exercised the intended behavior.

These are failure modes to consider, not a demand to add physics, a toggle, or pinning to every site. Choose techniques that serve the new brief.

## Example requests and intended scope

- “Use $motion-web-design to create a portfolio with one scroll-driven SVG scene and a simple mobile version.” Plan, implement, and verify; do not copy branding.
- “Use $motion-web-design to fix animation that breaks after resize.” Inspect ownership and measurements; repair the defect without a wholesale redesign.
- “Use $motion-web-design to audit this landing page.” Report observed defects and evidence; an audit alone does not authorize changes or publication.
- “Make this contact form clearer.” Use ordinary interface design unless motion meaningfully helps; elaborate scroll scenes are outside the need.
