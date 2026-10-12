---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Use the desktop transfer code and compare displayed digits
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Available local credentials select sending or receiving; the code, comparison digits, expiry and local transfer
    stage determine the next protocol action.
  kind: condition
  entities:
  - entity: device-connection
    effect: reads
    facts:
    - Code
    - Direction
    - Comparison digits
    - Expiry
    - Stage
  - entity: account
    effect: reads
    facts:
    - Identity
    - Alias
    - Proposed identity
    - Installed identity
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: The sender reports Connected after its success receipt; this does not certify receiver installation or completed
    data synchronization.
  kind: product
  entities:
  - entity: device-connection
    effect: creates
    facts:
    - Code
    - Direction
    - Comparison digits
    - Expiry
    - Stage
    to: Showing
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Compare the answered code digits
  kind: product
  entities:
  - entity: device-connection
    effect: changes
    facts:
    - Comparison digits
    - Stage
    from: Showing
    to: Confirm
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Confirm sending the sealed account
  kind: product
  entities:
  - entity: device-connection
    effect: changes
    facts:
    - Stage
    from: Confirm
    to: Working
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Accept the mailbox success receipt
  kind: product
  entities:
  - entity: device-connection
    effect: changes
    facts:
    - Stage
    from: Working
    to: Connected
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
references:
- kind: code
  role: implementation
  target: src/app/device_link_session.zi
- kind: code
  role: implementation
  target: src/screens/settings/settings_sync_account_impl.zi
---

# Connect device — desktop sender

## Trigger

Use the desktop transfer code and compare displayed digits.

## Outcome

The sender reports Connected after its success receipt; this does not certify receiver installation or completed data synchronization.
