# Khayal

A skill plugin that turns a user's imagination into a website (and later a video) that does not look AI-made, with one shared design direction. It runs on Claude Code and Antigravity with the same skills. The skill files are written in English so instructions to the model stay accurate, and the skills reply in the user's language.

## Skills (4)

- `khayal-guide`: the front door. Explains what Khayal can do and points to the right skill.
- `khayal-brief`: lets the user tell a vague idea freely, asks only for what is missing, and writes it into a `BRIEF.md`, then hands over to `khayal-web`.
- `khayal-web`: the main workflow for building a 2D, 3D, or hybrid website. The method is Amati, Tiru, Modifikasi (observe, imitate, modify) plus the user's own imagination: the user imagines first, then Claude researches Awwwards winners and competitors, offers three complete options in one message, and only then builds, through to testing in a browser. The user touches the process in three places: telling the idea, picking one option, and reviewing the result. Detailed guidance lives in `skills/khayal-web/references/`:
  - `web-type.md`: choosing 2D, 3D, or hybrid, and the rules for 3D (fallback, load budget, frame rate)
  - `research.md`: researching Awwwards winners and competitors, and the `REFERENCES.md` format
  - `layout-blueprint.md`: turning researched references into `LAYOUT.md`, a section-by-section plan
  - `3d-craft.md`: realism and consistency rules for 3D and hybrid sites
  - `landing-page.md`: extra steps for conversion pages
  - `direction.md`: how to write `DESIGN.md`
  - `interaction.md`: purposeful interaction, accessibility, test checklist
  - `copy.md`: specific, honest copy
  - `audit.md` and `tanda-slop.md`: auditing a page against the signs of "AI slop"
  - `template-prompt.md`: prompt templates
- `khayal-bench`: benchmarks web techniques (CSS + GSAP, SVG, shaders, Three.js, CSS 3D, Lottie/Rive/Spline, and more) at three levels: low, mid, and high. The user picks which IDs to test, Claude builds them and measures them in a real Chrome, and the user judges how they look. The catalog is in `skills/khayal-bench/references/catalog.md`.

The references under `khayal-web` are not separate skills. Not yet built: a video skill (planned: Remotion, using the colors, fonts, and motion language from `DESIGN.md`).

## Install on Claude Code

Try it without installing:

```bash
claude --plugin-dir ./khayal
```

Install through a local marketplace or a Git repository:

```bash
claude plugin marketplace add ./khayal
claude plugin install khayal@khayal-marketplace
```

For a GitHub repository, replace `./khayal` with `owner/repo-name`.

## Install on Antigravity

```bash
agy plugin validate --strict ./khayal
agy plugin install ./khayal
agy plugin list
```

Antigravity can also install from a GitHub repository link.

## Structure

```
khayal/
  .claude-plugin/plugin.json         Claude Code manifest
  .claude-plugin/marketplace.json    Claude Code marketplace
  .antigravity-plugin/plugin.json    Antigravity manifest
  skills/khayal-guide/SKILL.md
  skills/khayal-brief/SKILL.md
  skills/khayal-web/SKILL.md
  skills/khayal-web/references/      detailed guidance, loaded when needed
  skills/khayal-bench/SKILL.md
  skills/khayal-bench/references/    catalog, how to measure, review sheet
```

## To fill in before publishing

- The owner name in `marketplace.json` and `author` in both manifests (currently a placeholder or empty).
- The `repository` field in the Antigravity manifest (already set in the Claude Code manifest).
- A logo, if you want to list it on the Antigravity marketplace.

## Contributing

Issues and pull requests are welcome. Read [CONTRIBUTING.md](CONTRIBUTING.md) and the [Code of Conduct](CODE_OF_CONDUCT.md) first.

## License

[MIT](LICENSE).

## Where the content comes from

Summarized in our own words from research on anti-slop prompting: the Anthropic Cookbook on frontend aesthetics, the capitalandcompute article on slop tells, the prg.sh article on why AI makes the same design, and motion accessibility practice. The three-dial concept (ENERGY, RHYTHM, MOTION) is inspired by the antislop plugin (MIT). All of it is practitioner opinion and vendor documentation, not an official standard.
