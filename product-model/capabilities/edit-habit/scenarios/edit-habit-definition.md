---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Edit habit for the selected definition or date
  kind: actor
  entities:
  - entity: habit
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::habit
  actor: user
- text: The entered name is trimmed and checked against other loaded definitions; description, links, counting and
    schedule identify the local fields being edited.
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
      place: desktop-app::habit
  actor: user
- text: Definition edits persist; description is locally saved and is absent from mapped exchanged Habit fields.
  kind: product
  entities:
  - entity: habit
    effect: changes
    facts:
    - Name
    - Description
    - Color
    - Practice links
    - Linking mode
    - Counting mode
    - Target
    - Schedule
    - Reminder hour
  contexts:
    desktop:
      place: desktop-app::habit
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

# Edit habit — definition

## Trigger

Edit habit for the selected definition or date.

## Outcome

Definition edits persist; description is locally saved and is absent from mapped exchanged Habit fields.
