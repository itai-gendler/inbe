---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read or filter the app catalogue
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
  actor: user
- text: Enabled and installed app choices, pinned order and current package status determine the catalogue availability
    shown.
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
- text: Shipped choices reflect current enabled and installed masks and package status.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
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

# Browse apps — catalogue

## Trigger

Read or filter the app catalogue.

## Outcome

Shipped choices reflect current enabled and installed masks and package status.
