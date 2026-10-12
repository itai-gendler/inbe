---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Confirm initial app choices
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
- text: Selection is saved and initial setup records completion.
  kind: product
  entities:
  - entity: apps-settings
    effect: changes
    facts:
    - Enabled apps
    - Setup selection
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

# Change apps settings — first selection

## Trigger

Confirm initial app choices.

## Outcome

Selection is saved and initial setup records completion.
