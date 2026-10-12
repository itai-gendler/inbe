---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Delete session — remaining wim hof
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
- text: The selected saved result exists in active history; deleting an exposed value either retains positive values
    or removes the last-value result.
  kind: condition
  entities:
  - entity: wim-hof-session
    effect: reads
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Retention values
    - Mood
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
- text: One Wim Hof value is removed while remaining values retain the saved record.
  kind: product
  entities:
  - entity: wim-hof-session
    effect: changes
    facts:
    - Retention values
  - entity: habit-day
    effect: changes
    facts:
    - Stored count
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Completed
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/habits/habit_session_screen.zi
- kind: code
  role: implementation
  target: src/storage/storage_sessions.zi
- kind: code
  role: implementation
  target: src/habits/habit_sessions.zi
- kind: code
  role: implementation
  target: src/practices/whm/whm_session.zi
---

# Delete session — remaining wim hof

## Trigger

Delete session — remaining wim hof.

## Outcome

One Wim Hof value is removed while remaining values retain the saved record.
