---
appliesTo:
- type: entity
  id: sync-node
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

# Sync nodes use normalized bounded address lists

Normalize supported URLs, resolve duplicate addresses to the existing entry and cap at eight. Refuse last-node removal and guarded busy changes. Preferred activation retains separate node cursor/clock/hash state.
