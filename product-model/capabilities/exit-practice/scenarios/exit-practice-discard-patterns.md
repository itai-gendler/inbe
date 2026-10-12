---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Exit practice — discard patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: The unfinished originating process and its pause and elapsed/completed progress determine whether discard,
    qualifying partial save or cancellation is offered.
  kind: condition
  entities:
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Ratio
    - Phase
    - Cycle
    - Duration
    - Elapsed progress
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
  - entity: patterns-settings
    effect: reads
    facts:
    - Preset
    - Phase durations
    - Session duration
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit;
    no normal completion summary is produced.
  kind: product
  entities:
  - entity: patterns-practice
    effect: removes
    from: Running
  contexts:
    desktop:
      place: desktop-app::patterns
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
  target: src/practices/patterns/patterns_practice.zi
---

# Exit practice — discard patterns

## Trigger

Exit practice — discard patterns.

## Outcome

Discard ends unfinished progress and returns to start. Sun Salutation offers no matching partial-save exit; no normal completion summary is produced.
