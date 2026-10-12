---
appliesTo:
- type: entity
  id: habit
- type: entity
  id: habit-day
references:
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
- kind: code
  role: implementation
  target: src/habits/habit_sessions.zi
- kind: code
  role: implementation
  target: src/storage/storage_habit_materialize.zi
---

# Habit schedules and targets determine day summaries

A zero schedule means daily. Nonzero weekday masks determine scheduled dates; native counter targets are bounded one through ninety-nine. Eligible ordinary dates do not extend into the future.
