# Slop tells

Format: tell, then fix. Check for clusters, not a single tell.

## First wave (the best-known defaults)

**Visual and color**
- Purple-to-blue, blue-to-cyan, or purple-to-pink gradients, especially as the main color or on headline text. Fix: 2-3 core colors plus one accent, derived from the product concept.
- Glow and blurred light orbs behind the hero. Fix: remove, or keep one emphasis with a reason.
- Glass and blur on the navbar, cards, modals, and sidebar at once. Fix: at most one or two elements.
- Everything pill-shaped (buttons, inputs, cards, badges). Fix: radius as a hierarchy tool, not decoration.
- Large soft shadows on every component. Fix: shadow only as an elevation marker.
- A palette of five to seven colors with no system, or one accent everywhere. Fix: 2-3 core plus 1 accent at key moments.
- Dark mode only because it feels technical. Fix: choose from the product and audience, or ship a working toggle.

**Layout**
- Hero, subtitle, two buttons, screenshot, three cards, testimonials, FAQ, CTA, footer. Fix: section order follows the product's content.
- Centered hero with a pill badge above a headline that repeats the badge. Fix: drop the badge and make the headline work.
- Identical feature cards (same size, icon, padding). Fix: vary by content hierarchy; not every feature needs a card.
- Bento grid with content that is not actually different in size. Fix: a plain grid or list.
- A "how it works" section that is always three numbered circles. Fix: match the real process.
- A "trusted by" logo bar without real customers. Fix: remove it.
- Three pricing columns with the middle one marked "most popular". Fix: as many tiers as really exist.
- A four-column footer (Product, Company, Resources, Legal) with no variation. Fix: match the links that exist.
- The same padding and spacing in every section. Fix: a spacing scale with rhythm.
- Section backgrounds that only alternate light and dark. Fix: vary composition, not just color.

**Decoration**
- Sparkle, star, lightning, diamond, robot, or AI-orb icons. Fix: icons relevant to the content, or none.
- All icons from one thin rounded-stroke library. Fix: treat the icon set as a visual decision.
- Emoji as decoration in headings, bullets, and buttons. Fix: remove, or use a relevant icon.
- Arrows on almost every button. Fix: only where a direction cue helps.
- A colored stripe on the left edge of cards with no meaning. Fix: only if it marks a real state.
- Capsule badges ("AI Powered", "Beta", "New") with a dot and glow. Fix: only real status labels.
- A pulsing status dot that marks nothing. Fix: dots only for real states, with no endless pulse.
- A fake terminal window as the hero visual. Fix: the real product UI.
- Stock illustrations (Undraw, Storyset, 3D blobs) unrelated to the product. Fix: real screenshots or no illustration.
- Grid, blueprint lines, or dots in the background with no identity reason. Fix: texture only when it supports the concept.

**Typography**
- Inter, Roboto, Arial, or system fonts everywhere. Fix: fonts from the product's character, with a reason.
- Big monospace headings, or wide-tracked uppercase labels ("HOW IT WORKS"). Fix: typography that improves readability.

**Motion**
- The same fade-up on every section, plus floating, scale, and bounce. Fix: one choreographed moment, calm elsewhere.
- Elements that pulse or float forever. Fix: motion has a trigger and a purpose.
- Count-up animations on numbers with no source. Fix: remove the numbers.

**Content and copy**
- Headlines and text that fit any product ("Supercharge your workflow"). Fix: say what the product does.
- Generic buttons: Get Started, Learn More, Try Now, Explore. Fix: name the action.
- Buzzwords: revolutionary, seamless, next-gen, AI-powered, cutting-edge. Fix: specific language with evidence.
- Statistics and security or performance claims without a source ("10K+ users", "99.9% uptime", "SOC 2"). Fix: no number if there is no data.
- Fake testimonials (invented avatar, name, job title). Fix: remove the section.
- A generic FAQ that is irrelevant to the product. Fix: only real questions, or no FAQ.
- Em dashes everywhere and forced groups of three. Fix: periods, commas, colons, or rewrite.

**Function**
- Buttons, dropdowns, and forms that do nothing. Fix: give real behavior or remove.
- A navbar that points to pages or sections that do not exist. Fix: only real destinations.
- No empty, loading, or error states. Fix: all three, with the cause and the next step.
- Invented data in tables, forms, or activity feeds ("John Doe", "johndoe@example.com", "+12% this week"). Fix: honest placeholder or empty.
- The default dashboard: left sidebar, four stat cards, one chart, one table. Fix: build from the decision the user makes on that screen.
- A chart that answers no question. Fix: write the question in the chart title, or use one sentence.

**Accessibility and mobile**
- Low contrast (grey on grey, white on a gradient that is light in places). Fix: WCAG AA across the whole text area.
- Not keyboard operable, or `outline: none` with no replacement. Fix: clearly visible focus.
- Horizontal scroll, clipped cards, a broken navbar, touch targets under 44px. Fix: design a real mobile state, not a shrunken desktop.
- `100vh` sections that swallow a phone screen. Fix: height follows content, or `dvh` when truly needed.

## Second wave (appears after the first wave is banned)

- A cream background with a terracotta or clay accent. Fix: color from the product's own materials and context.
- A near-black background with one neon accent. Fix: derive from the brand, not from a "technical" feel.
- Hairlines, zero radius, and newspaper columns on non-editorial content. Fix: style matches the content type.
- Small tracked uppercase labels above headlines, "A · B · C" meta strings, an arrow on every link, numbering on things that are not sequential, one colored or italic word in a headline. Fix: keep only what has a real function.
- A replacement font that is also a default (for example Space Grotesk after Inter is banned). Fix: choose from the concept and write the reason.

## How to fix properly

1. Name the default you see. Do not just swap one style for another.
2. Write a short direction (color, fonts, layout, lead element) derived from the product and keep it in a shared file.
3. Check the new plan against the second-wave list before writing code.
4. If possible, add an automated scanner to CI or an edit hook to catch tells before merge.
