---
name: github-trend-finder
description: Use this skill whenever the user wants to find a GitHub repo niche/idea likely to gain stars, asks "what should I build to trend on GitHub", wants a trending open-source project idea, or wants help picking a high-potential repo concept before building it. Combines live research (GitHub Trending, Hacker News, Product Hunt) with a star-growth pattern checklist to produce a ranked list of niche ideas plus one fully fleshed-out repo concept (name, description, README draft). Trigger this for requests like "give me a repo idea that will trend", "what's hot on GitHub right now", or "help me pick a niche for my next open source project" — do NOT trigger for general coding help or when the user already has a fixed project and just wants it built.
---

# GitHub Trend Finder

Helps pick a repo niche with a realistically higher chance of trending — grounded in current data, not guesswork. **Be upfront with the user: nothing "guarantees" stars.** Timing, README quality, launch channels (HN/Reddit/Twitter), and luck matter as much as topic. This skill improves the odds by pattern-matching against what has actually worked recently; frame output that way, don't oversell it.

## Workflow

### Step 1: Calibrate with the user (skip if they already gave specifics)
Quick check — don't over-ask, 1 question max if anything is ambiguous:
- Any language/stack preference (e.g. Python, TS/React, CLI, Rust)?
- Any domain interest (dev tools, AI/LLM, data, productivity, gaming, no preference)?
- Are they building this themselves or generating a spec for a builder tool (Lovable/Bolt/Claude Code)?

### Step 2: Live research (do this every time — don't rely on memory, trends move weekly)
Run several searches in parallel/sequence:
- `web_search: github trending repositories this week`
- `web_search: github trending [language/domain if given]`
- `web_search: hacker news show hn [domain]` (Show HN launches that popped)
- `web_search: product hunt open source [domain] this month`
- Optionally `web_fetch: https://github.com/trending` and `https://github.com/trending?since=weekly` for the current snapshot (may need to fall back to search if fetch is blocked)

Look for **patterns, not just individual repos**: which categories of tool are repeatedly appearing (e.g. "AI agent framework," "self-hosted X," "CLI wrapper for Y API," "local-first Z"). A niche appearing 3+ times across different sources this week is a stronger signal than a single viral repo.

### Step 3: Apply the pattern checklist
Read `references/star_patterns.md` for the evergreen traits that correlate with fast star growth (novelty framing, "self-hosted alternative to X," dev-tool-for-AI-agents wave, single-command install, killer demo GIF, etc.). Cross-reference what you found in Step 2 against this checklist — niches that satisfy several of these traits AND are currently hot are the best candidates.

### Step 4: Produce the output
Two parts, always both:

**A. Ranked shortlist (3-5 niche ideas)**
For each: one-line concept, why it's trending right now (cite what you found), which star-pattern traits it satisfies, and a rough risk/competition note (e.g. "crowded — 6 similar repos launched this month" vs "underserved angle").

**B. One fleshed-out concept** (pick the strongest, or let the user pick from the shortlist first if they want to weigh in)
- Repo name + tagline
- One-paragraph pitch (the "elevator README hook")
- Full README draft: badges placeholder, problem statement, feature bullets, quickstart/install snippet, demo section placeholder, comparison table vs alternatives if relevant, license
- Launch plan: which channel to post first (HN Show HN / r/selfhosted / r/programming / Product Hunt), suggested title phrasing for that channel
- Honest caveat: what could stop this from trending (crowded space, needs strong visual demo, etc.)

If the user's known context (e.g. their Kenya/African-market SaaS work, Lovable/Bolt workflow) makes a niche especially natural for them to actually execute, note that — but don't force African-market angles onto every idea; global dev-tool trends often have nothing to do with that and forcing it would just be worse advice.

### Step 5: Offer next step
Ask if they want the README turned into an actual file, or want the concept translated into a Lovable/Bolt/Claude Code build prompt.
