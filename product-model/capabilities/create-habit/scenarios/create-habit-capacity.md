---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Create habit for the selected definition or date
  kind: actor
  entities:
  - entity: habit
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::habit
  actor: user
- text: Thirty-two loaded native definitions already occupy the creation capacity.
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
- text: The native 32-Habit capacity refuses another definition.
  kind: product
  entities:
  - entity: habit
    effect: reads
    facts: []
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

# Create habit — capacity

## Trigger

Create habit for the selected definition or date.

## Outcome

The native 32-Habit capacity refuses another definition.
