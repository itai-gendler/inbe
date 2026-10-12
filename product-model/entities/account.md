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

# Account

Locally available account credentials and an optional proposed switch.

## Information kept

- **Identity** — Public account identifier associated with the locally available credentials.
- **Private key** — Local account secret when key mode supplies it.
- **Alias** — Registered account alias shown after successful service registration.
- **Proposed identity** — Different credentials awaiting the local preserve-or-replace decision.
- **Installed identity** — Credentials currently used for account exchange; a proposed identity does not replace them until its switch succeeds.
