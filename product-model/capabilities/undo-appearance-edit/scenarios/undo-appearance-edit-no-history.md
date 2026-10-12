---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Undo appearance edit for the selected source or preference
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: No earlier draft is present in editor history.
  kind: condition
  entities:
  - entity: appearance-settings
    effect: reads
    facts:
    - Theme
    - Source selection
    - Mode
    - Scale
  - entity: custom-appearance
    effect: reads
    facts:
    - Scope
    - Draft source
    - Saved source
    - Applied source
    - Diagnostics
    - Undo information
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: Without undo history, the draft remains unchanged.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
- kind: code
  role: implementation
  target: src/app/appearance_actions.zi
---

# Undo appearance edit — no history

## Trigger

Undo appearance edit for the selected source or preference.

## Outcome

Without undo history, the draft remains unchanged.
