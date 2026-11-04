---
name: khayal-interaction
description: Designs and builds purposeful website interaction: a main interactive moment, scroll-driven effects, animation, cursor effects, GSAP, ScrollTrigger, Three.js, with accessibility rules, performance rules, and a test checklist. Use when the user asks for an interactive website, animation, scrollytelling, or effects that feel alive without being gimmicks. Also triggers on Indonesian requests such as "bikin web interaktif" or "tambahkan animasi".
---

# khayal-interaction

Good interaction explains something. Bad interaction only fills the page.

Reply in the user's language.

## Principles

- Choose **one main moment** and write down what it reveals about the product. Example: striking out a slop tell changes a sample page, so the visitor sees before and after.
- Use scroll when scrolling is part of the explanation (it changes a visualization or a scene), not as a way to move around.
- Limit effects: one subtle parallax per page, and do not stack many pinned or scroll-progress sections.
- One choreographed moment on load (staggered reveal, a line that draws itself) beats scattered micro-interactions. After it, nothing loops without a trigger.
- Small extras (hover, focus, status) only when they have a function.

## Choosing a stack

- Start with plain HTML, CSS, and JS. State stack limits at the start.
- GSAP with ScrollTrigger for scroll-linked animation: `scrub` ties progress to scroll position (a number adds smoothing lag), `pin` holds an element for a range of scroll.
- Three.js only if 3D is genuinely the content. GSAP can drive Three.js object properties through `onUpdate`.
- Smooth scroll (for example Lenis) is optional and must stay keyboard navigable.
- Animate `transform` and `opacity` only. Drive cursor effects with `requestAnimationFrame` and disable them on touch devices.

## Required

- `prefers-reduced-motion`: provide a complete no-motion version (content shows immediately, animation off). Design both, do not just switch it off.
- Keyboard: every effect has a keyboard path. Interactive elements are `button` or `a`, not clickable `div`s. Focus is always visible. Pinned sections and scroll snap stay navigable.
- Without JS, or if animation fails, the page stays readable. Do not hide content behind an animation with no way out.
- Touch: no hover-only interactions. Targets are at least 44px with spacing between them.
- Announce results through a live region (`aria-live`), and use `aria-pressed` for toggles.

## Control patterns that work

- A list of corrections as `button` elements with `aria-pressed`, a counter in a live region, "select all" and "reset" buttons, and buttons disabled when not relevant.
- Parts of an exhibit may be clickable as a mouse shortcut, as long as the keyboard path exists through the list.
- A copy button uses the Clipboard API with a fallback: if it is denied, select the text and show a message. Clipboard permission can be blocked in some contexts.

## Pitfalls that have appeared

- A variant hidden with a plain class (`.f {display:none}`) loses to a more specific rule (`.card b {display:block}`), so the "after" text shows early. Test the initial state as well as the final one.
- A tall `sticky` element covers content on small screens. Use sticky only when both width and height can hold it (`min-width` and `min-height` media queries), and on narrow screens scroll to the result after an action.
- Entry animation built on `opacity:0` depends on the animation running. A screenshot taken too early, or a hidden tab, can show a blank page. Make sure there is a way out if the animation does not run, and wait before judging from a screenshot.

## Test checklist

Run in a real browser, not just by reading code:

- Click every control one by one and watch the result, in both the initial and final states.
- Scroll fast, scroll backward, resize the window.
- At 375px width: no horizontal scroll, 44px targets, nothing covering content.
- Use only Tab, Enter, Space, and Escape. Focus is visible.
- Turn on reduced motion and compare.
- Read the console: there must be no errors.
- Report what was tested and what was not, including limits of the test environment.
