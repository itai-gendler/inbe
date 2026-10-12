---
domain: account
references:
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
- kind: code
  role: implementation
  target: src/app/app_sync.zi
---

# Sync settings

Optional synchronization preference and observable exchange status.

## Information kept

- **Enabled** — Saved preference enabling optional account synchronization.
- **Exchange status** — Observable current exchange progress, success or actionable failure.
- **Retry status** — Current retry delay or stopped retry outcome.
- **Pending review** — Whether incoming data is retained for a local keep, merge or replace decision.
