---
name: weekly-review
description: Generate the weekly review for a given week from daily logs. Reads all daily files, computes averages, runs drift check, writes weekly/YYYY-WNN.md, and commits.
disable-model-invocation: true
---

Generate a weekly review for this life-os repo.

## How to invoke

User types `/weekly-review` optionally followed by a week identifier (e.g. `W21` or `2026-W21`). If no argument is given, infer the most recently completed week from the daily logs.

## Steps

1. **Identify the week**: Determine which Mon–Sun range to cover. List `daily/` to find the relevant files (YYYY-MM-DD.md for that week's dates).

2. **Read all daily files** for that week. If a day has no file, treat all its fields as missing.

3. **Compute from the data**:
   - Training sessions completed: count days where `training` = `yes` or `partial`. Note which were missed and why.
   - Deep work days: count `deep_work = yes`. Reactive days: count `no — reactive day`.
   - Mind days: reading = days where `mind` includes "reading". Meditation = days where `mind` includes "meditation".
   - Energy avg: average of all `energy` values (1–5).
   - Mood avg: average of all `mood` values (1–5).
   - Best day: highest energy+mood combo. Worst day: lowest.

4. **Run drift check** (same logic as `/drift-check`):
   - sleep: 2+ consecutive `broken` or `late` → flag
   - screen_first: `instagram`, `whatsapp`, or social media 3+ days → flag
   - training: any unplanned `no` → flag
   - deep_work: 3+ consecutive `no — reactive day` → flag
   - mind: 3+ consecutive `neither` → flag
   - energy avg below 2.5 → flag
   - mood avg below 2.5 → flag
   - Count how many signals fired.

5. **Write the review** to `weekly/YYYY-WNN.md` using this exact format:

```markdown
# Week YYYY-WNN (Mon DD Mon — Sun DD Mon)

## Training
- Sessions completed: N/7
- Missed: [which ones and why, or "none"]
- BJJ notes: [from daily notes, or "—"]
- Gym: [from daily notes, or "—"]

## Work
- Deep work days: N/5
- Reactive days: N/5
- Key shipped: [what moved forward]
- Blockers: [what slowed things down]

## Mind
- Reading days: N/7
- Meditation days: N/7
- Book: [current book from daily notes, or "—"]

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
[one sentence — ask Gustavo if not obvious from context]
```

6. **Commit**: `git add weekly/YYYY-WNN.md && git commit -m "weekly: review YYYY-WNN"`

7. Ask Gustavo to confirm or adjust the "Note" and "Next week intention" sections before committing if they need personalisation.
