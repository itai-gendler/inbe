---
appliesTo:
- type: entity
  id: device-connection
- type: entity
  id: account
references:
- kind: code
  role: implementation
  target: src/app/device_link_session.zi
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
---

# Device Connected is a local protocol observation

Native code lifetime is approximately 590 seconds with one-second polling. Sender success follows mailbox acceptance; receiver may call imported while account-switch choice remains pending. Connected certifies neither installed keys nor completed exchange on both devices.
