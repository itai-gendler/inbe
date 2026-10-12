---
kind: edge
routes:
  desktop: Native desktop
steps:
- text: The active local transfer reaches its approximately 590-second deadline without completed protocol handling
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
    - Private key
    - Alias
    - Proposed identity
    - Installed identity
  contexts:
    desktop:
      place: desktop-app
  unattended: true
- text: The approximately 590-second local transfer lifetime expires and reports failure.
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
references:
- kind: code
  role: implementation
  target: src/app/device_link_session.zi
- kind: code
  role: implementation
  target: src/screens/settings/settings_sync_account_impl.zi
---

# Connect device — expired

## Trigger

Use the desktop transfer code and compare displayed digits.

## Outcome

The approximately 590-second local transfer lifetime expires and reports failure.
