---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Queued approved feedback reaches a failed delivery attempt before a matching receipt
  kind: condition
  entities:
  - entity: feedback-report
    effect: reads
    facts:
    - Report identity
    - Scope
    - Queued body
    - Delivery marker
  contexts:
    desktop:
      place: desktop-app::lumi
  unattended: true
- text: Failed delivery retains queued work for a sixty-second retry and an idempotent failure notice.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Send feedback — delivery failed

## Trigger

Send feedback for the current conversation.

## Outcome

Failed delivery retains queued work for a sixty-second retry and an idempotent failure notice.
