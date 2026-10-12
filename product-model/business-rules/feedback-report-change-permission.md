---
appliesTo:
- type: entity
  id: feedback-report
  effect: changes
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
permits:
- unattended: true
---

# Product delivery records Feedback report change

Unattended delivery records only a matching report-ID receipt as delivered. Failures and mismatched receipts retain the queued body for the demonstrated retry rather than fabricating success.
