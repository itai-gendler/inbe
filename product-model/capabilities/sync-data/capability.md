---
availability:
- place: desktop-app
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
- kind: code
  role: implementation
  target: src/storage/storage_core.zi
domain: account
---

# Sync data

Exchange queued local changes using optional account synchronization, preserving review and retry outcomes.
