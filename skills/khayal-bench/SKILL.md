---
name: khayal-bench
description: Benchmarks which web techniques Khayal can build well (CSS + GSAP, SVG, canvas and GLSL shaders, Three.js, CSS 3D, Lottie/Rive/Spline, text and scroll effects, page transitions, WebGL image effects, image sequences) at low, mid, and high difficulty. The user picks what to test, the agent builds it from a fixed prompt, measures it in a real browser, and the user judges the result. Use when the user wants to test, benchmark, or compare capabilities, for example "benchmark 3D", "uji kemampuan SVG", or "seberapa bagus kamu bikin Three.js". Not for building a real site: use khayal-web for that.
---

# khayal-bench

Purpose: find out what Khayal can really build, so `khayal-web` only offers the user what it can deliver. The user chooses what to test and judges the visual result. The agent builds and measures, and never gives itself the visual verdict.

Reply in the user's language. Write `RESULT.md` and the review sheet in the user's language.

## Rules

- **The user picks the test.** Do not choose IDs for them. Show the menu from `references/catalog.md` and ask.
- **Build in the main session.** Do not hand builds to subagents unless the user asks for it. A delegated run was stopped by the user as unreliable.
- **Use the catalog prompt verbatim.** Do not improve it, so results stay comparable. Record any deviation, and why.
- **Same brief for every ID** (the fictional roastery in the catalog) unless the user supplies their own. Facts about the business stay as labeled placeholders.
- **Never fabricate a number.** Anything not measured is written as "not measured" with the reason.
- **Report failures plainly.** Count attempts, list what failed, and keep a failed result as a result. No cherry-picking a good run.
- **Do not change `khayal-web` from benchmark results without the user's approval.**

## Workflow

1. **Choose.** Show the techniques and the three levels (L, M, H) from `references/catalog.md` and ask which IDs to run, one or several. If the user names a technique without a level, ask for the level and give each level in one line. If an ID needs assets (model, image, animation file, frames, account), ask the user for them or defer that ID and say so.
2. **Prepare.** Work in `testing/benchmark/<ID>/` in the project. Check the folder is git-ignored. If it is not, say so and ask before editing `.gitignore`.
3. **Build.** Take the prompt for the ID and build it. The result still follows the `khayal-web` rules: honest placeholders, accessibility, a fallback when the technique needs one. Keep a log of attempts. "Works first try" means the page opens with no console errors and every feature in the prompt works without a fix.
4. **Measure.** Follow `references/metrics.md` in a real browser, serving the folder over local HTTP. If only a static preview is available, mark the runtime metrics as not measured and say why.
5. **Write `RESULT.md`** in the ID folder: the prompt used, attempts and fixes, the measurements, what failed or was not measured, the libraries and versions, and how to open it.
6. **Hand to the user.** Tell them how to open the result, and add a review block for the ID to `testing/benchmark/REVIEW.md` from `references/review-template.md`. Wait for their verdict. You may state objective observations (an error, a dropped frame rate), but never claim the result looks good.
7. **Summarize.** Once the user has judged at least one level of a technique, write a short capability note per technique: the highest level the user judged "yes", where it fell apart, and whether to offer it to users of `khayal-web`. Show it to the user and wait for approval before putting it into `khayal-web` (for example a `references/capabilities.md` that `web-type.md` points to).

## Reporting

Keep the report short: which IDs ran, whether each worked first try, the three most important numbers, and what the user needs to review. Details live in `RESULT.md`.
