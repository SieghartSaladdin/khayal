# Research: Awwwards winners and competitors

Purpose: ground the options in real, current references instead of the model's habits, and give the user something concrete to react to. The user imagines first. Research widens what they can imagine, it does not replace their idea.

Reply in the user's language. Write `REFERENCES.md` in English.

## When to run it

After the REA preflight (workflow step 0), once the idea is clear enough (step 1), and before the proposal (step 3). Never skip it. If the user said to go ahead without asking, still run it.

## Steps

1. **Build queries from the user's imagination.** Combine theme, mood, dimension, and purpose. Run some queries with the theme and some without it (mood, dimension, or technique only), to find neutral references from other fields. Use the current year. Examples, adapt freely:
   - `awwwards site of the day [theme]`
   - `awwwards [theme] WebGL` or `awwwards [theme] Three.js` (for 3D or hybrid)
   - `awwwards [mood] portfolio` or `awwwards [mood] landing page`
   - `best [theme] website design [year]`
   - `[theme] competitors website` (for a conversion page, add `best converting [theme] landing page [year]`)
2. **Open the live sites.** An Awwwards page is only a pointer. From each Awwwards entry, follow its link to the live site and record both URLs. Then open the live site in the browser REA is attached to (see `rea.md`) and observe it with REA (see "Observe with REA" below): section order, structure, scripts, libraries, and signature elements. Fetched text or a search snippet cannot show how a site is built, so it does not count as checked. If REA cannot inspect the live site, replace it with another reference. Never keep a reference you did not observe with REA.
3. **Pick three to five that differ from each other.** Not five versions of the same look. Mix them on purpose: at least one relevant reference (the user's own field or a close competitor) for the conventions of that field, and at least one neutral reference from an unrelated field, chosen only because it has a section idea worth adapting. Not every reference has to match the brief. The unexpected pairing is what makes the result unique, so pick by the section worth adapting, not by topic fit. For 3D or hybrid, include at least one that uses real-time 3D well. The page will take sections from every reference you keep, so each one needs at least one section worth adapting. If fewer than three can be verified, say so instead of padding the list.
4. **Document each one** in `REFERENCES.md` (template below).
5. **Feed the proposal.** Do not stop to quiz the user about the references. They appear inside the three packages of the proposal (`SKILL.md` step 3): each package names the references it adapts, with URL and what is taken from each. The user's reaction comes with their pick.
6. **Synthesize.** Note what the references share (that is the convention, so avoid it or use it on purpose), what the user's own words point to, and the gap nobody fills. This feeds the three packages in the proposal.

## REA is the evidence (Amati)

Observation (the A of ATM) is done with REA. Screenshots are not required for references.

- Every claim about a reference comes from REA output: section order and headings from the page structure and accessibility nodes, libraries and routes from the bundle analysis, effects from the tracing tools. Never describe a site from memory, a search snippet, or fetched text.
- Palette, fonts, and type scale: take them from the page's loaded resources and styles when REA exposes them. If REA output does not show a detail, write `not confirmed` instead of guessing.
- Composition and the feel of motion are the two things structure data shows poorly. When one matters for the adaptation, take one targeted `capture_web_screenshot` of just that moment (a hero, a signature scene) as optional extra evidence and say what you see. This is a supplement for a specific detail, never a per-section requirement and never a reason to skip REA.
- Do not mark a reference as verified without listing the REA tools you ran and what they returned.

## REA depth (the user's choice)

Observing takes time, so the user chooses how much. Say in one line at the start of research which depth you will use, and start right away without waiting. If the user already named a depth, use it. Otherwise use Standard. The user can change it at any time.

- **Quick (partial):** `inspect_web_page` and `analyze_web_bundle`, reading the first view, the loader if any, and the three or four most important sections.
- **Standard (all sections), the default:** Quick for the whole page: every section in order from the page structure, plus the libraries, and the loader, canvas, scroll, and cursor behavior that REA can identify.
- **Specific:** only what the user names, for example "the loader and hero of site A, the product section of site B".
- **Full detail:** everything in Standard, plus the tracing tools in `rea.md` (`trace_web_module_imports`, `inspect_web_event_listeners`, `observe_web_execution`, `observe_web_session`) to find which module drives each loader, canvas scene, scroll animation, transition, and cursor. The slowest.

Quick is the minimum. Never go below it.

## Signature elements, not just sections

Many award-winning sites are not plain HTML and CSS sections. Their signature elements often matter more than the section layout, so record them for each reference:

- **Loader or preloader:** its type (counter, logo reveal, canvas, video), how long it lasts, what it covers, and how it exits. Find it in the page structure and the scripts that drive it; for Full detail, observe it with `observe_web_execution`.
- **Canvas or WebGL:** is there a `<canvas>`? What does it render (a 3D model, a shader background, particles, image distortion)? Is it fixed behind everything or inside one section? How does it react to scroll and the cursor? REA's page structure and bundle analysis answer most of this; trace the module for the rest.
- **3D use:** what the object or scene is, how the camera and the object change along the scroll, and a guess at the technique (Three.js, a shader, CSS 3D, video). Note its cost on load and on mobile.
- **Scroll behavior:** smooth scroll, pinned sections, horizontal scroll, scroll-linked animation.
- **Cursor, transitions, and micro-interactions:** a custom cursor, page or section transitions, hover effects.
- **Type and motion character:** the type scale, the main easing, and how fast things move.

## Observe with REA (required)

For every kept reference, at every depth, run REA on the live site (`references/rea.md` has the preflight, how to start the browser, and the tool list). At minimum:

- `inspect_web_page`: what the page loads (scripts, resources, canvas elements, workers) and its structure.
- `analyze_web_bundle`: libraries and structure behind the scripts (for example Three.js, GSAP, Lenis, Barba, PIXI), routes, and chunks.

For Full detail, and for any site that looks like it uses canvas or heavy animation, go further with the tracing tools in `rea.md` to find which module drives the loader, the canvas scene, the scroll animation, or the cursor.

Record in `REFERENCES.md` what REA confirmed (`confirmed (REA)`) and what it could not (`guess`), including the limitations REA reports, because minified or obfuscated builds can hide library names. REA tells you how a site is built. Reusing its code or assets needs the user's confirmation that they have the rights (see `SKILL.md`).

## Rules

- **Do not invent.** Only list sites you actually found. State an award (Site of the Day, Developer Award, year) only if you saw it on a page. Otherwise write `award: unverified`.
- **Cite every reference with both URLs:** the Awwwards page and the live site. A reference with only the Awwwards URL is not finished.
- **Close adaptation, not an identical copy.** The user has approved following a reference's layout, section order, composition, and motion closely, as long as the result is not identical. Reusing a reference's actual assets, text, or code is a separate matter and needs the user's confirmation that they have the rights (see `SKILL.md`). Write why each adopted idea fits this product. `layout-blueprint.md` turns this into a section-by-section plan.
- **Winners are not automatically right.** Many award winners are heavy, slow, or hard to use. Note the cost of each idea (load, mobile, accessibility, conversion) so the user can weigh it.
- **User first.** If the user's own imagination and the research disagree, present both and let them choose.
- **No web access.** Say so, and ask the user for two or three references they know (names or URLs) and what they like about each. Continue from those. Do not fill the gap from memory.

## REFERENCES.md template

For each reference:

- **Name, Awwwards page URL, and live site URL**
- **Source and award:** how it was found, and the award if seen (otherwise `unverified`)
- **Role:** `relevant` (the user's field or a close competitor) or `neutral` (an unrelated field, chosen for a section idea)
- **Verified:** how the live site was checked (tool, date), which sections were seen, and which are `not confirmed`
- **Palette:** dominant colors and how they are used
- **Typography:** serif, sans, display, scale, weight contrast
- **Layout:** overall approach (asymmetric, grid, full-bleed, and so on)
- **Section map:** every section in page order, each with its purpose, composition (grid, proportions, alignment, density), relative type scale, and motion or scroll behavior. Taken from REA evidence, and `not confirmed` where REA could not show it.
- **Motion and interaction:** what stands out
- **Dimension:** 2D, 3D, or hybrid, and how the 3D is used if present
- **Signature elements:** the loader, canvas or 3D scene, scroll behavior, cursor, and transitions, and what each one does
- **REA evidence:** which REA tools were run, the libraries, canvas use, and routes found, each marked `confirmed (REA)` or `guess`, and the limitations REA reported
- **Depth:** the REA depth used, and any optional screenshot taken (what it was for)
- **Unique element:** what makes it memorable
- **Mood and tone**
- **Conversion elements:** trust signals, CTA placement, proof (conversion pages only)
- **Borrow:** the sections or patterns worth adapting closely, and why they fit this product
- **Avoid:** what not to take, and the cost (load, mobile, accessibility)

At the end add **Synthesis**: shared conventions, what the user reacted to, and the open gap.
