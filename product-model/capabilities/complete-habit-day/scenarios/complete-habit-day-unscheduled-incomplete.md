---
kind: validation
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
- text: The selected overview date is unscheduled and derived incomplete, so no ordinary day-progress edit is performed.
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
- text: An incomplete unscheduled day does not perform the ordinary progress action. A completed unscheduled day
    remains a distinct eligible case.
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

# Complete habit day — unscheduled incomplete

## Trigger

Complete habit day for the selected definition or date.

## Outcome

An incomplete unscheduled day does not perform the ordinary progress action. A completed unscheduled day remains a distinct eligible case.
