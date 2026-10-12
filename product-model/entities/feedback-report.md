---
domain: lumi
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
---

# Feedback report

Approved feedback retained for delivery and retry.

## Information kept

- **Report identity** — Stable identity used to queue the approved report and match its delivery receipt.
- **Scope** — Account data context containing the delivery queue.
- **Queued body** — Approved title, message and context retained while delivery is pending.
- **Delivery marker** — Delivered marker replacing the queued body after a matching receipt is accepted.

## States

### Queued

The approved body is retained under its stable report identity for delivery and retry.

### Delivered

A matching receipt replaced the queued body with the delivered marker.
