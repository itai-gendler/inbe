---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Start practice — lumi patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested family, existing local process and fresh remote activity determine new start, same-process
    restoration or refusal; saved configuration supplies the new run.
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
      place: desktop-app::lumi
  actor: user
- text: A new originating Breathing Patterns process starts from its saved settings. Lumi origin is retained and
    the Product carries User into this practice.
  kind: product
  entities:
  - entity: patterns-practice
    effect: creates
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
    to: Running
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Carry User into the newly started process
  kind: product
  actor: user
  entities: []
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
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Start practice — lumi patterns

## Trigger

Start practice — lumi patterns.

## Outcome

A new originating Breathing Patterns process starts from its saved settings. Lumi origin is retained and the Product carries User into this practice.
