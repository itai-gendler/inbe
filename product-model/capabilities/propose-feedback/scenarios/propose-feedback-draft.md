---
kind: primary
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
- text: Entered feedback has a nonempty title and message within 160 and 4096 bytes and context within 2048 bytes
    before a draft is retained.
  kind: condition
  entities:
  - entity: lumi-message
    effect: reads
    facts:
    - Archive identity
    - Scope
    - Speaker
    - Text
    - Time
    - Card payload
    - Deletion marker
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: A draft with title, message, context and decision identity is retained without sending a report.
  kind: product
  entities:
  - entity: feedback-proposal
    effect: creates
    facts:
    - Identity
    - Scope
    - Title
    - Message
    - Context
    - Decision
    to: Proposed
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

# Propose feedback — draft

## Trigger

Propose feedback for the current conversation.

## Outcome

A draft with title, message, context and decision identity is retained without sending a report.
