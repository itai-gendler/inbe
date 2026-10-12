---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Finish practice — normal meditation explicit
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: The originating process has qualifying recorded progress and reaches ordinary completion or explicit Finish
    from awaiting finish.
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
- text: The qualifying completed duration is saved. Matching session-linked progress is refreshed; a finish helper
    can write one into an incomplete stored day. The ordinary result stays in the practice process for optional
    mood, discard or dismissal.
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    - Waiting state
    - Duration
    - Remaining time
    from: Awaiting finish
    to: Completed
  - entity: meditation-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Duration
    - Mood
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

# Finish practice — normal meditation explicit

## Trigger

Finish practice — normal meditation explicit.

## Outcome

The qualifying completed duration is saved. Matching session-linked progress is refreshed; a finish helper can write one into an incomplete stored day. The ordinary result stays in the practice process for optional mood, discard or dismissal.
