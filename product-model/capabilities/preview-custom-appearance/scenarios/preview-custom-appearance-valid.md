---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Preview custom appearance for the selected source or preference
  kind: actor
  entities:
  - entity: custom-appearance
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: The selected draft is parsed before applying a preview; invalid input retains the previous valid applied
    source.
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
- text: Valid draft source is applied as a preview without independently replacing saved source.
  kind: product
  entities:
  - entity: custom-appearance
    effect: changes
    facts:
    - Draft source
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

# Preview custom appearance — valid

## Trigger

Preview custom appearance for the selected source or preference.

## Outcome

Valid draft source is applied as a preview without independently replacing saved source.
