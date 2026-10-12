---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: The originating live timer reaches the next breath, phase, movement or duration boundary
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
  unattended: true
- text: Remaining duration counts down at the origin; expiration follows the configured completion path.
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Remaining time
    - Elapsed progress
    - Extension state
    - Waiting state
    - Pause
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
---

# Advance practice — timer meditation

## Trigger

Advance practice — timer meditation.

## Outcome

Remaining duration counts down at the origin; expiration follows the configured completion path.
