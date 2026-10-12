---
kind: primary
result: achieved
routes:
  desktop: Native desktop
steps:
- text: Accept the initial language choice
  kind: actor
  actor: user
  capability: change-device-settings
  entities: []
  contexts:
    desktop:
      place: desktop-app::language
- text: Save language and carry User to Apps selection
  kind: product
  actor: user
  capability: change-device-settings
  entities:
  - entity: device-settings
    effect: changes
    facts:
    - Preferred language
    - System language
  contexts:
    desktop:
      place: desktop-app::apps
- text: Choose initial enabled apps
  kind: actor
  actor: user
  capability: change-apps-settings
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
- text: Save selected apps and setup completion
  kind: product
  actor: user
  capability: change-apps-settings
  entities:
  - entity: apps-settings
    effect: changes
    facts:
    - Enabled apps
    - Setup selection
  - entity: profile
    effect: changes
    facts:
    - Setup progress
  contexts:
    desktop:
      place: desktop-app::apps
references:
- kind: code
  role: implementation
  target: src/screens/language_screen.zi
- kind: code
  role: implementation
  target: src/screens/app_selection_screen.zi
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
---

# Language acceptance to Apps selection

## Trigger

User opens an installation whose initial setup is unfinished.

## Outcome

The language preference and initial enabled selection are saved, and the application is ready for local use.
