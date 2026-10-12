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

# Effective Habit progress is the stored-linked maximum

Effective count is max(stored count, visible matching linked-session count). Counter completion compares it to the target; noncounter/legacy stored completion follows the implemented fallback.
