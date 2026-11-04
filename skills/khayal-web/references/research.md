# Research: Awwwards winners and competitors

Purpose: ground the options in real, current references instead of the model's habits, and give the user something concrete to react to. The user imagines first. Research widens what they can imagine, it does not replace their idea.

Reply in the user's language. Write `REFERENCES.md` in English.

## When to run it

After the idea is clear enough (step 1) and the dimension and purpose are chosen (step 2), and before offering directions (step 4). Never skip it. If the user said to go ahead without asking, still run it.

## Steps

1. **Build queries from the user's imagination.** Combine theme, mood, dimension, and purpose. Use the current year. Examples, adapt freely:
   - `awwwards site of the day [theme]`
   - `awwwards [theme] WebGL` or `awwwards [theme] Three.js` (for 3D or hybrid)
   - `awwwards [mood] portfolio` or `awwwards [mood] landing page`
   - `best [theme] website design [year]`
   - `[theme] competitors website` (for a conversion page, add `best converting [theme] landing page [year]`)
2. **Open the real pages.** Fetch the Awwwards page or the site itself, or use the browser tools to look at it. Awwwards pages often depend on JavaScript, so if text cannot be read, use a screenshot or the search snippet and mark what you could not confirm.
3. **Pick three to five that differ from each other.** Not five versions of the same look. Include at least one from the user's own field (a competitor) and the rest from anywhere with a strong idea. For 3D or hybrid, include at least one that uses real-time 3D well.
4. **Document each one** in `REFERENCES.md` (template below).
5. **Show the user.** One short block per reference: name, URL, one line on why it stands out, the single idea worth borrowing. Then ask what pulls them in, what puts them off, and what exactly about it. One question at a time.
6. **Synthesize.** Note what the references share (that is the convention, so avoid it or use it on purpose), what the user reacted to, and the gap nobody fills. This feeds the three directions.

## Rules

- **Do not invent.** Only list sites you actually found. State an award (Site of the Day, Developer Award, year) only if you saw it on a page. Otherwise write `award: unverified`.
- **Cite every reference** with its URL.
- **Patterns, not copies.** Borrow an idea (a type scale, a scroll moment, a way of showing a product), and write why it fits this product. Never copy a layout, asset, or brand identity.
- **Winners are not automatically right.** Many award winners are heavy, slow, or hard to use. Note the cost of each idea (load, mobile, accessibility, conversion) so the user can weigh it.
- **User first.** If the user's own imagination and the research disagree, present both and let them choose.
- **No web access.** Say so, and ask the user for two or three references they know (names or URLs) and what they like about each. Continue from those. Do not fill the gap from memory.

## REFERENCES.md template

For each reference:

- **Name and URL**
- **Source and award:** how it was found, and the award if seen (otherwise `unverified`)
- **Palette:** dominant colors and how they are used
- **Typography:** serif, sans, display, scale, weight contrast
- **Layout:** asymmetric, grid, full-bleed, and so on
- **Motion and interaction:** what stands out
- **Dimension:** 2D, 3D, or hybrid, and how the 3D is used if present
- **Unique element:** what makes it memorable
- **Mood and tone**
- **Conversion elements:** trust signals, CTA placement, proof (conversion pages only)
- **Borrow:** the one pattern worth adapting, and why it fits this product
- **Avoid:** what not to take, and the cost (load, mobile, accessibility)

At the end add **Synthesis**: shared conventions, what the user reacted to, and the open gap.
