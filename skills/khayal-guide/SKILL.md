---
name: khayal-guide
description: Explains how to use the Khayal plugin and routes the user to the right skill. Use when the user asks what Khayal can do, how to start, which skill to use, or seems unsure how to begin turning an idea into a website. Also triggers on Indonesian requests such as "khayal bisa apa", "gimana cara pakai khayal", or "aku harus mulai dari mana".
---

# khayal-guide

Khayal turns a user's imagination into a distinctive, interactive website that does not look like generic AI output. This skill is the front door: it explains what exists and sends the user to the right place. It does not build anything itself.

Reply in the user's language. Keep answers short and ask at most one question at a time.

## What Khayal has

- `khayal-brief`: lets the user tell a vague idea freely, asks only for what is missing, and writes it down as `BRIEF.md`. It then hands over to `khayal-web`.
- `khayal-web`: builds the website. It researches award-level references (and inspects how each is built with REA), shows them and asks what the user likes, offers three options in one message (one close to their wishes, two unique blends), writes `DESIGN.md` and `LAYOUT.md` from the one the user picks, builds the page, adds interaction and copy, audits its own work, and tests it in a browser.
- `khayal-bench`: benchmarks which web techniques (CSS/GSAP, SVG, shaders, Three.js, and more) Khayal can build well, at low, mid, and high difficulty. The user picks what to test and judges the result.
- `khayal-guide`: this skill.

`khayal-web` keeps its detailed guidance in reference files (design direction, interaction, copy, audit, slop tells, prompt template) and loads them when needed. They are not separate skills.

## Requirement: REA

Khayal requires REA (Reverse Engineer Anything, https://github.com/morluto/rea), an MCP server that inspects how a live reference site is built (libraries, canvas, scroll and transition machinery). `khayal-web` checks for it before research and stops if it is missing. Check for REA's tools when the user first asks for help. If they are missing, guide the user through installing REA before anything else, following the preflight in `skills/khayal-web/references/rea.md` (check Node.js, offer to run the setup for them after an explicit yes, remind them to restart the agent, then check again). The options:

- Claude Code: `/plugin marketplace add morluto/rea`, then `/plugin install rea@rea`, then restart.
- Any supported agent: `npx rea-agents setup`, approve the changes, then restart the agent.
- Needs Node.js (22.x, 24.x, or 26.12.1+) and a Chrome-family browser.

## Where to start

Ask one question if it is not already clear: does the user already know who the site is for, what single action visitors should take, and what makes it different?

- **No, or only partly:** start with `khayal-brief`.
- **Yes, and a `BRIEF.md` or `DESIGN.md` already exists:** go straight to `khayal-web`.
- **They only want a prompt to paste into another tool:** `khayal-web` has a prompt template to fill in together.
- **They want an existing page checked:** `khayal-web` includes an audit guide. Ask which page, then follow it.

## Typical flow

1. `khayal-brief`: the user tells the idea, missing basics are asked in one message, and `BRIEF.md` is written.
2. `khayal-web`: research, the user says which references they like, three options, the user picks one, then `DESIGN.md` and `LAYOUT.md`, build, self-audit, and test.
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
