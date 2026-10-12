---
appliesTo:
- type: entity
  id: habit-day
  effect: removes
references:
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Habit day removal

Definition deletion and scoped clearing remove associated dated progress. Replacement/reconciliation uses the implemented SQL scope rather than a universal reset of unrelated records.
