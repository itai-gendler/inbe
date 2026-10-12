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
      place: desktop-app::diary
- text: Choose a local calendar date
  kind: actor
  actor: user
  capability: browse-diary
  entities: []
  contexts:
    desktop:
      place: desktop-app::diary
- text: Load the complete supported dated document and its retained image references
  kind: product
  actor: user
  capability: browse-diary
  entities:
  - entity: diary-entry
    effect: reads
    facts:
    - Date
    - Text
    - Document
    - Photo references
    - Document validity
  contexts:
    desktop:
      place: desktop-app::diary
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
  target: src/screens/diary_screen.zi
---

# Use an app from Apps — diary

## Trigger

User opens an enabled installed destination from apps.

## Outcome

User reaches diary and completes the browse diary operation.
