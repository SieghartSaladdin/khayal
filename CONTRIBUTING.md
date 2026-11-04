# Contributing to Khayal

Thanks for wanting to help. Khayal is a plugin made of Markdown skills for Claude Code and Antigravity, so most contributions are writing, not code. Please read the [Code of Conduct](CODE_OF_CONDUCT.md) first.

## Ways to contribute

- Report a problem: a skill that gives a bad result, a reference that is wrong or outdated, a broken install step.
- Improve a reference file in `skills/khayal-web/references/`.
- Add or improve a benchmark case in `skills/khayal-bench/references/catalog.md`, or share benchmark results.
- Suggest a new skill. Open an issue first so we can agree on the scope.

## Content rules

- **Language:** skill and reference files are written in English so instructions to the model stay accurate. The skills reply in the user's language.
- **No invented facts.** Do not add sites, awards, statistics, or numbers you did not see. Put the URL next to the claim, and mark opinion as opinion. If a claim has no source, say so.
- **Patterns, not copies.** Write guidance in your own words. Do not paste text from other projects, books, or websites. If an idea comes from somewhere, credit it in the README section "Where the content comes from".
- **One purpose per file.** A reference file explains one thing and is loaded only when a workflow step needs it. Do not turn references into separate skills.
- **Keep it checkable.** Prefer a rule a person can verify ("contrast meets WCAG AA") over a vague one ("make it look good").
- **Trigger phrases.** The `description` in each `SKILL.md` decides when the skill loads. Keep it accurate, and keep the Indonesian and English trigger phrases that are already there.
- **Benchmark prompts are used verbatim.** Changing an existing ID in the catalog breaks comparison with older results, so add a new ID instead of rewording one.

## Testing a change

1. Load the plugin from your checkout:

   ```bash
   claude --plugin-dir ./khayal
   ```

2. Run the skill you changed on a small, real request and check that it behaves as described.
3. If you changed how websites are built (anything under `khayal-web`), run the affected technique through `khayal-bench` and compare with the previous result if you have one.
4. If you edited a manifest, check that the JSON is valid. For Antigravity, run `agy plugin validate --strict ./khayal`.
5. Do not commit the `testing/` folder. It is git-ignored on purpose.

## Pull requests

- Branch from `main` and keep each pull request about one thing.
- Say what changed, why, and how you tested it. Mention anything you could not test.
- Do not mix unrelated formatting changes into a content change.

## License

By contributing, you agree that your contribution is released under the [MIT License](LICENSE) that covers this project.
