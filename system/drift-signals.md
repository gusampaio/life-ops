# Drift Signals

Patterns that indicate the system is drifting from baseline. These are observed from data — not rules imposed upfront.

Check weekly. Flag when thresholds are hit. Two or more signals in the same week = surface a warning in the weekly review.

---

## Signals

| Signal | Field | Threshold | Notes |
|--------|-------|-----------|-------|
| sleep | `sleep` | 2+ consecutive broken/late | Consecutive matters — one bad night is noise |
| screen | `screen_first` | instagram/social 3+ mornings | First action sets the tone for the day |
| training | `training` | any unplanned "no" | Planned rest days don't count |
| deep work | `deep_work` | 3+ reactive days in a row | Reactive by choice is different from reactive by default |
| mind | `mind` | 3+ "neither" in a row | Reading or meditation — either counts |
| energy | `energy` | avg below 2.5 for the week | Compute from all 7 days |
| mood | `mood` | avg below 2.5 for the week | Compute from all 7 days |

---

## Patterns (populate after 4–6 weeks of data)

This section is intentionally empty at the start. Patterns will emerge from the data — don't pre-fill aspirationally.

Examples of what might appear over time:
- "screen_first=instagram always follows sleep=broken the night before"
- "deep_work=no correlates with high meeting load on Tuesdays"
- "mood drops below 3 after 3+ consecutive rest days without training"

Track these here once you have enough data to trust them.
