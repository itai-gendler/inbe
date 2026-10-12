---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Rewind practice — wim hof first reset
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: The supported current Wim Hof round or Sun Salutation movement position determines the previous position;
    Wim Hof first-round rewind resets that round.
  kind: condition
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Phase
    - Round
    - Breath
    - Retention progress
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
  - entity: wim-hof-settings
    effect: reads
    facts:
    - Rounds
    - Breaths
    - Speed
    - Progression
    - Start preference
    - Between-round pause
    - Animation
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: At the first round, rewind resets that round rather than inventing a negative round.
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: changes
    facts:
    - Phase
    - Round
    - Breath
    - Retention progress
  contexts:
    desktop:
      place: desktop-app::wim-hof
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
  target: src/practices/whm/whm_session.zi
---

# Rewind practice — wim hof first reset

## Trigger

Rewind practice — wim hof first reset.

## Outcome

At the first round, rewind resets that round rather than inventing a negative round.
