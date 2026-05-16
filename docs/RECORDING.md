# Demo recording script

A 30-second screencast is the single most impactful asset for sharing this skill. Record it once, link it from the README and every social post.

This file is a shot list — exact commands, timing, and what to capture — so you can record cleanly in one take with macOS's built-in screen recorder.

## Setup (one-time)

1. **Get a clean demo project** somewhere away from your real work:
   ```bash
   mkdir -p ~/demos/report-skill-demo && cd ~/demos/report-skill-demo
   ```
2. **Install the skill** if you haven't already (from inside Claude Code, in any directory):
   ```
   /plugin marketplace add TheoRata/Report-Skill
   /plugin install report@report-skill
   ```
3. **Window layout for recording:** position your terminal on the left half of the screen, your browser on the right half. Use a 1440×900 or 1920×1080 display so the resulting file isn't enormous.
4. **Theme:** light theme in the terminal, dark mode in the OS (or vice versa — just be consistent). Hide the dock with `Cmd+Option+D`.

## Recording (30 seconds)

Start recording with `Cmd+Shift+5` → *Record Selected Portion* → drag a frame covering both windows.

| Time | Action | Beat |
|---|---|---|
| 0:00–0:03 | Terminal visible. Type into Claude Code: *"Research the failure modes of LLM-generated frontend code and write me a deep-dive."* | Setup — establish what the user asks for. |
| 0:03–0:12 | Claude streams. Don't wait for the whole thing — cut while it's still writing. Pause the recording. | Establish that this is the *agent producing real work*. |
| 0:12–0:13 | Resume. The agent finishes. A line appears in the terminal: *"Report rendered: open `reports/failure-modes-…html`."* | Payoff. |
| 0:13–0:16 | Click the file path / open the URL. The browser opens to the rendered light-mode hero. | Reveal — the moment the value lands. |
| 0:16–0:20 | Scroll slowly. Pass a callout, a table, a code block. | Show the prose toolkit. |
| 0:20–0:23 | Click the **Theme** button. Page flips to dark mode. | One-button theme. |
| 0:23–0:27 | Hover a footnote. Popover appears in the margin. | The "wow this is real software" beat. |
| 0:27–0:30 | Click **Save as MD**. Download confirmation flashes. Hold on the file. | Lossless round-trip — the source is right there. |

Stop recording.

## Editing

Trim the dead air at the start. Speed up the *agent writing* segment (0:03–0:12) to 4× so the whole video lands at ~25 seconds.

Export at 1080p, H.264, MP4. Aim for under 8 MB so it embeds cleanly on GitHub and X.

For an animated GIF version (for places that don't support video): export the MP4 to 720p GIF at 12 fps using `ffmpeg`:

```bash
ffmpeg -i demo.mp4 -vf "fps=12,scale=960:-1:flags=lanczos" -loop 0 demo.gif
```

Aim for under 5 MB GIF — GitHub will inline preview it in issues, PRs, and the README.

## Where it goes

1. **Top of `README.md`** — replace the `00-demo-strip.png` reference with the demo video. GitHub auto-plays MP4s uploaded directly to releases or issue comments; for the README, embed the GIF.
2. **X/Twitter thread first tweet** — attach the MP4 directly. Native video plays inline and gets more impressions than linked content.
3. **Show HN comment** — paste a direct link to the MP4 hosted on GitHub releases.
4. **Reddit post** — same MP4 link. Reddit will autoplay videos hosted on i.imgur.com or v.redd.it; either re-upload or link to the GitHub-hosted version.

## What NOT to show

- Don't show the agent's raw streaming output for more than a couple of seconds. People watching are evaluating *the artifact*, not the AI working.
- Don't show your editor opening the `.md` source first. The "huh, just a Markdown file" beat is exactly the bad default the skill solves — start the reveal with the HTML.
- Don't narrate. Captions are fine, voiceover is rarely worth it for a 30-second piece.
