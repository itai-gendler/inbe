---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Show progress chart for the current conversation
  kind: actor
  entities:
  - entity: progress-chart
    effect: reads
    facts: []
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
- text: The requested tool path or target is unavailable; no chart is archived.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/lumi/lumi.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/cells/lumi_online.zi
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi#LumiPerform
---

# Show progress chart — lumi target or tools unavailable

## Trigger

Show progress chart for the current conversation.

## Outcome

The requested tool path or target is unavailable; no chart is archived.
