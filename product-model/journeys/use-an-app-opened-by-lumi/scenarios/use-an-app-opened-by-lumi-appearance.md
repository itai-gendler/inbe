---
kind: primary
result: achieved
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to open the selected app
  kind: actor
  actor: user
  capability: open-app
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
- text: Activate the selected destination and carry User into its working context
  kind: product
  actor: user
  capability: open-app
  entities: []
  contexts:
    desktop:
      place: desktop-app::appearance
- text: Choose a theme, appearance mode or scale at Appearance
  kind: actor
  actor: user
  capability: change-appearance-settings
  entities: []
  contexts:
    desktop:
      place: desktop-app::appearance
- text: Save the selected appearance preference from the destination settings subject
  kind: product
  actor: user
  capability: change-appearance-settings
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
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/app/app_nav_state.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
---

# Use an app opened by Lumi — appearance

## Trigger

User opens an enabled installed destination from lumi.

## Outcome

User reaches appearance and completes the change appearance settings operation.
