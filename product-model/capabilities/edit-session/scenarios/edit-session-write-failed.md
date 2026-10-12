---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Edit session — write failed
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
- text: Replacement of the selected positive saved value fails in the Wim Hof or Breathing Patterns editor.
  kind: condition
  entities:
  - entity: wim-hof-session
    effect: reads
    facts:
    - Identity
    - Retention values
  - entity: patterns-session
    effect: reads
    facts:
    - Identity
    - Recorded duration values
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

# Edit session — write failed

## Trigger

Edit session — write failed.

## Outcome

Failed replacement reports the write failure and does not claim a saved edit.

## Edge cases

- The same outcome applies to Wim Hof, Breathing Patterns through their exposed saved-history controls.
