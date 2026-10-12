---
kind: primary
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
      place: desktop-app::habit-day
  actor: user
- text: The selected date uses the overview effective count or detail stored count as its starting expression, then
    clamps the decrement against visible linked sessions.
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
      place: desktop-app::habit-day
  actor: user
- text: The detail handler starts from stored count. It applies one decrement and clamps against the visible linked
    floor before persisting and refreshing completion.
  kind: product
  entities:
  - entity: habit-day
    effect: changes
    facts:
    - Stored count
    - Stored completion
    - Effective count
    - Completed
  contexts:
    desktop:
      place: desktop-app::habit-day
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

# Decrease habit count — detail

## Trigger

Decrease habit count for the selected definition or date.

## Outcome

The detail handler starts from stored count. It applies one decrement and clamps against the visible linked floor before persisting and refreshing completion.
