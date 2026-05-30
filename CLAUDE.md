# CLAUDE.md

This is a personal life operating system. Read `who-i-am.md` before doing anything in this repo — it contains who the user is, their schedule, activities, and current context.

---

## Repo structure

```
daily/          — daily log entries (YYYY-MM-DD.md), one per day
weekly/         — weekly reviews (YYYY-WNN.md)
training/       — program.md with schedule and session notes
principles/     — personal decision framework, grows over time
projects/       — project tracking files (one per project) + finances
system/         — routine.md (daily ritual) + drift-signals.md (pattern detection)
books/          — one file per book + reading.md as section hub
who-i-am.md    — personal config: identity, schedule, activities, modes
home.md         — root hub, links to all sections (central graph node)
```

---

## Daily log format

Logs have no fixed time. Entry time determines what's known:
- **Morning entry (before ~12:00 local)** — the narrative is mostly about yesterday. "I did X", "last night", "before sleep" → log to previous day. "Today I want to / plan to" → log to current day as intention.
- **Evening entry** — narrative is about the current day. All fields can be filled.
- A single day's file can be updated multiple times as the day unfolds. That's fine.

**Temporal correlation rule:** Always infer which day an event belongs to from context, not just the date of the message. If the user writes at 8am saying "I read before sleep" or "training was brutal", that happened on the previous calendar day. "I woke up and did X" = current day. When in doubt, ask.

Every file in `daily/` follows this exact format:

```markdown
# YYYY-MM-DD

← [[weekly/YYYY-WNN]] · [[training/program]] [conditional topic links — see rules below]

## Log

| Field | Value |
|-------|-------|
| sleep | solid | ok | broken | late |
| screen_first | nothing | water | phone-passive | instagram | whatsapp | email | claude |
| training | yes | partial | no | rest-day |
| food | good | ok | poor | skipped |
| energy | 1–5 |
| mood | 1–5 |
| deep_work | yes | partial | no — reactive day |
| mind | both | reading only | meditation only | neither |
| substances | none | weed-N (N = number of Js) |

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

### Topic links — graph references

The header `←` line must include all relevant topic links for that day. This lets the Obsidian graph show which days each topic appeared.

**Always include:**
- `[[weekly/YYYY-WNN]]` — every day
- `[[training/program]]` — every day

**Include only when the topic is relevant that day:**
- `[[training/run]]` — a run session happened
- `[[training/gym]]` — a gym session happened
- `[[training/bjj]]` — a BJJ or martial arts session happened
- `[[training/swim]]` — a swim session happened
- `[[books/current-book-slug]]` — mind includes reading
- `[[projects/your-project]]` — a project was worked on (use the actual project slug)
- `[[projects/finances]]` — finances were noted or discussed
- `[[principles/README]]` — a principle was reflected on or added

Customize the training and project links to match the activities and projects defined in `who-i-am.md`.

### Periodic fields (ask proactively, not every day)

When filling a daily log, always ask about these even if the user doesn't mention them:

- **Reading** — current book + page number. Ask every 2–3 days or whenever `mind` is not "neither". If they finished a book, note it and ask what's next.
- **Finances** — any notable move or decision worth logging (new position, rebalance, goal update, market note). Ask every 3–4 days. Not looking for daily tracking, just notable moves or thoughts. Log to `projects/finances.md`.
- **Big purchases** — at the end of each month (last daily log of the month), ask: "Any purchases above [your threshold] this month?" If yes, log them in the big purchases table in `projects/finances.md`.

If Reading or Finances hasn't been mentioned in 3+ days, surface it as a question before closing the log. Add as a `## Reading` or `## Finances` section at the bottom of the daily file when there's something to record.

---

## Weekly review format

Files in `weekly/` follow this format:

```markdown
# Week YYYY-WNN (Mon DD Mon — Sun DD Mon)

## Training
- Sessions completed: N/7
- Missed: [which ones and why]
- Notes: [what worked, what didn't]

## Work
- Deep work days: N/5
- Reactive days: N/5
- Key shipped: [what moved forward]
- Blockers: [what slowed things down]

## Mind
- Reading days: N/7
- Meditation days: N/7
- Book: [what you're reading]

## Energy & Mood
- Avg energy: X.X/5
- Avg mood: X.X/5
- Best day: [day — why]
- Worst day: [day — why]

## Drift check
- sleep warning (2+ broken/late): yes/no
- screen warning (3+ social first): yes/no
- training warning (unplanned miss): yes/no
- deep work warning (3+ reactive): yes/no
- mind warning (3+ neither): yes/no
- **Signals fired:** N/5

## Note
[honest paragraph about the week — what the data actually says]

## Next week intention
[one sentence]
```

---

## Common tasks

### Generate a weekly review
Use `/weekly-review` — or manually: read all `daily/YYYY-MM-DD.md` files for the target week, compute averages for energy and mood, count training completions, deep work days, mind days, run the drift check, write the review to `weekly/YYYY-WNN.md` and commit.

### Check drift signals
Use `/drift-check` — or manually: read the last 7 daily log files and check each signal against the thresholds below.

### Update a project session log
After a work session, append a row to the session log table in `projects/[project].md` with today's date, what was done, and what's next.

### Add a principle
Append to the relevant section in `principles/README.md`.
Format: `### [number]. [title]` + explanation + `Added: [date]`.
Only add after lived experience — not from reading.

---

## Drift detection thresholds

| Signal | Threshold | Action |
|--------|-----------|--------|
| sleep | 2+ consecutive broken/late | flag |
| screen_first | instagram/social 3+ days | flag |
| training | any unplanned "no" | flag |
| deep_work | 3+ reactive days in a row | flag |
| mind | 3+ "neither" in a row | flag |
| energy avg | below 2.5 for the week | flag |
| mood avg | below 2.5 for the week | flag |

If 2+ signals fire in the same week: surface a warning in the weekly review.

---

## Important context

- This repo is the source of truth for the user's daily life data
- Weekly reviews should be generated every Sunday from the daily logs (use `/weekly-review`)
- Drift signals can be checked any time mid-week (use `/drift-check`)
- Principles should only be written from real experience, not aspirationally
- The drift signal patterns in `system/drift-signals.md` will emerge from data after 4–6 weeks of logging

---

## Git conventions

Commit messages:
- `daily: log YYYY-MM-DD`
- `weekly: review YYYY-WNN`
- `training: [what changed]`
- `project: [name] — [what changed]`
- `principle: [title]`
- `system: [what changed]`
- `finance: [what changed]`
