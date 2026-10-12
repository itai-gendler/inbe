---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Reorder habits for the selected definition or date
  kind: actor
  entities:
  - entity: habit
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::habits
  actor: user
- text: The loaded definitions and their current positions identify the reordered sequence to persist.
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
- text: The chosen order persists.
  kind: product
  entities:
  - entity: habit
    effect: changes
    facts:
    - Order
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

# Reorder habits — order

## Trigger

Reorder habits for the selected definition or date.

## Outcome

The chosen order persists.
