---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Save custom appearance for the selected source or preference
  kind: actor
  entities:
  - entity: custom-appearance
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: The selected draft must parse successfully before persistence; successful readback is needed to reconcile
    its known saved source.
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
- text: Valid source is saved and successful readback reconciles the editor saved source.
  kind: product
  entities:
  - entity: custom-appearance
    effect: changes
    facts:
    - Draft source
    - Saved source
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

# Save custom appearance — saved

## Trigger

Save custom appearance for the selected source or preference.

## Outcome

Valid source is saved and successful readback reconciles the editor saved source.
