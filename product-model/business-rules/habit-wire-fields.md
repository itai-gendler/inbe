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

# Habit description remains local in the mapped exchange

The locally persisted description is omitted from mapped inbound/outbound Habit definition fields. Linking mode is not an account-sync opt-out.
