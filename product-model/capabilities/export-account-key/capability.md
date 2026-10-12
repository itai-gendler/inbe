---
availability:
- place: desktop-app
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_sync_account_impl.zi
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
domain: account
---

# Export account key

Write the local account-key backup file in the plaintext format exposed by the native UI.
