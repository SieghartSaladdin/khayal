# Design direction (DESIGN.md)

The result of this skill is one `DESIGN.md` file that every output in the project shares, so the website and any video look like one brand. Without it, the model fills the gaps with the average of every tutorial.

Reply in the user's language. Write `DESIGN.md` in English.

## Who writes it

Design direction is the owner's identity. If the user writes it or answers questions, record their answers as given. If the agent writes it, label the top of the file: "Direction written by agent, not yet approved by the owner." Agents drift toward default taste, which is exactly what this plugin avoids.

If a `BRIEF.md` exists (from `khayal-brief`), read it first and build on it. Do not contradict the user's own words in it.

## Steps

1. Collect: product, audience, one primary action, the most distinctive thing, and the mood. One deciding question is enough if something is missing. Also read the chosen format (2D, 3D, or hybrid, see `web-type.md`) and `REFERENCES.md` and `LAYOUT.md` if they exist.
2. Find the visual source in the product itself: a material, culture, object, place, or way of working. Example: a page about corrections uses exam paper, ballpoint ink, and a teacher's red pen. "Modern and clean" is not a concept. References from research inform this step but do not replace it.
3. Use the direction from the package the user chose (see `SKILL.md`). Only if no package was offered, give three directions that differ strongly (not three color variations), each with a concept, palette, fonts, lead element, and where the 2D or 3D weight sits, and wait for a pick.
4. Write `DESIGN.md` with the structure below. Do not ask again about choices the user already made.

## DESIGN.md structure

- **Design Read:** one sentence. "A [kind of page] for [audience], in a [visual language] style."
- **Format:** 2D, 3D, or hybrid, and the purpose (landing page, showcase, story, product site). For 3D or hybrid add the scene concept (what it shows and why), the fallback when WebGL is unavailable, and the load budget.
- **References:** the entries from `REFERENCES.md` that shaped this direction, each with the one pattern borrowed. Omit if no research was done.
- **Dials:** ENERGY, RHYTHM, and MOTION, each 1 (calm), 2 (balanced), or 3 (bold). ENERGY is how loudly the page greets the visitor, RHYTHM is how much sections differ from each other, MOTION is how much movement there is. The output must stay consistent with the declared dials.
- **Concept** and the reason for it.
- **Lead element:** the one thing seen first, and why.
- **Color:** 2-3 core colors plus 1 accent, each with hex, role, and reason. The accent appears only at key moments.
- **Typography:** display font, text font, optionally one accent font, each with a reason. Use extreme contrast (weight 200 against 800, size jumps of 3x or more). Monospace only for actual code.
- **Background and texture:** only if it supports the concept, with a reason. Lines, grids, and patterns with no reason are cut.
- **Rhythm:** how sections differ from each other, and why the order follows the product's story.
- **Interaction and motion:** the one main moment and what it does, one choreographed moment on load, reduced-motion rules.
- **Shared tokens:** the colors, fonts, easing curve, and motion character in a form a video or another medium can reuse.
- **Bans:** the defaults this project avoids.

## Choice rules

- Do not pick Inter, Roboto, Arial, system fonts, or Space Grotesk without a reason that comes from the product. Models keep returning to Space Grotesk once Inter is banned, so name it too.
- After the classic bans (purple gradients, Inter), check two automatic escapes: cream with a terracotta accent, and black with one neon accent. Use them only if the concept truly demands them.
- Choose a light or dark theme from the product and audience. If there is no strong reason for one theme, ship a working toggle for both.
- Check every text and background color pair for contrast (WCAG AA). Do not guess.
- Limit gradients, glow, blur, and shadow to one or two elements, with a written reason.
- A choice whose reason cannot be written in one sentence counts as undecided.
