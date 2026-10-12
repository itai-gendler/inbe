---
kind: validation
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
- text: Trimming the replacement name leaves no nonblank content.
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
- text: Whitespace-only names are refused after trimming; no definition is saved.
  kind: product
  entities: []
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

# Edit habit — blank

## Trigger

Edit habit for the selected definition or date.

## Outcome

Whitespace-only names are refused after trimming; no definition is saved.
