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
      place: desktop-app::wim-hof
  actor: user
- text: The ordinary result’s saved identity and selected mood determine whether Done writes a positive mood or
    closes without a record edit
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
- text: Only when this ordinary result is saved and its selected mood is positive, persist that mood before closing;
    otherwise skip the record edit
  kind: product
  entities:
  - entity: wim-hof-session
    effect: changes
    facts:
    - Mood
  contexts:
    desktop:
      place: desktop-app::wim-hof
  actor: user
- text: After successful Done, close the ordinary result and return to start
  kind: product
  actor: user
  entities:
  - entity: wim-hof-practice
    effect: removes
    from: Completed
  contexts:
    desktop:
      place: desktop-app::wim-hof
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

# Rate session — normal result wim hof

## Trigger

Rate session — normal result wim hof.

## Outcome

Done closes the ordinary result after any required mood write succeeds. No selected positive mood, or an unsaved result, closes without editing a retained session; a failed required write retains the result.

## Decision points

### Mood write

Does Done require a saved-record update?

- Saved result with positive selected mood → save the mood, then close on success.
- No positive mood or unsaved result → close without editing a retained record.
