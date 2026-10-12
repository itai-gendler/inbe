---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to complete the referenced day
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
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
      place: desktop-app::lumi
  actor: user
- text: Repeating explicit completion leaves the day at or above target and completed; it does not uncomplete it.
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
      place: desktop-app::lumi
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
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Complete habit day — lumi repeat

## Trigger

Complete habit day for the selected definition or date.

## Outcome

Repeating explicit completion leaves the day at or above target and completed; it does not uncomplete it.
