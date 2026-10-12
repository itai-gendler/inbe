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

# Habit rematerialization follows each mutation predicate

Session/history mutation preservation uses the actual old-count expression. Materialization is broader than the latest-48 visible history and is not one universal additive or monotonic rule.
