---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Format custom appearance for the selected source or preference
  kind: actor
  entities:
  - entity: custom-appearance
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: The current draft parses as valid source before formatting; formatting changes editor text and history without
    independently saving it.
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
- text: Valid draft source is formatted and editor history retained without an independent save.
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

# Format custom appearance — formatted

## Trigger

Format custom appearance for the selected source or preference.

## Outcome

Valid draft source is formatted and editor history retained without an independent save.
