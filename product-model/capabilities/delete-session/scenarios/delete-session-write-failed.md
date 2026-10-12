---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Delete session — write failed
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
- text: The selected whole-record removal or exposed positive-value replacement fails in the addressed saved family.
  kind: condition
  entities:
  - entity: wim-hof-session
    effect: reads
    facts:
    - Identity
    - Retention values
  - entity: meditation-session
    effect: reads
    facts:
    - Identity
    - Duration
  - entity: patterns-session
    effect: reads
    facts:
    - Identity
    - Recorded duration values
  - entity: sun-salutation-session
    effect: reads
    facts:
    - Identity
    - Repetitions
  - entity: habit-day
    effect: reads
    facts:
    - Date
    - Stored count
    - Visible linked count
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
- text: Report the storage failure without claiming successful removal or replacement
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
---

# Delete session — write failed

## Trigger

Delete session — write failed.

## Outcome

Failed removal or replacement is reported; the requested record change is not claimed successful.

## Edge cases

- The same outcome applies to Wim Hof, Meditation, Breathing Patterns, Sun Salutation through their exposed saved-history controls.
