---
kind: primary
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
- text: The selected draft has an earlier editor-history entry to restore; absence of history leaves it unchanged.
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
- text: The prior draft is restored from available history without silently committing it.
  kind: product
  entities:
  - entity: custom-appearance
    effect: changes
    facts:
    - Draft source
    - Undo information
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

# Undo appearance edit — prior draft

## Trigger

Undo appearance edit for the selected source or preference.

## Outcome

The prior draft is restored from available history without silently committing it.
