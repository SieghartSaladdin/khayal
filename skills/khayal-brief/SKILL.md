---
name: khayal-brief
description: Turns a vague idea in the user's imagination into a clear brief for a website, a video, or both. Use at the start of a project when the user describes an idea loosely, wants help articulating it, or asks for a website or video without details. Also triggers on Indonesian requests such as "aku punya ide", "bantu jelaskan ide aku", or "pengen bikin web dan video".
---

# khayal-brief

The user has something in their head and cannot yet say it precisely. Your job is to draw it out and write it down, not to invent it. Keep it light: the user tells the idea once, and you ask only for what is truly missing.

Reply in the user's language. Write `BRIEF.md` in the language the user used.

## Rules

- Let the user tell the idea freely first. That is the main input, so do not start with a questionnaire.
- Ask only for what is missing and cannot be inferred, and put every question in one message, at most three. Skip anything the user already said.
- Never fill in an answer the user did not give. Mark it `[UNDECIDED]` instead. Feeling, the distinctive thing, and references are often best left `[UNDECIDED]`: the research in `khayal-web` proposes options for them.
- Never invent facts about the product: names, numbers, customers, features, dates, claims.
- Keep the user's own words. Quote them in the brief instead of paraphrasing them into marketing language.
- Do not design or build in this skill.

## Interview

1. Ask the user to describe the idea freely, in their own words.
2. If these essentials are still missing, ask them together in one message:
   - What is it, and who is it for?
   - What single action should the visitor or viewer take?
   - Is it a website, a video, or both, and are there constraints (stack, deadline, language, existing brand)?
3. If the user answers "I don't know" to anything, mark it `[UNDECIDED]` and move on. Do not stop to offer options. The options come from `khayal-web` after research.

## Output: BRIEF.md

Write the file in the project root with these sections, using the user's words where possible:

- **Idea:** the user's own description.
- **Audience**
- **Feeling:** what the viewer should feel, if the user said.
- **Distinctive thing:** if the user said.
- **Primary action**
- **Deliverables:** website, video, or both, plus constraints.
- **References:** anything the user volunteered, and what they like about it.
- **Open questions:** everything still `[UNDECIDED]`.

Show the brief back in a few lines in the same message as the handoff, so the user can correct it. Their correction can come with their pick in the next step, so do not wait for a separate confirmation.

## Handoff

- **Website, or website and video:** continue with `khayal-web`. It researches award-level references, asks which the user likes, and offers three options in one message, then writes `DESIGN.md` and `LAYOUT.md` from the one the user picks and builds. `khayal-web` needs REA (Reverse Engineer Anything) to study the references, so check for REA's tools before handing over. If they are missing, say so in the same message as the brief and guide the user through installing it first, following the preflight in `skills/khayal-web/references/rea.md`. Writing the brief itself does not need REA.
- **Video only:** this plugin does not yet include a video skill. Record it in the brief and tell the user. `DESIGN.md` is written so a video tool (for example Remotion, which uses the same React and CSS) can reuse the same colors, fonts, and motion language.
