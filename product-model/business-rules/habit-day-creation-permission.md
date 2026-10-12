---
appliesTo:
- type: entity
  id: habit-day
  effect: creates
references:
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Habit day creation

User operations or supported imports can establish dated progress for an existing definition. Matching session materialization and accepted current-context incoming records can create a previously absent dated record.
