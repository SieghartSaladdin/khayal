---
name: khayal-audit
description: Audits an existing web page or its code against the signs of generic "AI slop" and produces a numbered, prioritized findings list, then fixes only the numbers the user approves. Use when asked to audit, review a design, check whether a page looks AI-made, or fix a generic-looking design. Also triggers on Indonesian requests such as "audit halaman ini" or "cek apakah desain ini terlihat buatan AI".
---

# khayal-audit

A single tell on its own is usually fine. What makes a page feel like slop is a cluster of tells with no reason behind them. Look for clusters, then test each tell with one question: what does this choice serve?

Reply in the user's language.

## Steps

1. Read `DESIGN.md` if it exists. Without it, say the audit uses general standards, not the project's own.
2. Look at the real page (open it in a browser and take a screenshot) as well as the code, when possible. Many problems only show when the page runs.
3. Check the page against `references/tanda-slop.md`.
4. Write a numbered findings list. Each finding has: the tell, the evidence (location or a short quote), why it is a problem, and the fix.
5. **Change nothing** until the user names the numbers to fix. Numbers not mentioned are not touched.
6. Fix the approved numbers, re-run the page, and report the result.

## Priority

- **High:** function, honesty, accessibility. Dead controls, links to sections that do not exist, invented numbers or testimonials, contrast below WCAG AA, not usable by keyboard, horizontal scroll or collisions on mobile, security or performance claims without evidence.
- **Medium:** visual defaults without a reason. Gradients, glow, blur, shadows, identical cards, default fonts, template layout, stacked animations.
- **Low:** consistency and polish. Radius, spacing, rhythm between sections, a palette that has grown too wide.

## Report format

A numbered list, highest priority first. One line per finding at the top, details below. Close with one sentence: would the page still feel unique if the logo and product name were swapped?

## Not findings

- A popular font chosen with a reason that comes from the product.
- A gradient or glow that marks one level of hierarchy, with the reason written down.
- An exhibit that deliberately shows a bad example and is labeled as such.
- A single tell without a cluster, as long as it has a function.
