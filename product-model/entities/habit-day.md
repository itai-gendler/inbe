---
domain: habits
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_linked_rules.zi
---

# Habit day

A Habit on a date, with stored and derived progress.

## Information kept

- **Habit** — Habit definition to which this dated progress belongs.
- **Date** — Local calendar date of the progress.
- **Stored count** — Count persisted for this Habit and date, before the visible linked-count maximum.
- **Stored completion** — Persisted completion flag, including the legacy completion fallback.
- **Materialized baseline** — Persisted matching-session contribution rebuilt by the materialization paths and their preservation predicates.
- **Visible linked count** — Number of matching saved sessions on this date in loaded linked history; each session contributes one, regardless of rounds, duration or repetitions.
- **Effective count** — Maximum of stored count and visible linked count; visible history and stored materialization can have different query scopes.
- **Scheduled** — Whether the selected date matches the schedule.
- **Completed** — Derived completion using target and linked/stored progress.
