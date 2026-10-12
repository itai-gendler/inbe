---
appliesTo:
- type: entity
  id: feedback-proposal
- type: entity
  id: feedback-report
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
---

# Feedback delivery follows human approval and matching report receipts

Approve queues a stable report ID before marking the draft. Bounds are ID32, title160, message4096 and context2048; queued report identity is stable. Queue success can survive marker-write failure. Only a matching report-ID receipt marks delivery; failure keeps work for sixty-second retry.
