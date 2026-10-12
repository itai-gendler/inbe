---
kind: edge
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
- text: When queue persistence fails, report the failure without creating queued work; the draft remains proposed.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: When queue persistence succeeds but the later decision-marker write fails, retain the approved report
    as queued while the draft remains proposed.
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
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
---

# Approve feedback — queue or decision write failed

## Trigger

Approve feedback for the current conversation.

## Outcome

Queue failure leaves no claimed queued report. A later draft-marker failure can leave the report queued while the draft still appears undecided; approval is not rolled back as one atomic write.

## Decision points

### Failed persistence stage

Which write failed?

- Queue write → retain the proposed draft without claiming queued work.
- Decision-marker write after queue success → retain the queued report and the still-proposed draft, exposing the failure.
