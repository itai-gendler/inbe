---
appliesTo:
- type: entity
  id: habit
- type: entity
  id: habit-day
- type: entity
  id: wim-hof-session
- type: entity
  id: meditation-session
- type: entity
  id: patterns-session
- type: entity
  id: sun-salutation-session
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

# Each matching saved session contributes one linked count

Match selected local date and linked activity mask. Count saved sessions, not positive values, rounds, breaths, seconds or repetitions.
