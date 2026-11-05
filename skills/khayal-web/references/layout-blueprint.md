# Layout blueprint (LAYOUT.md)

`DESIGN.md` holds the identity (concept, palette, fonts). `LAYOUT.md` holds the structure: which sections the page has, in what order, and how each one is composed. It is built from the references found in research, so the page takes its layout from real award-level sites instead of the model's habits.

Reply in the user's language. Write `LAYOUT.md` in English.

## What may be taken from a reference

The method is Amati (observe, done with REA), Tiru (imitate), Modifikasi (modify), plus the user's khayal (imagination). The user prefers starting from a close copy and has approved close adaptation of a reference's design. So the section order, composition, proportions, type scale, rhythm, and motion behavior of a reference may be followed closely, up to an identical copy when the user wants that.

- **Modification follows the user's imagination.** Modify only as far as the user wants: change the text, the design, or both to match their idea (for example different proportions, a different alignment, a different order inside the section, an element from this product's concept, or the palette and fonts from `DESIGN.md`). If the user wants the result identical to a reference, do not force changes. If they want it different, change it as far as their imagination asks.

Never use a reference's name, logo, or other brand marks as if they were this site's.

## When to run it

Workflow step 4 (Lock), once the user has picked a package, and before writing `DESIGN.md`. It needs `REFERENCES.md` with a section map for each reference (see `research.md`), and the format from `web-type.md`.

## Steps

1. **List the sections and signature elements the product needs.** Signature elements are the loader, canvas or 3D scene, scroll behavior, cursor, and transitions recorded in `REFERENCES.md`. Start from `BRIEF.md`, the purpose, and, for conversion pages, the order in `landing-page.md`. Drop what the product does not need.
2. **Draft the plan inside each package.** In the proposal (`SKILL.md` step 3), each package carries a compact section list. For every section it names the reference and section it is adapted from, the composition in one line, and any cost or risk (heavy WebGL, hard on mobile, needs assets the user lacks). The user does not choose section by section. They pick a package, and may say "package 2, but the hero from package 1". Do not open a separate round of questions. Together the packages use every reference the user liked, assigned differently, and each says which section comes from which site and why (for example hero from site A, proof from site C), with each source's live URL beside it so the user can open and compare.
3. **Write `LAYOUT.md`** with the chosen sections (template below).
4. **Check the plan.** Every reference the chosen package names contributes at least one section. If a named reference cannot contribute, go back to research and replace it, instead of dropping it silently. No section was dropped silently. Every section states what is imitated and what, if anything, is modified. A section with no good reference is designed from the concept and marked `original`.

## LAYOUT.md template

For each section, in page order:

- **Section:** name and purpose
- **Source:** the reference (name and live URL) and the section it is adapted from, or `original`
- **Composition:** grid or layout, proportions, alignment, density, relative type scale
- **Motion and scroll:** what moves, what scroll does here, and the reduced-motion version
- **Imitate:** what is followed closely from the source
- **Modify:** the changes the user's imagination asks for (text, design, or both), taken from their words in the brief or the chosen concept, or `none` when the user wants it identical
- **Content needed:** text, data, and assets, with placeholders where the user has not provided them

Also list the **signature elements** the page will have (loader, canvas or 3D scene, scroll behavior, cursor, transitions). For each: its source reference and live URL, what it does, how it is adapted (for example a different 3D shape in place of the reference's model), and its cost on load and on mobile. A page built only from standard sections is not enough when the references rely on these.

Add a short **Notes** section for anything in a reference that could not be confirmed (`not confirmed`), so it is not presented as fact.

## Rules

- Follow the chosen dimension. A 2D page does not borrow a section whose idea needs a 3D scene, unless a 2D version is described.
- Keep the whole page consistent. Sections from different references still share one type scale, one spacing rhythm, and one motion character from `DESIGN.md`.
- If the user changes their mind about a section, update `LAYOUT.md` first, then the page.
- Build and audit against this file. The self-audit compares the order and composition of every built section with `LAYOUT.md`.
