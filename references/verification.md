# Verify motion as behavior

Use the project's tools and actual target environment. Adapt selectors and assertions to the site. Do not introduce a large test system for a small reversible change unless it provides useful coverage.

## Establish a meaningful test barrier

Navigation completing, a click succeeding, and a component being ready are different events. Wait for document readiness plus a meaningful scene condition: a wired control, enhancement-ready marker, or loaded layout inputs. Use bounded waits and report timeouts honestly. Avoid waiting for perpetual animation to become “network idle.”

On failure, distinguish application defects, fixture defects, and readiness errors. Fix the cause and rerun the affected scenario. Do not count an unexecuted scenario as a pass.

## Practical matrix

| Scenario | What to verify |
| --- | --- |
| Desktop, motion on | Readable scenes, pin start/end, complete travel, reverse scroll, working links |
| Narrow mobile; widths such as 320 and 390 CSS px when relevant | No page overflow, readable labels, usable touch targets, native scroll/swipe, menu open/close |
| Reduced motion | Essential content visible, unnecessary loops/pinning disabled or simplified, navigation intact |
| Manual motion toggle | Correct pressed state and visible result, smooth scrolling addressed, repeated toggles do not accumulate resources |
| Resize/breakpoint switch | Fresh dimensions, no stale transforms/spacers, correct content order and physics bounds |
| Missing optional vendors | Static content/native scrolling survive; unavailable controls hidden or meaningfully disabled |
| No JavaScript, when progressive enhancement is expected | Essential content/links usable; no hidden essential text or visible inert enhancement controls |
| Keyboard | Visible focus, reachable content, anchors, Enter/Space activation, Escape and focus return for dialogs |
| Offscreen/background/route change | Media and loops pause or dispose; returning does not duplicate scenes |

Adapt the matrix to scope. A physics-free page needs no physics test. Test more engines/devices when requested or when a specific compatibility risk warrants it.

## Assert outcomes

For a toggle, assert pressed state **and** resulting behavior. For example: motion-off restores native track overflow, removes the owned pin spacer, and stops the owned simulation; re-enabling creates exactly one applicable enhancement. Repeat cycles to catch accumulation. DOM counts alone do not prove that a render loop stopped; inspect its lifecycle or measure activity when that claim matters.

For a mobile menu, assert that it opens, Escape closes it, a navigation choice closes it and reaches its target, and focus returns sensibly. A successful click does not establish arrival.

Inspect screenshots and DOM bounds. Compare document scroll width with client width; separate track overflow from page overflow. Check first/last cards and clipping corners, not just the hero. Screenshots do not establish keyboard access or animation smoothness.

For media, test slow/blocked assets when relevant: posters and content should remain useful. Check pause/resume and reverse-entry policy. Inspect physics after font loading and container resizing.

## Evidence and reporting

Record URL or build/commit, viewport, motion preference, scenario, result, and material errors. Retain screenshots/structured results when useful, excluding credentials and unnecessary personal data.

Distinguish source review (cleanup exists), runtime checks (an exercised interaction worked), and measurement (a profiler measured resource use). Do not claim an FPS target, Lighthouse score, complete browser coverage, real-device testing, or zero console errors without the corresponding check. State gaps such as untested Safari, rotation, or screen-reader behavior. Summarize meaningful checks rather than dumping logs.
