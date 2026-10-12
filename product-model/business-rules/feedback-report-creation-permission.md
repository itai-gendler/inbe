---
appliesTo:
- type: entity
  id: feedback-report
  effect: creates
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
permits:
- actors:
  - user
---

# User performs Feedback report creation

User approval queues a stable report identity with the approved title, message and context. Queueing succeeds independently of the later proposal-marker write; drafting alone does not create queued work.
