---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Uncomplete habit day for the selected definition or date
  kind: actor
  entities:
  - entity: habit-day
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::habits
  actor: user
- text: The ordinary date is already completed and its counting/linking mode determines whether manual completion
    can be reversed rather than entering linked controls.
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
- text: Eligible ordinary manual completion is reversed; linked/counter interaction retains its distinct controls
    and derived floor.
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

# Uncomplete habit day — ordinary

## Trigger

Uncomplete habit day for the selected definition or date.

## Outcome

Eligible ordinary manual completion is reversed; linked/counter interaction retains its distinct controls and derived floor.
