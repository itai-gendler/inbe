---
availability:
- place: desktop-app
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
domain: lumi
---

# Send feedback

Deliver queued feedback and accept only the matching report receipt; failures retain retryable work.
