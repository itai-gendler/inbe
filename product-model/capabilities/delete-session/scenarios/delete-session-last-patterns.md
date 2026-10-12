---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Delete session — last patterns
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
  - entity: patterns-session
    effect: reads
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Recorded duration values
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
- text: The selected whole result, or result losing its last positive exposed value, leaves active history. Habit
    progress is refreshed with the actual preservation expression.
  kind: product
  entities:
  - entity: patterns-session
    effect: removes
  - entity: habit-day
    effect: changes
    facts:
    - Stored count
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Completed
  - entity: habit
    effect: reads
    facts: []
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
  target: src/practices/patterns/patterns_practice.zi
---

# Delete session — last patterns

## Trigger

Delete session — last patterns.

## Outcome

The selected whole result, or result losing its last positive exposed value, leaves active history. Habit progress is refreshed with the actual preservation expression.
