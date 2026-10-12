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
- text: Transport, seal/open or node-selection failure reports the local failed stage without certifying installation.
  kind: product
  entities:
  - entity: device-connection
    effect: changes
    facts:
    - Stage
    from: Working
    to: Failed
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

# Connect device — failed

## Trigger

Use the desktop transfer code and compare displayed digits.

## Outcome

Transport, seal/open or node-selection failure reports the local failed stage without certifying installation.
