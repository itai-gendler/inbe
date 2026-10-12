---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to select a recognized theme or appearance mode
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested shipped theme or light/dark/system mode is resolved before changing the saved preference.
  kind: condition
  entities:
  - entity: appearance-settings
    effect: reads
    facts:
    - Theme
    - Mode
    - Source selection
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Save the recognized theme or appearance mode and apply it in the current interface.
  kind: product
  entities:
  - entity: appearance-settings
    effect: changes
    facts:
    - Theme
    - Mode
    - Source selection
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
- kind: code
  role: implementation
  target: src/app/appearance_actions.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/app/settings_actions.zi
---

# Change appearance settings — lumi

## Trigger

Change appearance settings for the selected source or preference.

## Outcome

The recognized theme or appearance mode is saved and applied. Scale and custom-source editing remain settings-page actions.
