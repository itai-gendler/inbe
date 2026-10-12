---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Dismiss feedback for the current conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The selected draft is still Proposed with a valid decision identity; dismissal writes its marker without
    queueing a report.
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
- text: The draft decision is persisted as dismissed and no report is queued.
  kind: product
  entities:
  - entity: feedback-proposal
    effect: changes
    facts:
    - Decision
    from: Proposed
    to: Dismissed
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

# Dismiss feedback — decision

## Trigger

Dismiss feedback for the current conversation.

## Outcome

The draft decision is persisted as dismissed and no report is queued.
