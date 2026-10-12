---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Exit practice — partial save meditation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: The unfinished originating process and its pause and elapsed/completed progress determine whether discard,
    qualifying partial save or cancellation is offered.
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
- text: At least sixty elapsed seconds are saved on this exit. The live process ends and returns to its start process,
    without the normal result or Lumi summary route.
  kind: product
  entities:
  - entity: meditation-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Duration
    - Mood
  - entity: meditation-practice
    effect: removes
    from: Running
  - entity: habit-day
    effect: changes
    facts:
    - Stored count
    - Stored completion
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Completed
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

# Exit practice — partial save meditation

## Trigger

Exit practice — partial save meditation.

## Outcome

At least sixty elapsed seconds are saved on this exit. The live process ends and returns to its start process, without the normal result or Lumi summary route.
