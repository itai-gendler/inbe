---
kind: primary
result: achieved
routes:
  desktop: Native desktop
steps:
- text: Choose the app catalogue entry to open
  kind: actor
  actor: user
  capability: open-app
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
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
  target: src/app/app_launcher.zi
- kind: code
  role: implementation
  target: src/practices/practice_registry.zi
---

# Use an app from Apps — practices

## Trigger

User opens an enabled installed destination from apps.

## Outcome

User reaches practices and completes the browse practices operation.
