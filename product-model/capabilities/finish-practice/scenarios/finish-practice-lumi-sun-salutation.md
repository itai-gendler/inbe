---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: The originating live run reaches qualifying normal completion; the current launch context selects ordinary
    results or the Lumi summary
  kind: condition
  entities:
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
    - Movement step
    - Repetition progress
    - Pause
    - Result values
    - Save outcome
    - Pending control
    - Control outcome
  - entity: sun-salutation-settings
    effect: reads
    facts:
    - Repetitions
    - Start timing
    - End timing
    - Character
  contexts:
    desktop:
      place: desktop-app::sun-salutation
  unattended: true
- text: Positive completed repetitions are saved. Matching session-linked progress is refreshed; a finish helper
    can write one into an incomplete stored day. A conversation summary replaces the live result process and is
    available to read; this is the normal completion route.
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    from: Running
    to: Completed
  - entity: sun-salutation-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Repetitions
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
      place: desktop-app::sun-salutation
- text: Archive a saved or unsaved result summary and return to Lumi
  kind: product
  entities:
  - entity: lumi-message
    effect: creates
    facts:
    - Archive identity
    - Scope
    - Speaker
    - Text
    - Time
    - Card payload
    - Deletion marker
  - entity: sun-salutation-practice
    effect: removes
    from: Completed
  contexts:
    desktop:
      place: desktop-app::lumi
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
  target: src/practices/sun_salutation/sun_salutation_session.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Finish practice — lumi sun salutation

## Trigger

Finish practice — lumi sun salutation.

## Outcome

Positive completed repetitions are saved. Matching session-linked progress is refreshed; a finish helper can write one into an incomplete stored day. A conversation summary replaces the live result process and is available to read; this is the normal completion route.
