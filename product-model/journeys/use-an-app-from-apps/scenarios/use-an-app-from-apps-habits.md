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
      place: desktop-app::habits
- text: Read selected dates and their progress
  kind: actor
  actor: user
  capability: browse-habits
  entities: []
  contexts:
    desktop:
      place: desktop-app::habits
- text: Present scheduled status, target and stored-linked effective completion for the selected dates
  kind: product
  actor: user
  capability: browse-habits
  entities:
  - entity: habit
    effect: reads
    facts:
    - Name
    - Color
    - Order
    - Target
    - Schedule
  - entity: habit-day
    effect: reads
    facts:
    - Date
    - Stored count
    - Visible linked count
    - Effective count
    - Scheduled
    - Completed
  contexts:
    desktop:
      place: desktop-app::habits
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
  target: src/screens/habits_screen.zi
---

# Use an app from Apps — habits

## Trigger

User opens an enabled installed destination from apps.

## Outcome

User reaches habits and completes the browse habits operation.
