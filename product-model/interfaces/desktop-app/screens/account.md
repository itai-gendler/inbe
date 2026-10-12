---
entities:
- entity: account
  shows:
  - Identity
  - Alias
  - Proposed identity
  - Installed identity
  collects:
  - Alias
  - Proposed identity
- entity: sync-settings
  shows:
  - Enabled
  - Exchange status
  - Retry status
  - Pending review
  collects:
  - Enabled
- entity: sync-node
  shows:
  - Address
  - Order
  - Preferred
  - Active
  collects:
  - Address
- entity: device-connection
  shows:
  - Code
  - Direction
  - Comparison digits
  - Expiry
  - Stage
  collects:
  - Comparison digits
references:
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
- kind: code
  role: implementation
  target: src/app/app_sync.zi
- kind: code
  role: implementation
  target: src/screens/settings/settings_sync_account_impl.zi
---

# Account

Local account identity and alias, key-file backup actions, synchronization status and pending review, configured nodes and the desktop transfer process. The private key is not drawn.
