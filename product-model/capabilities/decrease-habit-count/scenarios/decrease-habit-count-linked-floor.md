---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Decrease habit count for the selected definition or date
  kind: actor
  entities:
  - entity: habit
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::habits
  actor: user
- text: The proposed decrement would fall below visible matching sessions, so the floor keeps linked effective progress.
  kind: condition
  entities:
  - entity: habit
    effect: reads
    facts:
    - Identity
    - Name
    - Description
    - Color
    - Order
    - Practice links
    - Linking mode
    - Counting mode
    - Target
    - Schedule
    - Reminder hour
  - entity: habit-day
    effect: reads
    facts:
    - Habit
    - Date
    - Stored count
    - Stored completion
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Scheduled
    - Completed
  contexts:
    desktop:
      place: desktop-app::habits
  actor: user
- text: The decrement cannot reduce effective progress below matching visible saved sessions.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::habits
  actor: user
references:
- kind: code
  role: implementation
  target: apps/habits/habits.zi
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

# Decrease habit count — linked floor

## Trigger

Decrease habit count for the selected definition or date.

## Outcome

The decrement cannot reduce effective progress below matching visible saved sessions.
