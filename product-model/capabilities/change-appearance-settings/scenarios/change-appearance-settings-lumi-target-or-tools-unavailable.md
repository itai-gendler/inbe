---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to select a recognized theme or appearance mode
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: If current mode, installed Lumi or the required target app makes this tool unavailable, refuse before
    reading protected target data. An unresolved request with available tools follows only its permitted lookup
    branch and still performs no mutation.
  kind: condition
  entities:
  - entity: profile
    effect: reads
    facts:
    - Account access mode
  - entity: apps-settings
    effect: reads
    facts:
    - Lumi installed
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The mapped Lumi preference path is unavailable; no appearance preference is changed.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
- kind: code
  role: implementation
  target: src/app/appearance_actions.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi#LumiPerform
---

# Change appearance settings — lumi target or tools unavailable

## Trigger

Change appearance settings for the selected source or preference.

## Outcome

The mapped Lumi preference path is unavailable; no appearance preference is changed.
