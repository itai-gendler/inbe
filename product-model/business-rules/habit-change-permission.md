---
appliesTo:
- type: entity
  id: habit
  effect: changes
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Habit change

User edits definition facts or ordering; local description remains outside the exchanged definition fields. Accepted current-context incoming records use timestamp, pending-edit and duplicate-name reconciliation predicates.
