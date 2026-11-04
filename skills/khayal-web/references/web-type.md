# Choosing the kind of site

Two choices, made by the user: the dimension (how it looks and feels in space) and the purpose (what the site must do). Ask them one at a time, give a recommendation with a reason, and let the user decide.

Reply in the user's language.

## Dimension

### 2D

HTML, CSS, JS, and optionally GSAP, SVG, or canvas 2D. Expression comes from typography, layout, color, scroll choreography, and illustration.

- Best for: pages that must convert, content-heavy pages, SEO, low-end phones, tight deadlines.
- Cost: lowest. Loads fast, easy to make accessible.
- Limit: no true depth or camera. Can still be bold; most Awwwards winners with strong typography are 2D.

### 3D

A WebGL scene is the main experience (Three.js, or React Three Fiber in a React project; GLSL shaders optional).

- Best for: product showcases where the object matters, spatial or immersive storytelling, art and portfolio pieces, launches meant to be remembered.
- Cost: heavier load, GPU use, mobile performance, asset production, and harder accessibility and SEO. Say this to the user plainly before they choose it.
- Fit test: if you remove the 3D and the site loses its reason to exist, 3D is justified. If it only decorates, suggest hybrid.

### Hybrid

A normal 2D page with one deliberate 3D moment: a hero object, one scene that reacts to scroll, or a product viewer. The 3D is contained in a canvas inside one section.

- Best for: when the user wants a "wow" but the page still has to convert or inform. This is the safe recommendation when the user is unsure.
- Cost: moderate. The rest of the page stays light and accessible.

## Purpose

Landing page (conversion), showcase or portfolio, story experience (scroll-driven narrative), or multi-page product site. If the purpose is a landing page or any page that must convert, also follow `landing-page.md`.

## Presenting the choice

Show the options as a short list with: what it feels like, what it costs, and which one you recommend and why. Example shape:

- 2D: "fast, sharp, type-led, easy to convert."
- Hybrid: "same page, plus one 3D hero object. Moderate cost."
- 3D: "the whole site is a scene. Heaviest, most memorable."

Record the decision in `DESIGN.md` under Format.

## Rules for 3D and hybrid

- **Content stays in the DOM.** Headlines, body text, links, and buttons are real HTML placed over or beside the canvas. The canvas is decorative (`aria-hidden="true"`) or has a text label that says what it shows.
- **Fallback is designed, not an afterthought.** Detect WebGL support and `prefers-reduced-motion`. When 3D cannot run, show a static poster image or a CSS version of the same moment, and keep the whole page usable.
- **Load budget (guideline, not a standard).** Keep the 3D payload as small as the concept allows, aim for a few MB at most for a conversion page, compress models (glTF/GLB with Draco or Meshopt) and textures (KTX2 or well-sized WebP), and load Three.js lazily. State the real size in the handover.
- **Loading state.** Show real content first, or a loader with true progress. Never a blank screen while assets load.
- **Frame rate.** Target a steady 60 fps on a mid-range laptop. Cap `devicePixelRatio` (about 2 on desktop, 1.5 on mobile), pause rendering when the canvas is offscreen or the tab is hidden, and dispose of geometries, materials, and textures you no longer use.
- **Mobile.** Simplify or reduce the scene at narrow widths. Test at 375px. Do not rely on hover or on drag gestures that fight page scroll.
- **Scroll.** Keep native scroll. Drive the camera or scene from scroll position (for example GSAP ScrollTrigger with `scrub`) instead of hijacking the wheel.
- **Camera controls.** Orbit or drag is optional. No content is reachable only through dragging, and a keyboard path exists for anything interactive.
- **Assets are honest.** Use procedural geometry, models the user provided, or properly licensed models with the license noted. Do not model a real branded product from imagination. Label placeholders clearly.
- **Lighting and color follow `DESIGN.md`.** A default grey studio render with a bloom glow is the 3D version of a purple gradient. Give the scene a concept: a material, a place, a light source with a reason.

## 3D checks before handover

- Page works with WebGL disabled and with reduced motion on.
- Console has no errors, including no lost-context or shader warnings.
- Frame rate checked while scrolling and interacting, and checked again with the browser's CPU or GPU throttled if the tools allow it.
- 375px width: nothing covers content, no horizontal scroll.
- Total transferred size reported.
