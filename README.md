# Report Skill

A [Claude Code](https://claude.com/claude-code) skill that turns long-form agent output — research, deep-dives, postmortems, analyses, write-ups — into a designed HTML report instead of a raw Markdown file. The agent writes Markdown; a renderer produces a polished HTML document with light/dark theming, a table of contents, footnotes, code blocks, callouts, framed figures with click-to-zoom, and a one-click export back to Markdown.

The token spend is the same as writing plain Markdown — the HTML is generated mechanically by `render.mjs`.

## What's in here

| File | Purpose |
|---|---|
| `SKILL.md` | Skill entry point — read by Claude Code when `/report` is invoked |
| `render.mjs` | Markdown → HTML renderer (the workhorse) |
| `template.html` | The HTML shell the renderer fills in |
| `index-template.html` | Template for the `reports/` index page |
| `build-index.mjs` | Builds the index of all reports in a project |
| `comments.mjs` / `clean-comments.mjs` | In-browser comment popup system |
| `review.mjs` / `review-summary.mjs` | Review-mode helpers |
| `extract.mjs` | Pulls source Markdown back out of a rendered HTML report |
| `example.html` | A rendered sample so you can see what output looks like |
| `*.test.mjs` | Node `--test` suite |

## Install

Clone into your Claude Code skills directory:

```bash
git clone https://github.com/TheoRata/Report-Skill.git ~/.claude/skills/report
```

That makes the skill globally available across all projects. Trigger it by asking Claude for a report, deep-dive, analysis, postmortem, etc., or invoke `/report` directly.

To install per-project instead, clone into `<project>/.claude/skills/report/`.

## Use

Ask Claude for any long-form structured output — *"write me a deep-dive on X"*, *"postmortem the Y incident"*, *"document the Z system"* — and the skill renders it as HTML into the project's `reports/` directory. Open the file in a browser.

To edit a report later, ask Claude to update it: the skill edits the source Markdown in place and re-renders.

See `SKILL.md` for the full workflow, frontmatter schema, Markdown extensions (callouts, framed figures, footnotes), and renderer flags.

## Tests

```bash
node --test *.test.mjs
```

## License

MIT — use it, fork it, improve it.
