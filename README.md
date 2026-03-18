# /x-marketing — Claude Code Skill

A Claude Code slash command for X (Twitter) marketing campaigns. Works for personal brands, companies, and agencies managing client accounts.

## What it does

Five modes, one command:

| Mode | Command | Output |
|---|---|---|
| **Setup** | `/x-marketing setup` | Profile copy + brand voice doc + content pillars + 30-day starter plan |
| **Strategy** | `/x-marketing strategy` | Content mix table + 90-day roadmap + KPI benchmarks |
| **Content** | `/x-marketing content` | Fully drafted tweets + threads + filled calendar |
| **Audit** | `/x-marketing audit` | Scored profile review + prioritized recommendations |
| **Campaign** | `/x-marketing campaign` | Pre-launch → launch → amplification content plan |
| **Diagnostic** | `/x-marketing` | 3 questions → recommends the right mode |

Every mode asks only the questions it needs, runs a Brand Voice Elicitation Protocol before generating any content, and self-reviews output before delivering it.

## Installation

### 1. Copy the command file

```bash
cp commands/x-marketing.md ~/.claude/commands/x-marketing.md
```

### 2. Copy the skill reference files

```bash
mkdir -p ~/.claude/skills/x-marketing
cp skills/x-marketing/* ~/.claude/skills/x-marketing/
```

### 3. Restart Claude Code

The new command will appear in autocomplete after a restart.

## Usage

```
/x-marketing
```
Run the diagnostic — it asks 3 questions and recommends a mode.

```
/x-marketing setup
/x-marketing setup "Acme Corp"
```
Full onboarding for a new X presence. Produces a brand voice document, profile copy for all 6 elements, content pillars, and a 30-day starter skeleton.

```
/x-marketing strategy
```
Design or reset a content strategy. Produces content pillars, a weekly content mix, 90-day roadmap in 3 phases, and KPI benchmarks.

```
/x-marketing content
```
Generate a batch of ready-to-post content. Produces fully written tweets and threads (numbered tweet-by-tweet), plus a calendar table with status codes.

```
/x-marketing audit
/x-marketing audit "@handle"
```
Review an existing X presence. Scores every profile element, analyzes recent content, and delivers 5 prioritized recommendations.

```
/x-marketing campaign
```
Plan a specific launch, event, or initiative. Produces pre-launch teasers, launch-day content, amplification posts, and a phased campaign calendar.

## WAT Framework integration

If you're running the [WAT framework](https://github.com/anthropics/claude-code) (Workflows, Agents, Tools), the skill detects it automatically and:

- Saves brand voice docs to `agents/brand_voice.md`
- Saves content batches to `.tmp/content_drafts_[DATE].md`
- Saves calendars to `.tmp/content_calendar_[MONTH].md`
- References your existing tools (`schedule_post.py`, `fetch_metrics.py`, etc.)

Without WAT, all outputs are delivered inline as markdown.

## Companion files

| File | Purpose |
|---|---|
| `skills/x-marketing/brand-voice-template.md` | Blank brand voice schema — filled by the Brand Voice Elicitation Protocol |
| `skills/x-marketing/content-formats.md` | Hook types + tweet and thread format library with examples |

## What it never does

- Produce generic advice that applies to any account unchanged
- Generate content before establishing brand voice
- Invent follower counts, engagement rates, or metrics
- Use hype language ("game-changing", "excited to share", "innovative")
- Skip self-review before delivering content

---

Built to work with [Claude Code](https://claude.ai/claude-code).
