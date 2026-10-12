---
appliesTo:
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

# Explicit Habit completion retains at least target progress

Set count to max(effective progress, target), persist successfully before updating memory, and retain completion on repetition rather than toggling it off.
