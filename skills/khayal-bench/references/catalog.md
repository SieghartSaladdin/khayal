# Benchmark catalog

The user picks one or more IDs (for example `3D-M`, `SVG-H`). Use the prompt verbatim.

## The brief

Used for every ID unless the user supplies their own: **Sangrai Senja**, a small coffee roastery in Bandung, Indonesia. Photos, testimonials, sales figures, and the WhatsApp number do not exist yet, so they are always labeled placeholders such as `[REAL DATA]`. Page text is in Indonesian.

## The three levels

- **L (low):** one effect, no outside assets. Tests whether the basic technique works.
- **M (mid):** the effect with a design concept, interaction, and a fallback. This is the level worth offering to users of `khayal-web`.
- **H (high):** production quality: a size budget, mobile, reduced motion, several sections, edge cases. This finds the limit.

## Source of each technique

"Research" means it appeared in the web research behind this catalog. "Added" means it comes from general practice and has no research support yet. The research found no official Awwwards statistics on which technologies winners use most, and many sources were one developer's blog, so treat the evidence as thin.

## GSAP-* · CSS + GSAP/ScrollTrigger · research

- **GSAP-L:** "Build the Sangrai Senja hero with text that appears in stages when the page opens and one element that shifts on scroll."
- **GSAP-M:** "Build one pinned section where the color and temperature of a single coffee bean change with scroll from green to dark, with a no-motion version for reduced motion."
- **GSAP-H:** "Build a full landing page: four sections alternating pinned and horizontal scroll, smooth scroll that stays keyboard usable, transitions between sections, smooth performance on a phone, and the page still readable without JS."

## SVG-* · interactive SVG · research (morphing, SVG transitions)

- **SVG-L:** "Draw a coffee bean in SVG whose crack line draws itself when the page opens."
- **SVG-M:** "An SVG coffee bean with a temperature slider: color, size, and crack change, smoke rises, usable by keyboard and announced through a live region."
- **SVG-H:** "A hand-made roasting drum illustration (drum, flame, falling beans, thermometer) animated per part, morphing between three roast stages, a draggable flame lever, and staying sharp at every screen size."

## FX-* · canvas 2D or fragment shader backgrounds · added

- **FX-L:** "A canvas 2D background of grey particles slowly rising behind the title."
- **FX-M:** "A smoke and ember background from a GLSL fragment shader that reacts to the cursor, with a CSS gradient fallback when WebGL is unavailable."
- **FX-H:** "A shader background that changes with scroll across four sections, adaptive resolution based on frame rate, pausing when the tab is hidden, and stable on a mid-range phone."

## 3D-* · Three.js with procedural geometry · research

- **3D-L:** "One 3D coffee bean built from code (no model file), slowly rotating, one light, color changing with scroll."
- **3D-M:** "A procedural bean with a center groove, material and light with a concept (embers as the light source), smoke particles, camera following scroll, a poster image and a fallback without WebGL."
- **3D-H:** "A procedural roasting-drum scene with many beans (instancing), a cinematic camera across four sections, light postprocessing, adaptive resolution, a 3D payload under 1.5 MB, and a simpler version for phones."

## GLB-* · Three.js with a GLB model · added

Needs a model file from the user or a clearly licensed model. Without one, defer.

- **GLB-L:** "Load one GLB model and show it with simple studio lighting, rotatable."
- **GLB-M:** "Load a compressed GLB (Draco or Meshopt) with a loader showing real progress, camera and material following `DESIGN.md`."
- **GLB-H:** "A model with KTX2 textures, several camera angles driven by scroll, lazy-loaded Three.js, memory cleanup, and the total transfer size reported."

## C3D-* · CSS 3D transforms · added

- **C3D-L:** "A coffee product card that tilts with the cursor using CSS 3D."
- **C3D-M:** "A coffee bean built from stacked CSS 3D elliptical slices, draggable to rotate, with a roast-level choice, no WebGL."
- **C3D-H:** "A CSS 3D scene with several layered objects (box, bag, beans), consistent depth, touch and keyboard interaction, and smooth performance without a strong GPU."

## TOOL-* · Lottie, Rive, Spline · research (Rive), Spline had no source

Needs assets or accounts from the user. This tests how well the agent wires up a tool, not how well it creates the asset.

- **TOOL-L:** "Embed one Lottie animation the user provides in the hero."
- **TOOL-M:** "Embed a Rive file with a state machine that reacts to hover and click, with a static image fallback."
- **TOOL-H:** "Combine Rive or Spline with GSAP scroll: choose the right tool per section, record its limits (sharpness, weight, mobile), and lazy-load everything."

## TXT-* · text animation and smooth scroll · research (Lenis with GSAP appeared)

- **TXT-L:** "A large headline that appears word by word on load."
- **TXT-M:** "Lenis smooth scroll synced to the GSAP ticker, text revealing line by line as it enters the screen, still usable with keyboard and reduced motion."
- **TXT-H:** "A whole page of kinetic typography: text following scroll, extreme type sizes, a custom cursor disabled on touch screens, and no layout shift."

## PT-* · page transitions · research (Barba.js with GSAP, overlays, SVG morph)

- **PT-L:** "Two pages with a fade transition."
- **PT-M:** "Three pages with a GSAP wipe transition, the browser back button still correct, focus moved to the new page's heading."
- **PT-H:** "Five pages with a different transition per route (wipe, SVG morph overlay, WebGL transition), preloading the next page, and still working without JS."

## WGL-* · WebGL image effects · research (WebGL transitions with Three.js and shaders)

Needs images from the user or labeled placeholders.

- **WGL-L:** "One image that distorts when the cursor passes over it."
- **WGL-M:** "A three-image gallery with shader transitions between images and a plain-image fallback without WebGL."
- **WGL-H:** "A scroll-driven gallery with distortion based on scroll velocity, lazy-loaded images, and a static version for reduced motion and weak phones."

## SEQ-* · scroll-driven image sequences · added

Needs a frame sequence from the user, or frames generated from code.

- **SEQ-L:** "Play 30 frames on a canvas following scroll."
- **SEQ-M:** "A 120-frame canvas sequence with progressive preloading, a loading indicator, and a poster when loading fails."
- **SEQ-H:** "A frame sequence with per-device sizing, WebP or AVIF, a memory limit, and the total transfer reported."
