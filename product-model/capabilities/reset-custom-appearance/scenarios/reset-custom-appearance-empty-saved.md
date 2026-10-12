---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Reset custom appearance for the selected source or preference
  kind: actor
  entities:
  - entity: custom-appearance
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: The selected source slot is reset by saving and applying empty source rather than removing the customization
    context.
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
- text: Empty custom source is saved, applied and reflected in the editor without removing the customization context.
  kind: product
  entities:
  - entity: custom-appearance
    effect: changes
    facts:
    - Draft source
    - Saved source
    - Applied source
    - Diagnostics
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

# Reset custom appearance — empty saved

## Trigger

Reset custom appearance for the selected source or preference.

## Outcome

Empty custom source is saved, applied and reflected in the editor without removing the customization context.
