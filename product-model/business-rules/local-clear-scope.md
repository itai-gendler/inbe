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
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Local clear removes the practice and Habit scope

Without account setup the implementation physically deletes its practice/Habit/day scope; with an account it retains tombstones/zero-day values and queues deletes. Lists, Diary, Lumi and general settings are outside the clear scope. RAM and SQL effects need not be globally atomic.
