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
      place: desktop-app::profile
- text: Enter a display name or intention and commit the edit
  kind: actor
  actor: user
  capability: edit-profile
  entities: []
  contexts:
    desktop:
      place: desktop-app::profile
- text: Save the entered local display name and intention within their byte and codepoint bounds
  kind: product
  actor: user
  capability: edit-profile
  entities:
  - entity: profile
    effect: changes
    facts:
    - Display name
    - Intention
  contexts:
    desktop:
      place: desktop-app::profile
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
  target: src/screens/profile_screen.zi
---

# Use an app from Apps — profile

## Trigger

User opens an enabled installed destination from apps.

## Outcome

User reaches profile and completes the edit profile operation.
