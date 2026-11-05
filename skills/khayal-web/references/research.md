# Research: Awwwards winners and competitors

Purpose: ground the options in real, current references instead of the model's habits, and give the user something concrete to react to. The user imagines first. Research widens what they can imagine, it does not replace their idea.

Reply in the user's language. Write `REFERENCES.md` in English.

## When to run it

After the idea is clear enough (workflow step 1) and before the proposal (step 3). Never skip it. If the user said to go ahead without asking, still run it.

## Steps

1. **Build queries from the user's imagination.** Combine theme, mood, dimension, and purpose. Use the current year. Examples, adapt freely:
   - `awwwards site of the day [theme]`
   - `awwwards [theme] WebGL` or `awwwards [theme] Three.js` (for 3D or hybrid)
   - `awwwards [mood] portfolio` or `awwwards [mood] landing page`
   - `best [theme] website design [year]`
   - `[theme] competitors website` (for a conversion page, add `best converting [theme] landing page [year]`)
2. **Open the live sites.** An Awwwards page is only a pointer. From each Awwwards entry, follow its link to the live site and record both URLs. Then open the live site in a real browser: scroll top to bottom, take a screenshot of each section, and read the heading order and structure from the page. Fetched text or a search snippet cannot show layout, so it does not count as checked. If the live site cannot be opened, or its sections cannot be seen, replace it with another reference. Never keep a reference you did not open.
3. **Pick three to five that differ from each other.** Not five versions of the same look. Include at least one from the user's own field (a competitor) and the rest from anywhere with a strong idea. For 3D or hybrid, include at least one that uses real-time 3D well. The page will take sections from every reference you keep, so each one needs at least one section worth adapting. If fewer than three can be verified, say so instead of padding the list.
4. **Document each one** in `REFERENCES.md` (template below).
5. **Feed the proposal.** Do not stop to quiz the user about the references. They appear inside the three packages of the proposal (`SKILL.md` step 3): each package names the references it adapts, with URL and what is taken from each. The user's reaction comes with their pick.
6. **Synthesize.** Note what the references share (that is the convention, so avoid it or use it on purpose), what the user's own words point to, and the gap nobody fills. This feeds the three packages in the proposal.

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
- **Verified:** how the live site was checked (tool, date), which sections were seen, and which are `not confirmed`
- **Palette:** dominant colors and how they are used
- **Typography:** serif, sans, display, scale, weight contrast
- **Layout:** overall approach (asymmetric, grid, full-bleed, and so on)
- **Section map:** every section in page order, each with its purpose, composition (grid, proportions, alignment, density), relative type scale, and motion or scroll behavior. A screenshot per section when a browser is available, and `not confirmed` where it could not be seen.
- **Motion and interaction:** what stands out
- **Dimension:** 2D, 3D, or hybrid, and how the 3D is used if present
- **Unique element:** what makes it memorable
- **Mood and tone**
- **Conversion elements:** trust signals, CTA placement, proof (conversion pages only)
- **Borrow:** the sections or patterns worth adapting closely, and why they fit this product
- **Avoid:** what not to take, and the cost (load, mobile, accessibility)

At the end add **Synthesis**: shared conventions, what the user reacted to, and the open gap.
