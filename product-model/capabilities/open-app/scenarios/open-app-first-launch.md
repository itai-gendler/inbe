---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Open the application for the first time
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
  actor: user
- text: Initial setup is unfinished, so language acceptance precedes app selection.
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
- text: An unfinished first setup presents language acceptance before app selection.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::language
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

# Open app — first launch

## Trigger

Open the application for the first time.

## Outcome

An unfinished first setup presents language acceptance before app selection.
