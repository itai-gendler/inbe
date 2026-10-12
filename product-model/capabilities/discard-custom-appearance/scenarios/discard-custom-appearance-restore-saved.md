---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Discard custom appearance for the selected source or preference
  kind: actor
  entities:
  - entity: custom-appearance
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: The selected source slot has a saved source distinct from any unsaved draft or applied preview.
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
- text: The editor and preview restore the saved source.
  kind: product
  entities:
  - entity: custom-appearance
    effect: changes
    facts:
    - Draft source
    - Applied source
    - Diagnostics
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

# Discard custom appearance — restore saved

## Trigger

Discard custom appearance for the selected source or preference.

## Outcome

The editor and preview restore the saved source.
