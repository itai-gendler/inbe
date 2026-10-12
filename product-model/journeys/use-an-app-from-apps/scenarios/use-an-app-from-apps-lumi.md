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
      place: desktop-app::lumi
- text: Read current conversation history
  kind: actor
  actor: user
  capability: browse-conversation
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
- text: Present valid current-scope chronological archive text and supported interactive payloads
  kind: product
  actor: user
  capability: browse-conversation
  entities:
  - entity: lumi-message
    effect: reads
    facts:
    - Speaker
    - Text
    - Time
    - Card payload
  contexts:
    desktop:
      place: desktop-app::lumi
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
  target: src/screens/lumi_screen.zi
---

# Use an app from Apps — lumi

## Trigger

User opens an enabled installed destination from apps.

## Outcome

User reaches lumi and completes the browse conversation operation.
