---
appliesTo:
- type: entity
  id: habit-day
  effect: changes
references:
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Habit day change

User changes dated count/completion through overview, detail or explicit Lumi completion. Matching practice completion and incoming application use their distinct count and preservation expressions; ordinary overview and Lumi gates narrow only their stated contexts.
