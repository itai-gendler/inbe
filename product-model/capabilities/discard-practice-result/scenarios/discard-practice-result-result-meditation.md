---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Discard practice result — result meditation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: The ordinary result is active; its saved outcome and recorded identity determine whether discard removes
    a retained result before closing the live result stage.
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
- text: Only when this ordinary result is already saved, remove its retained record and refresh linked progress;
    an unsaved result skips this removal.
  kind: product
  entities:
  - entity: meditation-session
    effect: removes
  - entity: habit-day
    effect: changes
    facts:
    - Materialized baseline
    - Visible linked count
    - Effective count
    - Completed
  contexts:
    desktop:
      place: desktop-app::meditation
  actor: user
- text: Close the discarded ordinary result process
  kind: product
  actor: user
  entities:
  - entity: meditation-practice
    effect: removes
    from: Completed
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

# Discard practice result — result meditation

## Trigger

Discard practice result — result meditation.

## Outcome

An already saved result is removed from active history and linked progress is refreshed; the ordinary result process closes. An unsaved result has no saved record to remove.

## Edge cases

- When the result is unsaved, discard closes the live result without removing a nonexistent saved record.

## Decision points

### Saved result

Does the ordinary result have a retained record?

- Saved → remove its retained record and refresh linked progress before closing the result.
- Unsaved → close the result without removing a nonexistent retained record.
