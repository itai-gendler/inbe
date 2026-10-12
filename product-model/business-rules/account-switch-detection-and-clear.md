---
appliesTo:
- type: entity
  id: account
- type: entity
  id: habit
- type: entity
  id: habit-day
- type: entity
  id: list
- type: entity
  id: todo
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
  target: src/storage/sync_account.zi
- kind: code
  role: implementation
  target: apps/habits/habits.zi
- kind: code
  role: implementation
  target: src/habits/habit_actions.zi
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Account switch detection and replacement have distinct scopes

Switch confirmation detection checks practice/Habit data. Replacement SQL additionally clears Lists/Todos, social snapshots and outbox; Diary/Lumi cell records and every setting are not demonstrated cleared. Identical credentials bypass a reset.
