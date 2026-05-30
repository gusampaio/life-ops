---
name: setup
description: First-time setup walkthrough for a new life-os fork. Fills in who-i-am.md, configures training schedule, sets up the finances file. Run once after forking.
disable-model-invocation: true
---

Guide the user through setting up their life-os for the first time. This is a conversational walkthrough — ask questions, then write the files based on their answers.

## Steps

### 1. Check current state
Read `who-i-am.md` and `training/program.md`. If `who-i-am.md` still contains the default template text ("Gustavo Sampaio" or the fork prompt), proceed with setup. If it's already personalized, confirm with the user before overwriting anything.

### 2. Gather identity info
Ask these questions (can be answered in one message):

- What's your name?
- What do you do for work? (role + company/context, one line)
- Where are you based?
- What are your main physical activities? (e.g. running, gym, yoga, cycling — these become training link types)
- Do you have any personal projects you want to track? (name + one-line description each)
- Do you have different schedule modes? (e.g. travel vs home base, seasonal changes) If yes, describe each.

### 3. Write `who-i-am.md`
Using their answers, write a clean `who-i-am.md`:

```markdown
# Who I am

> Fill this in when you fork life-os. Claude reads it for context on who you are.

- **Name**: [name]
- **Role**: [role]
- **Based in**: [location]
- **Active in**: [activities]
[if projects:] - **Projects**: [project — description], ...

[if modes:]
## Operating modes

### [Mode name]
[schedule and priorities]
```

### 4. Customize training links
Based on their activities, update the topic links section of `CLAUDE.md` to replace the example training types with theirs. If they don't have a specific activity (e.g. no BJJ), remove that link. If they have others not listed, add them.

### 5. Set up finances file
Ask: "Do you want to track finances? (investments, big purchases, savings goals — optional but useful)"

If yes, check if `projects/investments.md` or `projects/finances.md` already exists. If not, create `projects/finances.md` with this structure:

```markdown
# Finances

Last updated: [today]

---

## Big purchases log

One-off expenses worth tracking. Log anything above your personal threshold.

| Date | Item | Amount | Notes |
|------|------|--------|-------|
| | | | |

---

## Monthly review

*First of each month — answer these questions:*

1. Did total savings/portfolio grow or shrink vs last month?
2. Did I invest or save anything new? If not, why?
3. Any big purchases last month?
4. One financial decision to make or defer.

| Month | Total | Change | Action taken |
|-------|-------|--------|--------------|
| | | | |
```

### 6. Confirm and commit
Show the user a summary of what was written. Ask if anything needs adjusting. Then commit:

```
git add who-i-am.md training/program.md [finances file if created]
git commit -m "system: initial setup — who-i-am + personal config"
```

### 7. First log
Ask: "Want to log today now? I can walk you through your first daily entry."

If yes, proceed with the daily log format from CLAUDE.md.
