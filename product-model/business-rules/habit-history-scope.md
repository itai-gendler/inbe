---
appliesTo:
- type: entity
  id: habit-day
- type: entity
  id: wim-hof-session
- type: entity
  id: meditation-session
- type: entity
  id: patterns-session
- type: entity
  id: sun-salutation-session
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

# Visible linked history uses the latest forty-eight undeleted sessions

The native record loader is bounded to latest 48 and does not apply the same user predicate as broader materialization and account-scoped chart queries. Selected date and links then filter the visible set.
