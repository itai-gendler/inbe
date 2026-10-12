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
      place: desktop-app::lists
- text: Select a parent and completion filter
  kind: actor
  actor: user
  capability: browse-lists
  entities: []
  contexts:
    desktop:
      place: desktop-app::lists
- text: Present current-scope parent titles and their filtered items with saved completion
  kind: product
  actor: user
  capability: browse-lists
  entities:
  - entity: list
    effect: reads
    facts:
    - Title
    - Order
  - entity: todo
    effect: reads
    facts:
    - Parent List
    - Title
    - Comment
    - Order
    - Completion
  contexts:
    desktop:
      place: desktop-app::lists
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
  target: src/screens/elist_screen.zi
---

# Use an app from Apps — lists

## Trigger

User opens an enabled installed destination from apps.

## Outcome

User reaches lists and completes the browse lists operation.
