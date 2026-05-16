# Phase 2 launch kit

Ready-to-paste materials for sharing the Report Skill. Sequence below is the recommended order — each step warms up the next.

**Before you launch**, three quick checks:
1. Demo video / GIF is recorded (see [`RECORDING.md`](RECORDING.md)) and uploaded to a GitHub Release on `TheoRata/Report-Skill` so you have a stable URL to link to. Replace the demo-strip image at the top of the README with the GIF.
2. Repo description is set (already done) and topics are added: `claude-code`, `claude-skill`, `markdown`, `report`, `html`, `documentation`. Add via `gh repo edit TheoRata/Report-Skill --add-topic ...`
3. Pin the repo on your GitHub profile.

---

## 1. Show HN

**Best time to post:** Tuesday–Thursday, 8–10am Pacific (peak HN traffic, US engineers waking up). Submit then watch the first 30 minutes — early upvotes determine front-page placement.

**Title (80-char limit, no emoji):**

```
Show HN: A Claude Code skill that renders agent reports as HTML, not Markdown
```

**URL:** `https://github.com/TheoRata/Report-Skill`

**First comment** (post immediately after the submission lands — HN expects the author to set context):

```
Hi HN, author here.

Claude Code and similar agents are great at producing long-form text — research, postmortems, audits, docs. The default output is a Markdown file in `reports/` that nobody opens. I got tired of having a directory of 3000-word .md files I'd never look at again.

This skill flips the default. The agent still writes plain Markdown — the token cost is identical — but a small renderer (one Node file, no npm install) turns it into a designed HTML document: serif typography, light/dark themes, sticky table of contents, hover-preview footnotes, syntax-highlighted code, in-document review comments. The source `.md` is embedded inside the HTML so the round-trip is lossless.

Two things I think are interesting design-wise:

1. **Comments persist by storing them as HTML markers inside the embedded source-md, not in localStorage or a sidecar file.** That means when an agent re-renders the report later, the comments come back along with the prose — they're part of the document. An agent doing a "revise based on comments" pass reads the .md, sees every open thread with its target block, edits the affected text, and resolves the marker.

2. **The artifact is self-contained.** Every CSS rule, every JS handler, the theme switcher, the lightbox, the comment rail — all inlined into a single HTML file you can email, drop in Slack, or open offline ten years from now. ~100KB per report. The trade is deliberate: no build step, no CDN, no broken links.

Install: `/plugin marketplace add TheoRata/Report-Skill` then `/plugin install report@report-skill`. Or direct clone — instructions in the README.

Happy to answer questions about the design choices, the typography, or why the .md round-trip matters.
```

**If you get traction (10+ upvotes in first hour):**
- Respond to every top-level comment within 30 minutes
- Don't get defensive about disk-size objections — point at the Cost section in the README and acknowledge the trade-off
- Don't engage with replies-to-replies that aren't asking real questions
- Save longer technical answers for follow-up tweets / blog post

---

## 2. X / Twitter thread

**Tweet 1 (the hook + demo asset):**

```
I got tired of asking Claude for a deep research report and ending up with a 3000-word .md file nobody opens.

So I built a skill that turns the same agent output into a designed HTML document.

Same Markdown the agent would've written. Token cost: zero.

[attach 30s demo MP4 or GIF here]

🔗 github.com/TheoRata/Report-Skill
```

**Tweet 2 (differentiation):**

```
The agent writes plain .md. A renderer (one Node file, no npm install) does the rest:

→ serif typography + light/dark themes
→ sticky TOC, scrollspy
→ syntax-highlighted code
→ hover-preview footnotes
→ in-document review comments
→ one-click export back to source Markdown
```

**Tweet 3 (the clever bit):**

```
The interesting design choice:

review comments are stored as HTML markers *inside the embedded source-md*, not in localStorage.

So when you re-render later, the comments come back along with the prose — they're part of the document. The agent reads the .md, sees every open thread, and revises in place.
```

**Tweet 4 (install):**

```
Install from inside Claude Code:

  /plugin marketplace add TheoRata/Report-Skill
  /plugin install report@report-skill

Or git clone — full instructions + 9 screenshots + design notes in the README.

[link to repo]
```

**Tweet 5 (engagement nudge — optional, post 2 hours later if tweet 1 stalled below 5 likes):**

```
What's the longest LLM-generated artifact you've actually re-read after the conversation that produced it?

For me it's roughly zero. The "raw .md in /reports" pattern is broken. This is one attempt at fixing the artifact end of the chain.
```

**Tagging:** Don't tag Anthropic, don't @-mention them. If they notice and reshare, great. If you tag them and they don't, the tweet looks performative.

**Time to post:** Tuesday/Wednesday, 9–11am Pacific. Pin the thread to your profile for a week.

---

## 3. r/ClaudeAI post

**Title:**

```
I built a Claude Code skill that renders long-form agent output as designed HTML reports (with in-document review comments)
```

**Body:**

```
Hey r/ClaudeAI — I've been using Claude Code heavily for research and documentation tasks. The output is usually genuinely good, but it ends up in a Markdown file I never open again. The artifact undersells the work.

I built a skill that fixes the artifact end: the agent still writes the same Markdown, but a small Node renderer turns it into a designed HTML document — TOC, callouts, footnotes, light/dark themes, syntax highlighting, the works. Token cost is unchanged because the agent writes the same .md it would have anyway.

A few features worth calling out:

• **In-document review comments.** Run a local review server, click any paragraph, leave a comment. The comments are stored as markers inside the embedded source-md, so they survive re-renders — when the agent later edits the report, your comments come along with the prose.

• **Lossless round-trip.** The source .md is embedded inside the HTML. One button extracts it back out. The HTML is the canonical artifact; the source survives inside it.

• **Inline edit mode.** Click "Edit," fix a typo straight in the browser, save back to .md. No re-rendering, no toolchain.

• **Self-contained output.** Every CSS rule and JS handler is inlined into a single HTML file you can email, drop in Slack, or open offline. ~100KB per report.

Install with `/plugin marketplace add TheoRata/Report-Skill` then `/plugin install report@report-skill`. Demo screenshots and the full design rationale in the README:

https://github.com/TheoRata/Report-Skill

Happy to take feedback or feature requests — this is the result of about three weeks of dogfooding for my own work and I'm sure there's stuff I haven't caught.
```

**Subreddit etiquette:**
- Read the rules — r/ClaudeAI sometimes restricts self-promotion. Check the sidebar for "Self-promotion threads only" rules.
- Engage in the comments. Mods notice and traffic does too.
- Crosspost to r/LocalLLaMA only if it doesn't violate their self-promo policy (they're stricter).

---

## 4. PR — `hesreallyhim/awesome-claude-code`

**PR title:**

```
Add Report Skill — render long-form agent output as designed HTML reports
```

**PR body:**

```
Adds [Report Skill](https://github.com/TheoRata/Report-Skill) to the Skills section.

A Claude Code skill that turns long-form agent output (research, deep-dives, postmortems, analyses, write-ups) into a designed HTML document instead of a flat Markdown file. The agent writes Markdown — the renderer (a single Node file, no npm install) handles light/dark themes, a sticky table of contents, syntax-highlighted code, callouts, framed figures, hover-preview footnotes, in-document review comments, and a one-click export back to the source Markdown.

Token spend is identical to writing a `.md`. The HTML is generated mechanically.

Install:

    /plugin marketplace add TheoRata/Report-Skill
    /plugin install report@report-skill

Repo: https://github.com/TheoRata/Report-Skill
License: MIT
```

**Where in the list:** check the README structure — typically the appropriate section is "Skills" or "Plugins" or "Documentation". If unsure, ask in the PR.

---

## 5. PR — `Chat2AnyLLM/awesome-claude-plugins`

This list auto-indexes plugin repos with a `.claude-plugin/marketplace.json`. Since the repo already has that file, listing may be automatic — but a PR speeds it up.

**PR title:**

```
Add report-skill marketplace
```

**PR body:**

```
Adds the [report-skill](https://github.com/TheoRata/Report-Skill) marketplace.

**Marketplace:** report-skill
**Plugin:** report
**Category:** documentation
**Source:** https://github.com/TheoRata/Report-Skill

Renders long-form Claude Code agent output as designed HTML reports (TOC, callouts, footnotes, light/dark themes, in-document review comments, lossless `.md` round-trip).
```

---

## 6. Blog post — *"How to make review comments survive re-renders"*

This is the standalone-content angle. The technical idea is novel enough to travel on HN and dev.to *separately* from the skill itself, which is the best kind of marketing — readers find the technique, then discover the project.

**Target length:** 1200–1800 words. Posted on dev.to or your personal blog, with a link back to the repo at the end (not the start — earn the click).

**Outline:**

```
Title: Persistent review comments that survive re-renders, by storing
       them in the source Markdown the renderer reads

1. The problem (200 words)
   - Agent-generated reports get re-rendered constantly. Comments
     written on the rendered HTML get lost when the .md is re-rendered.
   - Storing comments in localStorage works for one user, one browser,
     one machine. Useless for sharing.
   - Storing comments in a sidecar .json file works but the source of
     truth fragments — the .md is one place, the comments another.

2. The constraint that shapes the answer (150 words)
   - The .md file MUST stay the canonical source. An agent rerunning
     a "revise based on comments" pass should read ONE file and see
     the prose AND the comments together.

3. The trick — comments live inside the source .md as HTML markers
   (300 words)
   - Show the @report-comment marker syntax (HTML comment, attributes
     for id/status/target, body for the comment text).
   - HTML comments are invisible in rendered output, ignored by most
     Markdown processors, but easy for a regex parser to find.
   - The marker carries a target like block:b14 — the rendered
     paragraph's ID. UI affordance, not a brittle text range.

4. The renderer/review-server contract (300 words)
   - Renderer ignores @report-comment markers when producing HTML.
   - Review server parses markers out of the embedded source-md inside
     the HTML, renders them into a side rail / popovers.
   - When a user writes/edits/resolves a comment, the server updates
     BOTH the HTML's embedded source-md AND the sibling .md file.
   - Re-running `render.mjs the-report.md` later picks up every
     comment, in its current state.

5. Why this matters for AI agents specifically (200 words)
   - An agent revising a report can read the .md once and see prose +
     comments + targets in a single contiguous context.
   - The agent edits the affected text and changes status="open" to
     status="resolved" with a "Resolved: ..." note appended.
   - No separate ticketing system, no API, no schema. Just text.

6. Trade-offs and the things that don't work (200 words)
   - You can't target an arbitrary text range — only blocks. Brittle
     text-range anchoring is the wrong problem to solve.
   - Markers in the .md add visual noise when the source is read raw.
     Mitigation: most agents read the .md, not humans.
   - If the .md is hand-edited in a way that deletes a block, the
     associated comment dangles. Mitigation: the review server flags
     this on render.

7. The bigger pattern (150 words)
   - "Make the artifact carry its own metadata" — instead of building
     a parallel system to store stuff about the artifact, embed it
     inside the artifact in a way the artifact's other tools ignore.
   - HTML's `<script>` blocks, Markdown's HTML comments, EXIF in
     images: all examples of the same shape.
   - The cost is one parser. The win is durability and portability.

8. (Soft CTA) The project this came out of: link to the Report Skill repo.
```

**Where to post:**
1. Your blog / dev.to (primary)
2. Crosspost to HN as a separate Show HN ("Show HN: persistent review comments by storing them in the source Markdown") — yes, you can post twice if the angle is genuinely different
3. r/programming
4. lobste.rs (under "design" or "ai" tag)

---

## 7. Submission to Anthropic's official marketplace (Phase 3, not yet)

Only do this once Phase 2 generates ~100 stars and at least a couple of unprompted issues or PRs from users (signal that the skill is being used in anger).

**Target repo:** `anthropics/claude-plugins-official`
**Process:** open an issue in that repo requesting inclusion, link the Report-Skill repo, summarize quality signals (stars, downloads if measurable, no open critical bugs, MIT-licensed).

Anthropic curates based on quality and security. The plugin manifests are already in place; the security bar is the bit to plan for — review your own dependencies, make sure there's no telemetry, no network calls outside what's documented.

---

## Timing summary

| Day | Action |
|---|---|
| **D0** | Record demo. Replace demo-strip with GIF in README. Set GitHub topics. Pin repo. |
| **D1 (Tue/Wed 9am PT)** | Post X thread. Post Show HN. Submit r/ClaudeAI. |
| **D1 (afternoon)** | Open PRs to both awesome lists. |
| **D2–D7** | Respond to every comment / issue / PR within 24h. Build a list of feature requests. |
| **D7–D14** | Publish the blog post. Crosspost to HN. |
| **D14+** | If traction is real, plan Anthropic marketplace submission. |

If after 7 days you have under 20 stars, the bottleneck is probably the demo. Re-record it and re-post the X thread with the better video.
