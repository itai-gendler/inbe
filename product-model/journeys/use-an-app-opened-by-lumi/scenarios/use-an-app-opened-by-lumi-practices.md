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
      place: desktop-app::practices
- text: Read the shipped practice choices
  kind: actor
  actor: user
  capability: browse-practices
  entities: []
  contexts:
    desktop:
      place: desktop-app::practices
- text: Present the four shipped practice choices and access to their guide and configuration
  kind: product
  actor: user
  capability: browse-practices
  entities: []
  contexts:
    desktop:
      place: desktop-app::practices
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
  target: src/practices/practice_registry.zi
---

# Use an app opened by Lumi — practices

## Trigger

User opens an enabled installed destination from lumi.

## Outcome

User reaches practices and completes the browse practices operation.
