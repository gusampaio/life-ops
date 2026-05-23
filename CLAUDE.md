# CLAUDE.md

This is your personal life operating system. Read this file before doing anything in this repo.

---

## Who I am

- [YOUR ROLE] at [YOUR COMPANY], based in [YOUR CITY]
- Active in: [YOUR ACTIVITIES — e.g. BJJ, gym, running, music, photography]
- Personal project: [PROJECT NAME] — [one-line description]

---

## Repo structure

```
daily/          — nightly log entries (YYYY-MM-DD.md), one per day
weekly/         — weekly reviews (YYYY-WNN.md)
training/       — program.md has the full schedule and gym phases
principles/     — personal decision framework, grows over time
projects/       — one file per project with session logs
system/         — routine.md (daily ritual) + drift-signals.md (pattern detection)
books/          — one file per book + reading.md as the section hub
home.md         — root hub, links to all sections
```

---

## Operating mode

<!-- Add your schedule here. Example: -->
```
Mon  REST
Tue  BJJ 19:30
Wed  Gym 07:20
Thu  BJJ 19:30
Fri  Gym + BJJ
Sat  Swim (recovery)
Sun  Run (easy)
```

---

## Daily log format

Logs have no fixed time. Entry time determines what's known:
- **Morning entry (before ~12:00 local)** — the narrative is mostly about yesterday. "I did X", "last night" → log to previous day. "Today I want to / plan to" → log to current day as intention.
- **Evening entry** — narrative is about the current day. All fields can be filled.
- A single day's file can be updated multiple times. That's fine.

**Temporal correlation rule:** Always infer which day an event belongs to from context, not just the date of the message. If the user writes at 8am saying "I read before sleep" or "training was brutal", that happened on the previous calendar day. "I woke up and did X" = current day. When in doubt, ask.

Every file in `daily/` follows this exact format:

```markdown
# YYYY-MM-DD

← [[weekly/YYYY-WNN]] · [[training/program]] · [[books/current-book-slug]]

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

### Periodic fields (ask proactively, not every day)

When filling a daily log, always ask about these even if the user doesn't mention them:

- **Reading** — current book + page number. Ask every 2–3 days or whenever `mind` is not "neither".
- **Investments** — any update worth logging (new position, rebalance, market note). Ask every 3–4 days.

If either hasn't been mentioned in 3+ days, surface it before closing the log.

---

## Weekly review format

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
Read all `daily/YYYY-MM-DD.md` files for the target week.
Compute averages for energy and mood.
Count training completions, deep work days, mind days.
Run the drift check against the thresholds in `system/drift-signals.md`.
Write the review to `weekly/YYYY-WNN.md` and commit.

### Check drift signals
Read the last 7 daily log files.
Check each signal in `system/drift-signals.md`.
Report which signals fired and how many.

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

## Git conventions

Commit messages:
- `daily: log YYYY-MM-DD`
- `weekly: review YYYY-WNN`
- `training: [what changed]`
- `project: [name] — [what changed]`
- `principle: [title]`
- `system: [what changed]`
