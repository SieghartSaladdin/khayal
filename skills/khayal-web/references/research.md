# Research: Awwwards winners and competitors

Purpose: ground the options in real, current references instead of the model's habits, and give the user something concrete to react to. The user imagines first. Research widens what they can imagine, it does not replace their idea.

Reply in the user's language. Write `REFERENCES.md` in English.

## When to run it

After the idea is clear enough (workflow step 1) and before the proposal (step 3). Never skip it. If the user said to go ahead without asking, still run it.

## Steps

1. **Build queries from the user's imagination.** Combine theme, mood, dimension, and purpose. Run some queries with the theme and some without it (mood, dimension, or technique only), to find neutral references from other fields. Use the current year. Examples, adapt freely:
   - `awwwards site of the day [theme]`
   - `awwwards [theme] WebGL` or `awwwards [theme] Three.js` (for 3D or hybrid)
   - `awwwards [mood] portfolio` or `awwwards [mood] landing page`
   - `best [theme] website design [year]`
   - `[theme] competitors website` (for a conversion page, add `best converting [theme] landing page [year]`)
2. **Open the live sites.** An Awwwards page is only a pointer. From each Awwwards entry, follow its link to the live site and record both URLs. Then open the live site in a real browser: scroll top to bottom, take a screenshot of each section, and read the heading order and structure from the page. Fetched text or a search snippet cannot show layout, so it does not count as checked. If the live site cannot be opened, or its sections cannot be seen, replace it with another reference. Never keep a reference you did not open.
3. **Pick three to five that differ from each other.** Not five versions of the same look. Mix them on purpose: at least one relevant reference (the user's own field or a close competitor) for the conventions of that field, and at least one neutral reference from an unrelated field, chosen only because it has a section idea worth adapting. Not every reference has to match the brief. The unexpected pairing is what makes the result unique, so pick by the section worth adapting, not by topic fit. For 3D or hybrid, include at least one that uses real-time 3D well. The page will take sections from every reference you keep, so each one needs at least one section worth adapting. If fewer than three can be verified, say so instead of padding the list.
4. **Document each one** in `REFERENCES.md` (template below).
5. **Feed the proposal.** Do not stop to quiz the user about the references. They appear inside the three packages of the proposal (`SKILL.md` step 3): each package names the references it adapts, with URL and what is taken from each. The user's reaction comes with their pick.
6. **Synthesize.** Note what the references share (that is the convention, so avoid it or use it on purpose), what the user's own words point to, and the gap nobody fills. This feeds the three packages in the proposal.

## Screenshots are mandatory

- Every kept reference must be opened with a tool that takes screenshots, and the screenshots must be saved as files. Text, a search snippet, or memory cannot replace them.
- If you have any tool that can take a screenshot (a built-in browser pane, a browser extension, a devtools or Playwright tool), you must use it. Check your tool list before saying you cannot. If you have no screenshot tool but can run shell commands, try a headless browser script (for example Playwright or Puppeteer) if one is installed. If nothing works, stop and tell the user plainly, and ask for screenshots or URLs they trust. Never describe a site you did not see.
- Save files under `references-shots/<site>/`, named in order (`00-loader-1.png`, `01-hero.png`, `02-<section>.png`, and so on), and list them in `REFERENCES.md`.
- Look at each screenshot after taking it (open or read the image) and write what you actually see. Do not write the section map from page text alone.
- Do not mark a reference as verified without the list of files to back it up. The user can check the folder.

## Capture depth (the user's choice)

Capturing takes time, so the user chooses how much. Say in one line at the start of research which depth you will use, and start right away without waiting. If the user already named a depth, use it. Otherwise use Standard. The user can change it at any time.

- **Quick (partial):** the first view (and the loader, if there is one) plus the three or four most important sections of each reference.
- **Standard (all sections), the default:** every section from top to bottom at desktop width, the loader if any, and the first view at 375px.
- **Specific:** only what the user names, for example "the loader and hero of site A, the product section of site B".
- **Full detail:** everything in Standard, plus loader frames over time, every section at desktop and 375px, hover and scroll states, the canvas or 3D scene at several scroll positions, transitions, the cursor, and the technical inspection below. The slowest.

Quick is the minimum. Never go below it.

## Signature elements, not just sections

Many award-winning sites are not plain HTML and CSS sections. Their signature elements often matter more than the section layout, so record them for each reference:

- **Loader or preloader:** its type (counter, logo reveal, canvas, video), how long it lasts, what it covers, and how it exits. Capture it at several moments: the start, about one second in, near the end, and just after it exits.
- **Canvas or WebGL:** is there a `<canvas>`? What does it render (a 3D model, a shader background, particles, image distortion)? Is it fixed behind everything or inside one section? How does it react to scroll and the cursor? Capture it at several scroll positions.
- **3D use:** what the object or scene is, how the camera and the object change along the scroll, and a guess at the technique (Three.js, a shader, CSS 3D, video). Note its cost on load and on mobile.
- **Scroll behavior:** smooth scroll, pinned sections, horizontal scroll, scroll-linked animation.
- **Cursor, transitions, and micro-interactions:** a custom cursor, page or section transitions, hover effects.
- **Type and motion character:** the type scale, the main easing, and how fast things move.

For Full detail, and for any site that looks like it uses canvas or heavy animation, run a quick technical check in a browser that can execute scripts:

```js
({
  canvases: [...document.querySelectorAll('canvas')].map(c => ({w: c.width, h: c.height, position: getComputedStyle(c).position})),
  libs: ['gsap', 'ScrollTrigger', 'Lenis', 'THREE', 'Barba', 'PIXI'].filter(k => window[k]),
  fonts: [...new Set([...document.querySelectorAll('h1,h2,p,a')].map(e => getComputedStyle(e).fontFamily))].slice(0, 6)
})
```

Treat the result as a hint, because minified builds hide library names. Record what you could and could not confirm. This tells you how a site is built; it does not license copying its code or assets.

## Rules

- **Do not invent.** Only list sites you actually found. State an award (Site of the Day, Developer Award, year) only if you saw it on a page. Otherwise write `award: unverified`.
- **Cite every reference with both URLs:** the Awwwards page and the live site. A reference with only the Awwwards URL is not finished.
- **Close adaptation, not an identical copy.** The user has approved following a reference's layout, section order, composition, and motion closely, as long as the result is not identical and no assets are taken (logos, photos, illustrations, videos, 3D models). Write why each adopted idea fits this product. `layout-blueprint.md` turns this into a section-by-section plan.
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
- **Section map:** every section in page order, each with its purpose, composition (grid, proportions, alignment, density), relative type scale, and motion or scroll behavior. A screenshot per section when a browser is available, and `not confirmed` where it could not be seen.
- **Motion and interaction:** what stands out
- **Dimension:** 2D, 3D, or hybrid, and how the 3D is used if present
- **Signature elements:** the loader, canvas or 3D scene, scroll behavior, cursor, and transitions, and what each one does
- **Screenshots:** the list of saved files (`references-shots/<site>/...`) and the capture depth used
- **Unique element:** what makes it memorable
- **Mood and tone**
- **Conversion elements:** trust signals, CTA placement, proof (conversion pages only)
- **Borrow:** the sections or patterns worth adapting closely, and why they fit this product
- **Avoid:** what not to take, and the cost (load, mobile, accessibility)

At the end add **Synthesis**: shared conventions, what the user reacted to, and the open gap.
