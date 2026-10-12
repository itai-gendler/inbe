---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Complete habit day for the selected definition or date
  kind: actor
  entities:
  - entity: habit-day
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::habits
  actor: user
- text: The selected date uses its schedule, counting mode, links and derived completion; an incomplete unscheduled
    overview date has no completion interaction.
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
- text: An eligible binary manual day is completed. Counting and linked-day selections enter their controls rather
    than blindly toggling a flag.
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

# Complete habit day — ordinary

## Trigger

Complete habit day for the selected definition or date.

## Outcome

An eligible binary manual day is completed. Counting and linked-day selections enter their controls rather than blindly toggling a flag.
