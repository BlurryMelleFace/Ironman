# Training Metrics — IRONMAN Belgium 2027

> Log every session in the **Today** table on the [[Dashboard]]. Consistent logging reveals patterns — when you're fatigued, when your best sessions happen, and which disciplines need attention.

> This page is the single place for history: weekly overview, daily log, monthly summary and race-day log.

---

## Weeks

One row per week. Days done, actual hours and average RPE are calculated from what you log in the Today table, so there is nothing to type here.

```base
filters:
  and:
    - file.inFolder("Log/Weeks")
    - kind == "training-week"
    - week_start != null
formulas:
  week_status: if(week_start <= today() && week_end >= today(), "0 Current", if(week_start > today(), "1 Upcoming", "2 Completed"))
  days_done: days.filter(value.asFile().properties.done == true).length
  days_skipped: days.filter(value.asFile().properties.skipped == true).length
  hours_actual: days.map(value.asFile().properties.hours).filter(value.isTruthy()).map(number(value)).reduce(acc + value, 0)
  rpe_values: days.map(value.asFile().properties.rpe).filter(value.isTruthy()).map(number(value))
  avg_rpe: if(formula.rpe_values.length > 0, (formula.rpe_values.reduce(acc + value, 0) / formula.rpe_values.length).round(1), "")
properties:
  formula.week_status:
    displayName: Status
  formula.days_done:
    displayName: Days done
  formula.days_skipped:
    displayName: Days skipped
  formula.hours_actual:
    displayName: Actual (h)
  formula.avg_rpe:
    displayName: Avg RPE
  note.week_number:
    displayName: Week
  note.week_start:
    displayName: Start
  note.phase:
    displayName: Phase
  note.hours_planned:
    displayName: Planned (h)
  note.long_bike_planned:
    displayName: Long Bike Planned
  note.long_run_planned:
    displayName: Long Run Planned
  note.swim_planned:
    displayName: Swim Planned
  note.quality_planned:
    displayName: Quality Planned
  note.strength_planned:
    displayName: Strength Planned (sessions)
views:
  - type: table
    name: Weekly Log
    groupBy:
      property: formula.week_status
      direction: ASC
    order:
      - file.name
      - week_number
      - week_start
      - phase
      - hours_planned
      - formula.hours_actual
      - formula.days_done
      - formula.days_skipped
      - formula.avg_rpe
      - long_bike_planned
      - long_run_planned
      - swim_planned
      - quality_planned
      - strength_planned
    sort:
      - property: week_start
        direction: ASC
```

## Days

Every logged day, grouped by week with completed-day counts, average RPE and total hours.

```base
filters:
  and:
    - file.inFolder("Log/Days")
    - kind == "training-day"
    - date <= today()
properties:
  note.weekday:
    displayName: Day
  note.date:
    displayName: Date
  note.week_number:
    displayName: Week
  note.planned:
    displayName: Planned
  note.done:
    displayName: Done
  note.skipped:
    displayName: Skipped
  note.actual:
    displayName: Actual
  note.rpe:
    displayName: RPE
  note.hours:
    displayName: Hours
  note.metrics:
    displayName: Metrics
  note.notes:
    displayName: Notes
views:
  - type: table
    name: Daily Log
    groupBy:
      property: note.week_number
      direction: DESC
    order:
      - date
      - weekday
      - planned
      - done
      - skipped
      - actual
      - rpe
      - hours
      - metrics
      - notes
    sort:
      - property: date
        direction: ASC
    summaries:
      done: Checked
      skipped: Checked
      rpe: Average
      hours: Sum
```

---

## How to Log

| Field | What to write |
|---|---|
| **Done** | Tick when the planned session is completed |
| **Skipped** | Tick when you deliberately skipped the session (leave both unticked for "not logged yet") |
| **Actual** | What you actually did (e.g. "55 min, felt heavy") |
| **RPE** | Rate of Perceived Exertion: 1 (very easy) → 10 (maximum) |
| **Hours** | Training time as a number (e.g. 1.5) — adds up to the weekly total |
| **Metrics** | Heart rate, pace, power, distance, weight, etc. |
| **Notes** | Anything relevant — form cues, nutrition, fatigue, highlights |

**RPE Quick Guide:**
- 1–3: Recovery, easy walk/jog, barely working
- 4–5: Zone 2, conversational, comfortable
- 6–7: Zone 3, noticeably harder
- 8–9: Zone 4–5, interval effort, breathing hard
- 10: Maximum, can't hold for long

---

## Monthly Summary Table

> Fill in at the end of each month for a quick overview.

| Month | Swim (sessions / km) | Bike (sessions / hours) | Run (sessions / hours) | Strength | Total Hours | Notes |
|---|---|---|---|---|---|---|
| October 2026 | | | | | | |
| November 2026 | | | | | | |
| December 2026 | | | | | | |
| January 2027 | | | | | | |
| February 2027 | | | | | | |
| March 2027 | | | | | | |
| April 2027 | | | | | | |
| May 2027 | | | | | | |
| June 2027 | | | | | | |
| July 2027 | | | | | | |
| August 2027 | | | | | | |
| **Total** | | | | | | |

---

## 🏁 Race Day Log

**IRONMAN Belgium · 5 September 2027 · Knokke-Heist**

| Segment | Target | Actual | Notes |
|---|---|---|---|
| Swim 3.8 km | 1:15–1:25 h | | |
| T1 | ~10 min | | |
| Bike 180 km | 5:30–6:00 h | | |
| T2 | ~8 min | | |
| Run 42.2 km | 5:30–6:00 h | | |
| **Total** | **<14:00 h** | | |

**How did you feel at each stage?**
- After swim:
- At 60 km bike:
- At 120 km bike:
- At 10 km run:
- At 30 km run:
- Finish line:

**Nutrition notes:**
- Did the fueling strategy work?
- Any GI issues?
- What would you change?

**Overall:**
- 

---

*Back to [[../Dashboard]]*