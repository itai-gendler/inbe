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
      place: desktop-app::leaderboard
- text: Read the available personal and relationship practice comparisons
  kind: actor
  actor: user
  capability: browse-leaderboard
  entities: []
  contexts:
    desktop:
      place: desktop-app::leaderboard
- text: Present rankings derived from available practice statistics, using the no-data outcome when none are usable
  kind: product
  actor: user
  capability: browse-leaderboard
  entities:
  - entity: profile
    effect: reads
    facts:
    - Local counts
  - entity: friend
    effect: reads
    facts:
    - Display identity
    - Practice statistics
  contexts:
    desktop:
      place: desktop-app::leaderboard
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
  target: src/screens/leaderboard_screen.zi
---

# Use an app from Apps — leaderboard

## Trigger

User opens an enabled installed destination from apps.

## Outcome

User reaches leaderboard and completes the browse leaderboard operation.
