---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Choose the app catalogue entry to open
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
  actor: user
- text: The requested destination is resolved against current app choices and installed packages; setup and the
    selected settings section determine the actual destination.
  kind: condition
  entities:
  - entity: apps-settings
    effect: reads
    facts:
    - Enabled apps
    - Installed apps
    - Pinned apps
    - Pinned order
    - Setup selection
    - Package versions
    - Package status
    - Online Lumi
    - Lumi installed
    - Habits available
    - Lists available
    - Diary available
    - Practices available
  contexts:
    desktop:
      place: desktop-app::apps
  actor: user
- text: The selected destination is active. Settings uses the selected section or its Device default; opening does
    not reset every settings section.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lists
  actor: user
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/app/launcher_policy.zi
- kind: code
  role: implementation
  target: src/cells/package_manager.zi
---

# Open app — apps lists

## Trigger

Open lists.

## Outcome

The selected destination is active. Settings uses the selected section or its Device default; opening does not reset every settings section.
