---
appliesTo:
- type: entity
  id: habit
- type: entity
  id: habit-day
- type: entity
  id: list
- type: entity
  id: todo
- type: entity
  id: device-settings
- type: entity
  id: apps-settings
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
  target: src/storage/storage_elist.zi
- kind: code
  role: implementation
  target: src/screens/settings/settings_device.zi
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
---

# Import merges demonstrated data and whitelisted preferences

Positive canonical sessions deduplicate, check-ins import when new and Habit-day import uses maximum handling. Description/schedule/reminder and credentials are not universally restored. OneList is bounded four MB. ZIP exports an unredacted SQLite snapshot, not a guaranteed full restoration contract.
