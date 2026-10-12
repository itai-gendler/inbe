---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Discard practice result — result patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: The ordinary result is active; its saved outcome and recorded identity determine whether discard removes
    a retained result before closing the live result stage.
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
- text: Only when this ordinary result is already saved, remove its retained record and refresh linked progress;
    an unsaved result skips this removal.
  kind: product
  entities:
  - entity: patterns-session
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
      place: desktop-app::patterns
  actor: user
- text: Close the discarded ordinary result process
  kind: product
  actor: user
  entities:
  - entity: patterns-practice
    effect: removes
    from: Completed
  contexts:
    desktop:
      place: desktop-app::patterns
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

# Discard practice result — result patterns

## Trigger

Discard practice result — result patterns.

## Outcome

An already saved result is removed from active history and linked progress is refreshed; the ordinary result process closes. An unsaved result has no saved record to remove.

## Edge cases

- When the result is unsaved, discard closes the live result without removing a nonexistent saved record.

## Decision points

### Saved result

Does the ordinary result have a retained record?

- Saved → remove its retained record and refresh linked progress before closing the result.
- Unsaved → close the result without removing a nonexistent retained record.
