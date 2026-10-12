---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Check installed app releases
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
  actor: user
- text: Installed package version and trial status are compared with releases that pass publisher, signature, sequence,
    host compatibility and payload checks.
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
- text: An unproved or failed cached trial is marked unusable and the known working fallback is retained.
  kind: product
  entities:
  - entity: apps-settings
    effect: changes
    facts:
    - Package versions
    - Package status
    - Installed apps
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

# Check app updates — trial fallback

## Trigger

Check installed app releases.

## Outcome

An unproved or failed cached trial is marked unusable and the known working fallback is retained.
