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

# Habit adjustments clamp at the visible linked floor

Overview starts from max(stored, linked); detail starts from stored. Apply the requested delta and clamp against linked count. These are distinct starting expressions.
