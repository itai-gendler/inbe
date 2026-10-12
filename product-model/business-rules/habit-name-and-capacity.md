---
appliesTo:
- type: entity
  id: habit
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

# Native Habit names are trimmed unique and bounded

Trim spaces/tabs, refuse blank names and loaded-set duplicates, and refuse native definition creation above 32 Habits.
