# 🏠 Ironman Belgium 2027 — Mission Control

```base
filters:
  and:
    - file.inFolder("Log/Weeks")
    - kind == "training-week"
    - week_start <= today()
    - week_end >= today()
formulas:
  days_to_race: ((number(date("2027-09-05")) - number(today())) / 86400000).round(0)
  weeks_to_race: (formula.days_to_race / 7).floor()
properties:
  note.week_number:
    displayName: Week (of 49)
  note.phase:
    displayName: Phase
  formula.days_to_race:
    displayName: Days to race
  formula.weeks_to_race:
    displayName: Weeks to race
views:
  - type: table
    name: Countdown
    order:
      - week_number
      - phase
      - formula.days_to_race
      - formula.weeks_to_race
```

## ✅ Today

> Updates automatically by date. Click a cell to enter Done / Skipped / Actual / RPE / Hours / Metrics / Notes.

![[Log/Today.base]]

---

## 🎯 This Week

> Full history (all weeks and days) → [[Log/Training Metrics]]

![[Log/This Week.base]]

### 📅 Current Week Overview

> Open the week note for the full plan and reflection. All weeks → [[Log/Training Metrics]]

![[Log/Current Week.base]]

### 🔜 Next Key Sessions

> Upcoming long rides, long runs and Thursday intervals.

```base
filters:
  and:
    - file.inFolder("Log/Days")
    - kind == "training-day"
    - date >= today()
    - or:
        - planned.contains("Long Bike")
        - planned.contains("Long Run")
        - planned.contains("Bike intervals")
properties:
  note.date:
    displayName: Date
  note.weekday:
    displayName: Day
  note.planned:
    displayName: Session
views:
  - type: table
    name: Next Key Sessions
    limit: 4
    order:
      - date
      - weekday
      - planned
    sort:
      - property: date
        direction: ASC
```

---

## 📍 Quick Navigation

| Section | Link |
|---|---|
| 🗺️ Training Plan Overview | [[Plan/00 Training Plan Overview]] |
| 📅 Monthly Calendar | [[Plan/01 Monthly Calendar]] |
| 📋 Phase Guide | [[Plan/02 Phases and Reasoning]] |
| 🗓️ Week-by-Week Schedule | [[Plan/03 Week by Week Schedule]] |
| 🏊 Swim Sessions | [[Workouts/Swim]] |
| 🚴 Bike Sessions | [[Workouts/Bike]] |
| 🏃 Run Sessions | [[Workouts/Run]] |
| 🧱 Brick Sessions | [[Workouts/Brick]] |
| 💪 Strength Training | [[Workouts/Strength]] |
| 🍌 Nutrition & Fueling | [[Support/Nutrition and Fueling]] |
| 🔄 Recovery & Adjustments | [[Support/Recovery and Adjustments]] |
| 📏 Baseline Tests | [[Support/Baseline Tests]] |
| 📊 Training Metrics | [[Log/Training Metrics]] |

---

## 📊 Phase Overview

| Phase | Dates | Weeks | Weekly Hours | Focus |
|---|---|---|---|---|
| 🟢 **Phase 1 — Foundation** | Sep 28 – Dec 27, 2026 | 1–13 | 7–10 h | Build habit, aerobic base, swim technique |
| 🔵 **Phase 2 — Base Build** | Dec 28, 2026 – Mar 28, 2027 | 14–26 | 10–13 h | Volume, long rides, run durability |
| 🟡 **Phase 3 — Pre-Exam Maintenance** | Mar 29 – Jul 4, 2027 | 27–40 | 7–9 h | Maintain fitness, protect exam prep |
| 🔴 **Phase 4 — Peak Build** | Jul 5 – Aug 8, 2027 | 41–45 | 14–15 h | Race-specific intensity, long bricks |
| ⚫ **Phase 5 — Taper** | Aug 9 – Sep 5, 2027 | 46–49 | 8→3 h | Shed fatigue, stay sharp |

> Every Thursday = bike intervals + run intervals (eased in Week 16). On leave 24 Dec 2026 – 9 Jan 2027 (no training), so Weeks 13–15 are far below the hours shown.

---

## ⚠️ Key Dates & Flags

| Date | Note |
|---|---|
| 2 Oct 2026 | **Training starts** |
| 24 Dec 2026 – 9 Jan 2027 | **On leave — no training sessions** |
| 6 Jan 2027 | Epiphany (BW holiday) |
| 26 Mar 2027 | Good Friday (BW holiday) |
| 29 Mar 2027 | Easter Monday (BW holiday) |
| 6 May 2027 | Ascension Day (BW holiday) |
| 17 May 2027 | Whit Monday (BW holiday) |
| 27 May 2027 | Corpus Christi (BW holiday) |
| ~4 Jul 2027 | **Exam done — Peak phase begins** |
| 8–22 Aug 2027 | Final long sessions, then taper entry |
| 5 Sep 2027 | 🏁 **RACE DAY — IRONMAN Belgium** |

---

*Vault created: 2 October 2026 · Powered by evidence-based triathlon coaching principles*
