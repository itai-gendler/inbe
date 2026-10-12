---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Start practice — lumi meditation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested family, existing local process and fresh remote activity determine new start, same-process
    restoration or refusal; saved configuration supplies the new run.
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
      place: desktop-app::lumi
  actor: user
- text: A new originating Meditation process starts from its saved settings. Lumi origin is retained and the Product
    carries User into this practice.
  kind: product
  entities:
  - entity: meditation-practice
    effect: creates
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
    to: Running
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Carry User into the newly started process
  kind: product
  actor: user
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
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
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Start practice — lumi meditation

## Trigger

Start practice — lumi meditation.

## Outcome

A new originating Meditation process starts from its saved settings. Lumi origin is retained and the Product carries User into this practice.
