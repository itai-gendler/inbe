---
appliesTo:
- type: entity
  id: habit
  effect: removes
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Habit removal

User confirms definition deletion or clears the relevant local SQL scope. Accepted incoming deletion markers remove definitions from active history; tombstones and associated dated progress follow their implemented paths.
