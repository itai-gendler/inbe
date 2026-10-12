---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Browse sessions — linked history patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
- text: The selected date and practice links filter the latest forty-eight undeleted saved records; each matching
    record contributes one linked session.
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
- text: Latest-48 undeleted saved records are filtered by selected date and practice links. Each matching record
    counts once, regardless of rounds, seconds or repetitions; broader materialization is separate.
  kind: product
  entities: []
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

# Browse sessions — linked history patterns

## Trigger

Browse sessions — linked history patterns.

## Outcome

Latest-48 undeleted saved records are filtered by selected date and practice links. Each matching record counts once, regardless of rounds, seconds or repetitions; broader materialization is separate.
