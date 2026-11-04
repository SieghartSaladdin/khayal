---
name: khayal-guide
description: Explains how to use the Khayal plugin and routes the user to the right skill. Use when the user asks what Khayal can do, how to start, which skill to use, or seems unsure how to begin turning an idea into a website. Also triggers on Indonesian requests such as "khayal bisa apa", "gimana cara pakai khayal", or "aku harus mulai dari mana".
---

# khayal-guide

Khayal turns a user's imagination into a distinctive, interactive website that does not look like generic AI output. This skill is the front door: it explains what exists and sends the user to the right place. It does not build anything itself.

Reply in the user's language. Keep answers short and ask at most one question at a time.

## What Khayal has

- `khayal-brief`: draws a vague idea out of the user's head and writes it down as `BRIEF.md`, then offers three design directions.
- `khayal-web`: builds the website. It writes `DESIGN.md` from the brief, builds the page, adds interaction and copy, audits its own work, and tests it in a browser.
- `khayal-bench`: benchmarks which web techniques (CSS/GSAP, SVG, shaders, Three.js, and more) Khayal can build well, at low, mid, and high difficulty. The user picks what to test and judges the result.
- `khayal-guide`: this skill.

`khayal-web` keeps its detailed guidance in reference files (design direction, interaction, copy, audit, slop tells, prompt template) and loads them when needed. They are not separate skills.

## Where to start

Ask one question if it is not already clear: does the user already know who the site is for, what single action visitors should take, and what makes it different?

- **No, or only partly:** start with `khayal-brief`.
- **Yes, and a `BRIEF.md` or `DESIGN.md` already exists:** go straight to `khayal-web`.
- **They only want a prompt to paste into another tool:** `khayal-web` has a prompt template to fill in together.
- **They want an existing page checked:** `khayal-web` includes an audit guide. Ask which page, then follow it.

## Typical flow

1. `khayal-brief`: interview, `BRIEF.md`, three directions, the user picks one.
2. `khayal-web`: `DESIGN.md`, then build, then self-audit, then test.
3. The user reviews the result and asks for changes one dimension at a time (for example "change only the typography").

## Files the flow creates

- `BRIEF.md`: the idea in the user's own words, with anything undecided marked `[UNDECIDED]`.
- `DESIGN.md`: concept, palette, fonts, lead element, motion, and bans, each with a reason. Every page in the project follows it.

## Honest limits

- There is no video skill yet. A video tool can reuse the colors, fonts, and motion language in `DESIGN.md`.
- Khayal does not invent logos, photos of people, testimonials, or numbers. Missing content is marked as a placeholder.
- The rules in the reference files come from practitioner articles and vendor documentation, not from an official standard.

## Rules

- Do not start building from this skill. Hand off to `khayal-brief` or `khayal-web` and say which one you chose and why.
- If the user asks for something Khayal does not cover, say so plainly instead of improvising.
