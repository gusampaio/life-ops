# life-ops

A personal operating system framework. Treat your life with the same intentionality you'd bring to a production system — structured logging, drift detection, weekly reviews, and a principle ledger built from real experience.

Inspired by SRE practices applied to daily life.

---

## Philosophy

Production systems have dashboards, alerts, and on-call rotations because nobody trusts intuition alone. Your life deserves the same rigor. life-ops gives you:

- **Daily logs** — structured fields, not journals. Fast to fill, honest by design.
- **Drift signals** — automatic flags when patterns break (sleep, training, screen habits, deep work).
- **Weekly reviews** — computed from the daily data, not written from memory.
- **Principles** — a ledger of decisions made from lived experience, not aspirational rules.
- **Project tracking** — your personal projects get the same seriousness as work.

The system is intentionally minimal. No app, no subscription, no gamification. Just markdown files in a git repo, a Claude Code assistant that knows your context, and honest data over time.

---

## What you can use it for

- **Daily check-ins** — log sleep, energy, mood, training, food, screen habits in under 2 minutes
- **Behavioral drift detection** — get flagged when you've had 3+ reactive work days, skipped training unexpectedly, or reached for the phone first 3 mornings in a row
- **Weekly self-review** — auto-generated from your daily logs with averages, drift checks, and an honest paragraph about the week
- **Decision framework** — build a personal principle ledger from real decisions, not from books
- **Life project tracking** — side projects, fitness goals, reading — all in one place with session logs
- **AI-assisted reflection** — Claude Code reads your logs and helps you fill, review, and notice patterns without you having to ask the right questions

---

## Structure

```
daily/          — one log file per day (YYYY-MM-DD.md)
weekly/         — weekly reviews (YYYY-WNN.md)
training/       — your training schedule and phases
principles/     — personal decision framework, grows from experience
projects/       — one file per project, with session logs
books/          — reading tracker
system/         — routine.md (daily ritual) + drift-signals.md (thresholds)
home.md         — root hub, links to all sections
CLAUDE.md       — instructions for your Claude Code assistant
```

---

## Getting started

### 1. Use this template

Click **Use this template** → **Create a new repository**. Keep it private — this is your personal data.

### 2. Fill in CLAUDE.md

Open `CLAUDE.md` and replace all `[PLACEHOLDER]` sections with your actual context: who you are, your schedule, your operating modes. This is what Claude reads before doing anything.

### 3. Set up Claude Code

Install [Claude Code](https://claude.ai/code) and open your repo. Claude will read `CLAUDE.md` automatically and know your system.

### 4. Start your first daily log

Ask Claude: *"start today's log"* — it will create the file, ask the right questions, and fill the fields. Or copy `daily/example.md` and fill it yourself.

### 5. Let the data build

The drift signals and weekly reviews become meaningful after 3–4 weeks of consistent logging. Don't try to optimize early — just log honestly.

---

## Using with Claude Code

Claude Code is the intended interface for this system. With `CLAUDE.md` in place, Claude:

- Creates and fills daily logs by asking you structured questions
- Infers which day an event belongs to from context (morning entries often describe yesterday)
- Proactively asks about reading and investments every few days
- Generates weekly reviews from your daily data
- Detects which drift signals fired
- Updates project session logs after work sessions

**Example prompts:**
- *"log today — trained BJJ, sleep was rough, deep work in the morning"*
- *"generate this week's review"*
- *"check drift signals for the last 7 days"*
- *"add a principle: never make big decisions when tired"*
- *"update the RunMyTrack session log — shipped the BPM enrichment fix"*

---

## Daily log format

Every file in `daily/` follows this structure:

```markdown
# YYYY-MM-DD

← [[weekly/YYYY-WNN]] · [[training/program]] · [[books/current-book]]

## Log

| Field        | Value |
|--------------|-------|
| sleep        | solid | ok | broken | late |
| screen_first | nothing | water | phone-passive | instagram | whatsapp | email |
| training     | yes | partial | no | rest-day |
| food         | good | ok | poor | skipped |
| energy       | 1–5 |
| mood         | 1–5 |
| deep_work    | yes | partial | no — reactive day |
| mind         | both | reading only | meditation only | neither |
| substances   | none | weed-N |

## Note
[one sentence about the day]

## Tomorrow
**Intention:** [one sentence]

**Top 3:**
1. ...
2. ...
3. ...

**Training:** [session type] — [time]
```

See `daily/example.md` for a filled example.

---

## Drift signals

Thresholds that trigger a flag in your weekly review:

| Signal | Threshold |
|--------|-----------|
| sleep | 2+ consecutive broken/late |
| screen_first | social app 3+ mornings |
| training | any unplanned skip |
| deep_work | 3+ reactive days in a row |
| mind | 3+ "neither" in a row |
| energy avg | below 2.5 for the week |
| mood avg | below 2.5 for the week |

If 2+ signals fire in the same week, the weekly review surfaces a warning.

---

## Principles

The `principles/README.md` file is a ledger of decisions made from lived experience. The rule: only add a principle after you've actually lived it — not from reading, not aspirationally.

Format:
```markdown
### 1. [Title]
[Explanation of what you learned and why it matters]
Added: YYYY-MM-DD
```

---

## Contributing

This is a framework, not a product. If you've adapted it and discovered something that works better — a new field, a smarter drift signal, a weekly format that's more honest — open a PR or an issue. The goal is a system that survives contact with real life.

---

## License

MIT
