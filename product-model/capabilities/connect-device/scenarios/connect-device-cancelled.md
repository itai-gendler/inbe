---
kind: edge
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
- text: Cancel resets the local transfer process without claiming account installation.
  kind: product
  entities:
  - entity: device-connection
    effect: removes
    from: Showing
  - entity: account
    effect: reads
    facts: []
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

# Connect device — cancelled

## Trigger

Use the desktop transfer code and compare displayed digits.

## Outcome

Cancel resets the local transfer process without claiming account installation.

## Edge cases

- Cancellation/reset also clears a local confirmation or working transfer stage; it does not certify account installation.
