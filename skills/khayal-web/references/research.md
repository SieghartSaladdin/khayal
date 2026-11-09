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
2. **Open the live sites.** An Awwwards page is only a pointer. From each Awwwards entry, follow its link to the live site and record both URLs. Then open the live site in the browser REA is attached to (see `rea.md`) and observe it with REA at the depth set in "REA depth" below. Fetched text or a search snippet cannot show how a site is built, so it does not count as checked. If REA cannot inspect the live site, replace it with another reference. Never keep a reference you did not observe with REA.
3. **Pick three to five that differ from each other.** Not five versions of the same look. Mix them on purpose: at least one relevant reference (the user's own field or a close competitor) for the conventions of that field, and at least one neutral reference from an unrelated field, chosen only because it has a section idea worth adapting. Not every reference has to match the brief. The unexpected pairing is what makes the result unique, so pick by the section worth adapting, not by topic fit. For 3D or hybrid, include at least one that uses real-time 3D well. The page will take sections from every reference you keep, so each one needs at least one section worth adapting. If fewer than three can be verified, say so instead of padding the list.
4. **Document each one** in `REFERENCES.md` (template below).
5. **Show the research and check in.** Before any proposal, show the user the output (`SKILL.md` step 2): each reference with both URLs, a short style summary, and what is worth borrowing, and ask what they like, what they dislike, and whether to go deeper on any site. Their answers decide how the proposal is built.
6. **Synthesize.** Note what the references share (that is the convention, so avoid it or use it on purpose), what the user's own words and likes point to, and the gap nobody fills. This feeds the proposal: package 1 follows what the user liked, and packages 2 and 3 blend references into something unique.

## REA is the evidence (Amati)

Observation (the A of ATM) is done with REA. Screenshots are not required for references.

- Every claim about a reference comes from REA output: section order and headings from the page structure and accessibility nodes, libraries and routes from the bundle analysis (Deep), effects from the tracing tools (Deep). Never describe a site from memory, a search snippet, or fetched text.
- Palette, fonts, and type scale: take them from the page's loaded resources and styles when REA exposes them. If REA output does not show a detail, write `not confirmed` instead of guessing.
- Composition and the feel of motion are the two things structure data shows poorly. When one matters for the adaptation, take one targeted `capture_web_screenshot` of just that moment (a hero, a signature scene) as optional extra evidence and say what you see. This is a supplement for a specific detail, never a per-section requirement and never a reason to skip REA.
- Do not mark a reference as verified without listing the REA tools you ran and what they returned.

## REA depth (the user's choice)

Deep observation takes a long time, so the first pass is a simple style survey, the user checks the sites themselves, and deep work happens only for the sites they choose. Say in one line at the start of research that you are doing the simple survey, and that deeper research is available. Start right away without waiting.

- **Light, the default (a style survey):** the landing page (first page) of each reference only, with `inspect_web_page`. Record the style: fonts (from the loaded resources), palette when exposed, the layout, and the section order. Do not analyze bundles, do not trace modules, and do not open inner pages. This is the minimum. Never go below it. Give the user each site's live URL and a short style summary so they can open the sites and judge for themselves.
- **Deep, chosen sites:** Light for every reference, then Deep for only the sites the user names (for example "study site B deeply").
- **Deep, all sites:** Deep for every kept reference.
- **Specific:** only what the user names, for example "the loader and hero of site A, the product section of site B".

**Deep** means everything in Light plus `analyze_web_bundle` (libraries, routes) and the tracing tools in `rea.md` (`trace_web_module_imports`, `inspect_web_event_listeners`, `observe_web_execution`, `observe_web_session`) to find which module drives each loader, canvas scene, scroll animation, transition, and cursor, and the inner pages the user asks about. Say that it takes longer.

Neither Light nor Deep is enough to imitate a reference. Once the user picks a package, the Tiru capture (`tiru-capture.md`) runs on every reference that package names and records measured values in a **Tiru blueprint** inside `REFERENCES.md`. That is automatic and needs no request from the user.

The user decides after looking at the research, at the check-in in `SKILL.md` step 2. Their reply can include "go deep on site B" or "go deep on all". Then run Deep on those sites before building the proposal. If they never ask, build from the Light survey and mark anything about how a site is built as `guess`.

## Signature elements, not just sections

Many award-winning sites are not plain HTML and CSS sections. Their signature elements often matter more than the section layout, so record them for each reference. In Light mode note only what the page structure visibly shows (for example a `<canvas>` or a loader element) and mark the rest `guess`. Fill in the details in Deep research:

- **Loader or preloader:** its type (counter, logo reveal, canvas, video), how long it lasts, what it covers, and how it exits. Find it in the page structure and the scripts that drive it; for Deep research, observe it with `observe_web_execution`.
- **Canvas or WebGL:** is there a `<canvas>`? What does it render (a 3D model, a shader background, particles, image distortion)? Is it fixed behind everything or inside one section? How does it react to scroll and the cursor? REA's page structure and bundle analysis answer most of this; trace the module for the rest.
- **3D use:** what the object or scene is, how the camera and the object change along the scroll, and a guess at the technique (Three.js, a shader, CSS 3D, video). Note its cost on load and on mobile.
- **Scroll behavior:** smooth scroll, pinned sections, horizontal scroll, scroll-linked animation.
- **Cursor, transitions, and micro-interactions:** a custom cursor, page or section transitions, hover effects.
- **Type and motion character:** the type scale, the main easing, and how fast things move.

## Observe with REA (required)

For every kept reference, at every depth, run REA on the live site (`references/rea.md` has the preflight, how to start the browser, and the tool list). At minimum, in Light:

- `inspect_web_page`: the page's structure (section order, headings), what it loads (scripts, resources, fonts, canvas elements), and its style signals.

Only when the user asks for Deep research (on chosen sites or on all), add:

- `analyze_web_bundle`: libraries and structure behind the scripts (for example Three.js, GSAP, Lenis, Barba, PIXI), routes, and chunks.
- The tracing tools in `rea.md`, to find which module drives the loader, the canvas scene, the scroll animation, or the cursor.

If a site in Light mode clearly uses canvas or heavy animation, mark the details `guess` and mention that Deep research is available for it.

Record in `REFERENCES.md` what REA confirmed (`confirmed (REA)`) and what it could not (`guess`), including the limitations REA reports, because minified or obfuscated builds can hide library names. REA tells you how a site is built.

## Rules

- **Do not invent.** Only list sites you actually found. State an award (Site of the Day, Developer Award, year) only if you saw it on a page. Otherwise write `award: unverified`.
- **Cite every reference with both URLs:** the Awwwards page and the live site. A reference with only the Awwwards URL is not finished.
- **Close adaptation, up to an identical copy.** The user has approved following a reference's layout, section order, composition, and motion closely, including identically when they want that. Modification goes only as far as the user's imagination asks. Write why each adopted idea fits this product. `layout-blueprint.md` turns this into a section-by-section plan.
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
