---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Edit session — invalid value
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::habit-day
  actor: user
- text: The proposed value is nonpositive or invalid within the at-most-three-digit input path.
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
- text: Report the rejected value without persisting an edit
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

# Edit session — invalid value

## Trigger

Edit session — invalid value.

## Outcome

Nonpositive or invalid edited values are refused; the editor accepts at most three digits through its input path.

## Edge cases

- The same outcome applies to Wim Hof, Breathing Patterns through their exposed saved-history controls.
