---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Edit session — patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
- text: The selected Wim Hof or Breathing Patterns recorded value is positive and editable through the at-most-three-digit
    input; other saved families have no such editor.
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
- text: The selected positive recorded value is replaced and history is refreshed using the implemented old-count
    preservation formula. Meditation and Sun Salutation have no corresponding round editor.
  kind: product
  entities:
  - entity: patterns-session
    effect: changes
    facts:
    - Recorded duration values
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
  target: src/practices/patterns/patterns_practice.zi
---

# Edit session — patterns

## Trigger

Edit session — patterns.

## Outcome

The selected positive recorded value is replaced and history is refreshed using the implemented old-count preservation formula. Meditation and Sun Salutation have no corresponding round editor.
