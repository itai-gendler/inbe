---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Approve feedback for the current conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The selected draft still has its proposed title, message and context; acceptance first queues its stable
    report identity and then writes the decision marker.
  kind: condition
  entities:
  - entity: feedback-proposal
    effect: reads
    facts:
    - Identity
    - Scope
    - Title
    - Message
    - Context
    - Decision
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Human approval queues a stable report ID, then records the draft decision. The queued report need not wait
    for marker persistence.
  kind: product
  entities:
  - entity: feedback-report
    effect: creates
    facts:
    - Report identity
    - Scope
    - Queued body
    - Delivery marker
    to: Queued
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Record acceptance of the selected draft
  kind: product
  entities:
  - entity: feedback-proposal
    effect: changes
    facts:
    - Decision
    from: Proposed
    to: Accepted
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
---

# Approve feedback — queue

## Trigger

Approve feedback for the current conversation.

## Outcome

Human approval queues a stable report ID, then records the draft decision. The queued report need not wait for marker persistence.
