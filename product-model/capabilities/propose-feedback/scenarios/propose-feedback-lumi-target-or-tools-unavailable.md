---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Propose feedback for the current conversation
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
- text: The mapped proposal tool path is unavailable; no draft is retained.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi#LumiPerform
---

# Propose feedback — lumi target or tools unavailable

## Trigger

Propose feedback for the current conversation.

## Outcome

The mapped proposal tool path is unavailable; no draft is retained.
