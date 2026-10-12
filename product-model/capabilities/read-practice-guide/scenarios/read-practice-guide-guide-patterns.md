---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read practice guide — guide patterns
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::patterns
  actor: user
- text: The selected shipped family identifies the guide presented in the same process as its configuration.
  kind: condition
  entities:
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
- text: The Breathing Patterns guide is presented in the same practice process as its configuration.
  kind: product
  entities: []
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

# Read practice guide — guide patterns

## Trigger

Read practice guide — guide patterns.

## Outcome

The Breathing Patterns guide is presented in the same practice process as its configuration.
