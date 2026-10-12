---
appliesTo:
- type: entity
  id: sync-settings
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

# Sync retry uses classified delays and node-specific state

Retryable results use 5/15/30/60-second delays and renewed challenges when needed. Unknown/actionable results stop. Failover classification is narrower than retry classification; node cursors are separate and queued local data remains.
