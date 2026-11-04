# Prompt template: distinctive, interactive website

Fill in the bracketed parts. The concept and the lead element decide the most, so never leave them blank.

```
Role: you are a senior art director and frontend developer.

PROJECT
A website for [product], audience [who], one primary action [what].
The most distinctive thing about this product: [one sentence].

DESIGN DIRECTION (write it first, save it as DESIGN.md)
- Concept: [the material or culture the visuals come from, not "modern and clean"]
- Color: 2-3 core colors and 1 accent, each with a role
- Typography: one display font, one text font, and the reason for each
- Lead element: [the one thing a visitor sees first]
- Rhythm: every section has a different composition, and the order follows the product story

BANS
Inter, Roboto, Arial, Space Grotesk. Purple-to-blue gradients. A centered hero with a pill
badge. Three identical cards. A fake logo bar or fake testimonials. Glass, glow, and soft
shadows on every element. Decorative emoji. Invented numbers. Cream with terracotta and
black with neon as automatic escapes.

INTERACTION
- One main moment: [what this interaction explains]
- Stack: [plain HTML/CSS/JS, GSAP, or Three.js]. Animate only transform and opacity.
- Required: prefers-reduced-motion support, keyboard operable, readable without JS,
  responsive down to 360px.

PROCESS
1. Offer three clearly different design directions, then wait for me to choose.
2. Build the page. Write a reason for every generic visual choice.
3. Audit your own work against the BANS list and fix violations.
```

## One-dimension iteration

After the first result, change one thing per prompt so changes stay controlled.

```
Keep everything, change only the typography. Do not use [current font] or any font from
the BANS list. Propose a new font based on [concept], explain why, then apply it.
```

## Asking for three directions

```
Before building, give me three design directions that differ strongly from each other.
For each, write: the concept (visual source), the palette with color roles, the display
and text fonts with reasons, and the lead element. Build nothing until I pick one.
```

## Notes

- Models drift back to common choices, so update the ban list after every result.
- Lock the theme by saving DESIGN.md so later pages stay consistent.
- References help: explain why an example works, then ask for the pattern to be applied, not copied.
