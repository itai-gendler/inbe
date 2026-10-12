---
appliesTo:
- type: entity
  id: sync-settings
references:
- kind: code
  role: implementation
  target: src/app/app_sync.zi
- kind: code
  role: implementation
  target: src/app/sync_retry.zi
- kind: code
  role: implementation
  target: src/storage/sync_review.zi
---

# Incoming application defers around unsafe live edits

Native frame-thread versus worker exchange and safe UI-application deferral follow the practice/editing guards. This establishes no mobile/browser lifecycle parity.
