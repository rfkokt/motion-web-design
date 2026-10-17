# Motion patterns

## Choose the smallest adequate rendering system

| Need | Useful starting point | Main cost or constraint |
| --- | --- | --- |
| Hover, focus, simple state changes | CSS transitions or Web Animations | Preserve keyboard state and interruption behavior |
| Coordinated DOM/SVG sequences and scroll choreography | Existing timeline library; GSAP is one option | Own triggers, cleanup, responsive measurements |
| A marker following a drawn route | SVG path and a timeline/path utility | Compatible path and marker coordinates |
| Authored vector illustration | Lottie or a lightweight SVG sequence | Asset complexity, renderer size, playback lifecycle |
| Rich showcase without live geometry | Authored video | Download/decode cost, poster, playback controls |
| Objects the user can push or collide | Canvas/DOM with a physics engine such as Matter | Input, bounds, measurement, cleanup and CPU cost |
| Real-time depth, lighting or manipulable 3D | WebGL, when justified | GPU/memory budget, loading, accessible fallback |

A complex-looking scene need not use WebGL. A video reveal or SVG composition may deliver the intended result more simply. Avoid adding several libraries for overlapping responsibilities.

## Scroll as a timeline

Define normalized scene progress as `clamp((scroll - start) / (end - start), 0, 1)`, guarding a zero-length range. Map that progress to the scene state. Scrubbed motion usually needs linear progress; smoothing introduces lag and must be deliberate.

Specify entry, active, exit, and reverse-entry behavior. A down-scroll demonstration does not establish that the scene reverses correctly. Keep reading order coherent independently of the choreography.

Measure once necessary layout inputs are available. Refresh when fonts, images, containers, or breakpoints change. Do not use arbitrary delays as the primary readiness mechanism.

## SVG route and kinetic type

Keep the route and marker in one SVG coordinate system where possible. If the marker lives elsewhere, account for viewBox scaling and element transforms. Center its anchor on the path; decide whether path rotation is appropriate.

Use sections of the route timeline to reveal short words or accent a headline. Keep a semantic heading. Hide decorative duplicate letters from assistive technology, avoiding repeated spoken text. Reduced motion should expose the readable final composition.

## Pinned horizontal sequence

Use a viewport wrapper and a wider track. Travel distance is:

`travel = max(0, track.scrollWidth - viewport.clientWidth)`

Translate the track from zero to negative travel during the pinned range. Base duration on content and reading pace, not an unexplained fixed distance. Refresh when content or viewport dimensions change. Skip pinning if travel is zero.

Start with a native horizontal scroller or stacked layout that works without enhancement. Add the pin-specific class only when ready. On teardown, remove owned triggers, spacers, transforms, and classes. Keep one active scene per mounted instance. Do not globally kill other components' triggers.

For narrow screens, native swipe or vertical flow is often clearer. Every card must be keyboard reachable and visible when focused. Distinguish intentional track overflow from unintended page overflow. Chapter counters must reflect track position, including after mode switches.

## Circular media reveal

Animate a clipping shape around its focal point. For a target rectangle of width `w`, height `h` and center `(cx, cy)`, a covering radius in the same coordinate units is:

`r = max(hypot(cx, cy), hypot(w-cx, cy), hypot(cx, h-cy), hypot(w-cx, h-cy))`

Convert units correctly when using percentages, whose reference geometry may differ. Recalculate on resize and inspect every corner. Keep a visible poster/static state while media loads.

Play video only while useful. Decide whether reverse entry resumes or restarts it. Handle rejected play requests, pause on exit/background, and avoid surprise audio. Supply controls or a suitable reduced-motion alternative for continuous movement.

## Physics chips or playground

Use physics when manipulating objects is part of the experience. Offer the same labels and destinations in a static layout. Keep essential navigation outside drag-only interactions.

Wait for relevant fonts before calculating bodies. Use current rendered chip dimensions for body size; cache dimensions for drawing. Observe size changes and resize/scale bodies or rebuild deliberately. Recalculate bounds after container resize.

Prevent late asynchronous initialization from reviving a disposed scene: use an instance/generation token, check it after awaited readiness, and invalidate it on teardown. Avoid duplicate input handlers or loops on toggles.

Release pointer capture on cancel and cleanup. Keep touch scrolling usable. Pause simulation/rendering offscreen or when the document is hidden, and stop loops/listeners/observers when disabled. Hide physics-only controls such as “stir” until their handlers are ready.

## Smooth scrolling and lifecycle

Native scrolling is the baseline. Integrate an optional smooth-scroll controller with the chosen animation clock according to the installed version's official documentation. Avoid unsynchronized duplicate clocks. Verify anchors, keyboard scrolling, focus, mobile behavior, and history.

Motion-off should address CSS smooth scrolling and any custom scroller, not merely visible timelines. Determine how an explicit user setting interacts with the OS preference; preserve the site's established policy.

Treat scenes as owned resources: initialize, measure, pause/resume, dispose. Disposal covers animations, observers, handlers, pointer state, media, render loops, and engines. Route changes, responsive switches, and repeated toggles are normal lifecycle events.
