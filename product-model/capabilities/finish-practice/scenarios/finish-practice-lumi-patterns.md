---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: The originating live run reaches qualifying normal completion; the current launch context selects ordinary
    results or the Lumi summary
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
  unattended: true
- text: The qualifying recorded elapsed duration is saved. Matching session-linked progress is refreshed; a finish
    helper can write one into an incomplete stored day. A conversation summary replaces the live result process
    and is available to read; this is the normal completion route.
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Result values
    - Save outcome
    from: Running
    to: Completed
  - entity: patterns-session
    effect: creates
    facts:
    - Identity
    - Local date
    - Local time
    - Source
    - Recorded duration values
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
      place: desktop-app::patterns
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
  - entity: patterns-practice
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
  target: src/practices/patterns/patterns_practice.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Finish practice — lumi patterns

## Trigger

Finish practice — lumi patterns.

## Outcome

The qualifying recorded elapsed duration is saved. Matching session-linked progress is refreshed; a finish helper can write one into an incomplete stored day. A conversation summary replaces the live result process and is available to read; this is the normal completion route.
