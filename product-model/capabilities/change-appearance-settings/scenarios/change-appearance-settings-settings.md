---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Change appearance settings for the selected source or preference
  kind: actor
  entities:
  - entity: appearance-settings
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::appearance
  actor: user
- text: The selected theme, source, light/dark/system mode or scale is resolved before saving the requested preference.
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
- text: The selected theme/source, mode and scale preferences persist; Lumi recognition uses the same preference
    outcome.
  kind: product
  entities:
  - entity: appearance-settings
    effect: changes
    facts:
    - Theme
    - Source selection
    - Mode
    - Scale
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

# Change appearance settings — settings

## Trigger

Change appearance settings for the selected source or preference.

## Outcome

The selected theme/source, mode and scale preferences persist; Lumi recognition uses the same preference outcome.
