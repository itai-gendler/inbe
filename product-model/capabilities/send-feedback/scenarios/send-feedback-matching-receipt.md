---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Queued approved feedback receives a response carrying its matching report identity
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
- text: A matching report-ID receipt records delivery and can replace the retained body with its delivered marker;
    it does not imply a separate success message was archived.
  kind: product
  entities:
  - entity: feedback-report
    effect: changes
    facts:
    - Queued body
    - Delivery marker
    from: Queued
    to: Delivered
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

# Send feedback — matching receipt

## Trigger

Send feedback for the current conversation.

## Outcome

A matching report-ID receipt records delivery and can replace the retained body with its delivered marker; it does not imply a separate success message was archived.
