---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Choose an optional mood and Done on the ordinary result
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: The ordinary result’s saved identity and selected mood determine whether Done writes a positive mood or
    closes without a record edit
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
- text: Only when this ordinary result is saved and its selected mood is positive, persist that mood before closing;
    otherwise skip the record edit
  kind: product
  entities:
  - entity: patterns-session
    effect: changes
    facts:
    - Mood
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: After successful Done, close the ordinary result and return to start
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

# Rate session — normal result patterns

## Trigger

Rate session — normal result patterns.

## Outcome

Done closes the ordinary result after any required mood write succeeds. No selected positive mood, or an unsaved result, closes without editing a retained session; a failed required write retains the result.

## Decision points

### Mood write

Does Done require a saved-record update?

- Saved result with positive selected mood → save the mood, then close on success.
- No positive mood or unsaved result → close without editing a retained record.
