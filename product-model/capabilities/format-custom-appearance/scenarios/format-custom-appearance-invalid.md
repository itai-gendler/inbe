---
kind: validation
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
- text: The selected draft fails source parsing or validation; the previous valid applied preview and known saved
    source remain the recovery reference.
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
- text: Invalid source reports diagnostics and retains the previous valid applied preview; it is not committed as
    valid source.
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

# Format custom appearance — invalid

## Trigger

Format custom appearance for the selected source or preference.

## Outcome

Invalid source reports diagnostics and retains the previous valid applied preview; it is not committed as valid source.
