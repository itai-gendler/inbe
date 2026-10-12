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

# Practice finish can set incomplete stored day progress to one

The finish helper writes one when stored completion is false; it does not universally preserve larger incomplete stored counts.
