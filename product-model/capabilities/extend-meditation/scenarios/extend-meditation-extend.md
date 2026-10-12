---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Extend meditation — extend
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: Extension controls are enabled for the live process; the selected extension increases configured duration
    and remaining time, including from awaiting finish.
  kind: condition
  entities:
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Duration
    - Remaining time
    - Elapsed progress
    - Extension state
    - Waiting state
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
  - entity: meditation-settings
    effect: reads
    facts:
    - Duration mode
    - Custom minutes
    - Interval bell
    - Extension controls
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: The selected extension increases duration and remaining time, clears awaiting finish and resumes interval/music
    behavior; extension is also usable before waiting.
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Duration
    - Remaining time
    - Waiting state
    - Extension state
    from: Awaiting finish
    to: Running
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
references:
- kind: code
  role: implementation
  target: src/practices/practice_actions.zi
- kind: code
  role: implementation
  target: src/app/activity_start.zi
- kind: code
  role: implementation
  target: src/practices/session_results.zi
- kind: code
  role: implementation
  target: src/practices/meditation/meditation_session.zi
---

# Extend meditation — extend

## Trigger

Extend meditation — extend.

## Outcome

The selected extension increases duration and remaining time, clears awaiting finish and resumes interval/music behavior; extension is also usable before waiting.
