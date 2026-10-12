---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: Queued approved feedback receives a response carrying a different report identity
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
- text: A mismatched receipt does not mark the queued report delivered.
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

# Send feedback — receipt mismatch

## Trigger

Send feedback for the current conversation.

## Outcome

A mismatched receipt does not mark the queued report delivered.
