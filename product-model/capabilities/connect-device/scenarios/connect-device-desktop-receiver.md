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
- text: The receiver can advance to Connected while account-switch confirmation remains pending. Native desktop
    shows a code; scanner acceptance is outside this contract.
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
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Poll for the sealed account
  kind: product
  entities:
  - entity: device-connection
    effect: changes
    facts:
    - Stage
    from: Showing
    to: Working
  - entity: account
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Receive and prepare the proposed identity
  kind: product
  entities:
  - entity: device-connection
    effect: changes
    facts:
    - Stage
    from: Working
    to: Received
  - entity: account
    effect: changes
    facts:
    - Proposed identity
  contexts:
    desktop:
      place: desktop-app::account
  actor: user
- text: Record local transfer completion
  kind: product
  entities:
  - entity: device-connection
    effect: changes
    facts:
    - Stage
    from: Received
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

# Connect device — desktop receiver

## Trigger

Use the desktop transfer code and compare displayed digits.

## Outcome

The receiver can advance to Connected while account-switch confirmation remains pending. Native desktop shows a code; scanner acceptance is outside this contract.
