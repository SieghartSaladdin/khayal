# Landing pages and conversion

Extra steps for pages whose job is to make a visitor act (buy, book, message, sign up). Use it after the direction is chosen and before building. A showcase or story site does not need all of it.

Reply in the user's language.

## Decide the message before the design

Design serves the message, so settle these first and show them to the user before continuing:

- **Audience:** primary and secondary. Propose them from the theme and the research, and let the user correct them.
- **Pain point:** the main problem the audience feels.
- **Objections:** what usually makes them hesitate or not act.
- **Value proposition:** one sentence on why they would pick this business over the alternatives.
- **Tone of voice:** for example warm and professional, bold and confident, exclusive and premium.

Facts about the business (numbers, clients, years, prices, certifications) come from the user. If they are missing, ask or use a labeled placeholder (`[REAL DATA]`). Never invent them.

## Copy per section

- **Hero headline:** names the outcome, not the feature. A useful shape: the result they want, plus without or with the obstacle they expect. Example shape: "A professional website in 7 days, without the technical hassle". Only use a number if it is true.
- **Hero subheadline:** one or two specific sentences.
- **Value props (three or four):** benefits, not features.
- **Social proof framing:** real figures only (clients, projects, years). Placeholders until the user supplies them.
- **CTA text:** specific and action-oriented. Not "Contact us".

See `copy.md` for the rules on specific, honest text.

## Section order

Order for conversion, adapted to the product:

1. Navigation with a CTA that stays visible
2. Hero: one primary CTA, optionally one secondary, and a trust line below
3. Problem: name the pain before offering the solution
4. Solution: how this business solves it
5. Services or offer, with a price hint if relevant
6. Social proof: testimonials and key figures
7. Portfolio or results: real work
8. FAQ: four or five real objections
9. Final CTA: one clear action
10. Footer: full contact details and links

Drop or reorder sections the product does not need. The order follows the story, not a checklist.

## Conversion elements

- A CTA reachable at all times (sticky header button).
- At least three CTA placements across the page: top, middle, bottom.
- Trust signals: real figures, client names, or certifications, each with a source.
- FAQ that answers real objections.
- A direct contact channel the audience actually uses (for example a floating WhatsApp button). Ask for the number or link. Do not invent one, and leave a clearly marked placeholder until it is provided.
- Urgency only when it is true (a real limited slot or deadline). Never a fake counter.
- Visual hierarchy leads the eye to the CTA, and whitespace is used on purpose.

## Where this differs from a generic template

- Testimonials and avatars: use labeled placeholders (`[REAL TESTIMONIAL]`) until real ones exist. A realistic-looking fake is still fake.
- Client logos and statistics follow the same rule.
- Aesthetic direction still comes from `DESIGN.md`. Conversion does not mean generic.

## Output format

A single HTML file with CSS custom properties and vanilla JS is fine for a 2D landing page. For hybrid or 3D, state the setup you chose (for example ES modules from a CDN import map, or a small Vite project) and why. Either way the page is mobile-first, has scroll-triggered effects with `IntersectionObserver` where they help, and follows `interaction.md`.
