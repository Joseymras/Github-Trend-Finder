# github-trend-finder

A [Claude Skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that helps you pick a GitHub repo niche with a realistically higher chance of trending — grounded in live research, not guesswork.

## What it does

When triggered inside Claude, this skill:

1. **Researches live** — pulls current GitHub Trending, Hacker News, and Product Hunt signals (never relies on stale training data, since trends shift weekly).
2. **Scores against a pattern checklist** — cross-references what's currently hot against an evergreen list of traits that correlate with fast star growth (self-hosted-alternative framing, killer demo GIFs, single-command install, comparison-bait README, etc.).
3. **Outputs two things, every time:**
   - A ranked shortlist (3–5 niche ideas) with rationale and competition notes
   - One fully fleshed-out concept: repo name, tagline, README draft, and a launch plan (which channel, what day, suggested title)

It's explicit about one thing: **nothing guarantees stars.** Timing, execution, and luck matter as much as topic choice. This skill improves your odds with data — it doesn't sell certainty.

## Installation

**Claude.ai / Claude apps:** Download [`github-trend-finder.skill`](./github-trend-finder.skill) from this repo and upload it via Settings → Capabilities → Skills (or drag-and-drop where skill files are accepted). Click **Save skill** to install.

**Claude Code / Cowork:** Copy the `github-trend-finder/` folder into your skills directory (e.g. `~/.claude/skills/` or your project's `.claude/skills/`).

## Usage

Just ask, e.g.:

- "Give me a repo idea that will trend on GitHub"
- "What's hot on GitHub right now that I could build a version of?"
- "Help me pick a niche for my next open source project, I want to build in TypeScript"

Claude will do the research, apply the checklist, and hand you a shortlist plus one ready-to-build concept.

## Structure

```
github-trend-finder/
├── SKILL.md                       # Main skill definition (triggers + workflow)
└── references/
    └── star_patterns.md           # Evergreen star-growth pattern checklist
```

## License

MIT — see [LICENSE](./LICENSE).
