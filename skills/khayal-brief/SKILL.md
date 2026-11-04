---
name: khayal-brief
description: Turns a vague idea in the user's imagination into a clear brief for a website, a video, or both. Use at the start of a project when the user describes an idea loosely, wants help articulating it, or asks for a website or video without details. Also triggers on Indonesian requests such as "aku punya ide", "bantu jelaskan ide aku", or "pengen bikin web dan video".
---

# khayal-brief

The user has something in their head and cannot yet say it precisely. Your job is to draw it out and write it down, not to invent it.

Reply in the user's language. Write `BRIEF.md` in the language the user used for their answers.

## Rules

- Ask one question at a time, at most six in total. Skip any question the user has already answered.
- Never fill in an answer the user did not give. Mark it `[UNDECIDED]` instead.
- Never invent facts about the product: names, numbers, customers, features, dates, claims.
- Keep the user's own words. Quote them in the brief instead of paraphrasing them into marketing language.
- Do not start designing or building until the user confirms the summary.

## Interview

Start by letting the user describe the idea freely. Then ask, only as needed:

1. Who is this for?
2. What should someone feel in the first ten seconds?
3. What is the one thing only this idea has?
4. What single action should the visitor or viewer take?
5. What do you need: a website, a video, or both? Any constraints (stack, deadline, language, existing brand)?
6. Optional: is there anything you like as a reference, and what exactly do you like about it?

If the user answers "I don't know" to a question, offer two or three concrete options to react to, and let them pick or reject.

## Output: BRIEF.md

Write the file in the project root with these sections, using the user's words where possible:

- **Idea:** the user's own description.
- **Audience**
- **Feeling:** what the viewer should feel.
- **Distinctive thing**
- **Primary action**
- **Deliverables:** website, video, or both, plus constraints.
- **References:** what and why.
- **Open questions:** everything still `[UNDECIDED]`.

Read the brief back in a few lines and ask the user to correct it.

## Three directions

Once the brief is confirmed, offer three directions that differ strongly from each other, not three color variations. For each give:

- a name
- the concept source: a material, culture, object, or place that comes from the idea itself
- the mood in one sentence
- a palette (2-3 core colors and 1 accent, with roles)
- display and text fonts, each with a reason
- the lead element (the first thing a visitor sees)
- if a video is wanted: one line about the opening shot

Do not choose for the user. Wait for them to pick one, or to mix parts of two.

## Handoff

After the user chooses, pass the brief and the chosen direction to `khayal-direction`, which writes `DESIGN.md` for the whole project. For a website, continue with `khayal-web`. This plugin does not yet include a video skill. If a video is wanted, record it in the brief and tell the user that `DESIGN.md` is written so a video tool (for example Remotion, which uses the same React and CSS) can reuse the same colors, fonts, and motion language.
