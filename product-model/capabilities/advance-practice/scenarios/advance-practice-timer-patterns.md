---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: The originating live timer reaches the next breath, phase, movement or duration boundary
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
- text: The four-phase ratio and elapsed cycle progress advance.
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Ratio
    - Phase
    - Cycle
    - Duration
    - Elapsed progress
    - Pause
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

# Advance practice — timer patterns

## Trigger

Advance practice — timer patterns.

## Outcome

The four-phase ratio and elapsed cycle progress advance.
