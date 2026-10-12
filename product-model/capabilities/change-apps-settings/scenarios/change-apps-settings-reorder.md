---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Choose the pinned app order
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
  actor: user
- text: Current enabled and installed choices and pinned order determine which selection or ordering preference
    is being changed; disabling retains app data.
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
- text: Pinned order is saved.
  kind: product
  entities:
  - entity: apps-settings
    effect: changes
    facts:
    - Pinned order
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

# Change apps settings — reorder

## Trigger

Choose the pinned app order.

## Outcome

Pinned order is saved.
