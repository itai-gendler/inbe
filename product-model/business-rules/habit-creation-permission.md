---
appliesTo:
- type: entity
  id: habit
  effect: creates
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Habit creation

User saves a trimmed, unique native definition within capacity, or imports a supported definition. Current-context incoming records can add absent definitions with defaults for fields not exchanged.
