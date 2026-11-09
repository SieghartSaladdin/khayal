# Tiru capture: measuring a reference closely enough to imitate it

The Light survey (`research.md`) is enough for the user to react to a reference: fonts, palette, section order. It is not enough to imitate one. Without measured numbers the build drifts to the model's habits and ends up looking nothing like the reference. This file is the second REA pass that fixes that. It runs in workflow step 4 (Lock), after the user has picked a package and before `LAYOUT.md` and `DESIGN.md` are written.

Reply in the user's language. Write the blueprint in English, inside `REFERENCES.md`.

## Scope

- Run it for every reference the chosen package names, without asking the user, but only on the sections the package's section plan takes from that reference. Say in one line which sections will be measured and from which site.
- Capture only those sections, usually one to three per reference: the ones worth borrowing (a hero, a story index, a process, an inquiry drawer). Standard parts of the page (nav, footer, FAQ, plain text blocks) are not captured unless the package takes them from a reference. They are designed from the concept and the measured tokens, and marked `original` in `LAYOUT.md`.
- Choose these sections when writing the proposal (`SKILL.md` step 3): for the product at hand, pick the few sections per reference that suit it, and give the rest of the page to `original`. A page where every section is captured is slower to build and no more faithful.
- Fast mode does not skip it. Only the waiting is skipped.

## Keep it fast

- Measure at 1440px first. Measure 390px only for the captured sections.
- Read the scripts only for sections with meaningful motion (a loader, a canvas, a scroll-linked effect, a drawer). A static section needs only its CSS.
- Search the exported CSS for the selectors of the captured sections instead of reading every file in full.
- Take the global tokens (colors, fonts, type scale, container, spacing steps) once per reference, not once per section.

## How to capture (REA first)

Read each tool's input schema before calling it.

1. **Scrolled captures with `capture_browser_scenario`.** `inspect_web_page` is passive and `capture_web_screenshot` only shows the current viewport, so neither can walk a page. Use `capture_browser_scenario` on the live site, connected to the same browser REA uses (`rea.md`), with actions that scroll to each captured section, wait for its motion to finish, and capture a screenshot plus the DOM and accessibility tree. Run it at 1440x900, then at 390x844 for the captured sections only. Scenario defaults are reduced motion on, which hides the animations being studied, so set motion to no-preference.
2. **Styles from the real stylesheets.** In the same scenario select `capture.network.response_body` so the CSS files come back, and use `inspect_web_page` with `include_script_sources`. Read the CSS for: `:root` custom properties, `@font-face` sources and font stacks, type sizes and line heights, letter-spacing, spacing values, grid and flex templates, container widths, breakpoints, `transition` and `animation` durations and easings, and `@keyframes`.
3. **Motion from the scripts.** `export_web_scripts`, then read the animation code (GSAP timelines, Lenis options, IntersectionObserver reveals) for durations, easings, delays, staggers, triggers, and scroll distances. Use the Deep tracing tools in `rea.md` when a loader, canvas scene, or cursor effect needs to be found in the bundle.
4. **Measured values when REA cannot show them.** REA does not evaluate page JavaScript, so computed values from minified or utility-class CSS may be missing. Then measure in the attached browser: computed font size, weight, line height, letter-spacing, colors, margins, paddings, and bounding boxes of the main elements (devtools `get_css_styles` or `evaluate_script` with `getComputedStyle` and `getBoundingClientRect`). This is read-only measurement of a public page. Mark these values `measured (browser)`, and REA-derived ones `confirmed (REA)`.

## What the blueprint records

Per reference, under a **Tiru blueprint** heading in `REFERENCES.md`:

- **Tokens:** every color with hex and where it is used; each font with family, weights, and its real source; the type scale as measured sizes, line heights, and letter-spacing for each text role (display, heading, body, label, nav, button), at both viewports.
- **Grid and spacing:** container max width, margins, column count, gutters, vertical padding of each section, and the spacing steps in use.
- **Per section, in order:** the elements and their order, the grid proportions (for example image 7 of 12 columns, text 4 of 12, offset 1), aspect ratios, alignment, density, how it reflows at 390px, and the screenshot taken at each viewport.
- **Motion and interaction per element:** trigger (load, scroll position, hover, click), the property that changes, duration, easing, delay, stagger, and the reduced-motion behavior.
- **Signature elements:** the loader, canvas, cursor, transitions, and scroll engine, with options and values.

Mark anything not obtained as `not confirmed`. The blueprint is done when someone could rebuild each section from it without opening the site. If a number is missing, measure it. Never write "similar to" or "approximately like".

## How the blueprint is used

- `LAYOUT.md` copies the measured proportions, spacing, type sizes, and motion values into the **Imitate** line of each section (`layout-blueprint.md`).
- `DESIGN.md` takes its palette, type scale, and easing from the blueprint for the references the user liked. Fonts follow the reference. If the reference font is commercial or custom, use the closest free font by shape and metrics, and say so in the handover. Do not copy the reference's font files, images, or code (`rea.md` boundaries). Use the measured values, not the reference's assets.
- What changes is only what the user's imagination asks (text, imagery, brand colors, their own sections). Everything else stays at the measured values.

## Fidelity check (after the build)

Run it in the self-audit, for every section marked Imitate:

1. Capture the built page with the same scenario, the same two viewports, and the same scroll positions as the reference.
2. Compare measured values against the blueprint: container width, section padding, column proportions, font sizes and line heights, and motion durations and easings. A difference above about 8% needs a fix or a written reason.
3. Put each pair of screenshots side by side and look at them. Composition, proportion, alignment, and rhythm must read as the same layout. `compare_web_screenshots` gives a changed-pixel ratio, which is only meaningful where text and images are alike, so treat it as supplementary and not as the pass condition.
4. Fix and repeat until every Imitate section passes. For sections with a Modify line, confirm that the listed changes are the only differences.
5. Report per section: followed closely, modified as asked, or deviated with the reason. A page that passes the audit but does not resemble its reference has failed this check.
