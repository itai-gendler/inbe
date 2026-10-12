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

# Habit conflicts follow distinct ordering and import paths

Ordinary timestamp ordering, equal-time protection, duplicate-name reconciliation and import maximum counts are distinct; no universal maximum merge is asserted.
