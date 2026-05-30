---
name: drift-check
description: Check the last 7 daily logs for drift signals and report which thresholds fired. Read-only — no files written.
---

Read the last 7 daily log files in `daily/` and check each drift signal defined below. Report results clearly.

## Thresholds

| Signal | Condition | Flag? |
|--------|-----------|-------|
| sleep | 2+ consecutive days with `broken` or `late` | yes |
| screen_first | `instagram`, `whatsapp`, or any social media on 3+ days (not necessarily consecutive) | yes |
| training | any day with unplanned `no` (rest-day is not a flag) | yes |
| deep_work | 3+ consecutive days with `no — reactive day` | yes |
| mind | 3+ consecutive days with `neither` | yes |
| energy avg | average below 2.5 for the 7-day window | yes |
| mood avg | average below 2.5 for the 7-day window | yes |

## Output format

```
## Drift check — last 7 days (YYYY-MM-DD → YYYY-MM-DD)

| Signal | Status | Detail |
|--------|--------|--------|
| sleep | ✓ ok / ⚠ flagged | [e.g. broken May 28–29] |
| screen_first | ✓ ok / ⚠ flagged | [e.g. instagram 3 days] |
| training | ✓ ok / ⚠ flagged | [e.g. unplanned no on May 27] |
| deep_work | ✓ ok / ⚠ flagged | [e.g. 3 reactive in a row May 25–27] |
| mind | ✓ ok / ⚠ flagged | [e.g. neither 4 days straight] |
| energy avg | ✓ ok / ⚠ flagged | [e.g. 2.1 avg] |
| mood avg | ✓ ok / ⚠ flagged | [e.g. 2.3 avg] |

**Signals fired: N/7**
[If 2+: surface a warning and note the pattern.]
```

Do not write any files. Just report.
