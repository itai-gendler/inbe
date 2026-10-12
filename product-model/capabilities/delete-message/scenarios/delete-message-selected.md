---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Delete message for the current conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The selected retained row has an archive identity; the synthetic greeting has none, and the selected ordinary
    or chart kind determines the removal effect.
  kind: condition
  entities:
  - entity: lumi-message
    effect: reads
    facts:
    - Archive identity
    - Scope
    - Speaker
    - Text
    - Time
    - Card payload
    - Deletion marker
  - entity: progress-chart
    effect: reads
    facts:
    - Archive identity
    - Scope
    - Message header
    - Metric
    - Date range
    - Dates
    - Snapshot values
    - Deletion marker
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: For a selected ordinary archived row, mark that addressed row deleted
  kind: product
  entities:
  - entity: lumi-message
    effect: removes
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: For a selected chart row instead, mark its addressed snapshot deleted
  kind: product
  actor: user
  entities:
  - entity: progress-chart
    effect: removes
  contexts:
    desktop:
      place: desktop-app::lumi
references:
- kind: code
  role: implementation
  target: apps/lumi/lumi.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/cells/lumi_online.zi
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
---

# Delete message — selected

## Trigger

Delete message for the current conversation.

## Outcome

The addressed archived row, whether ordinary or a chart, is marked deleted and omitted from active history; the branch removes only the selected kind.

## Decision points

### Selected archive kind

Which retained row was selected?

- Ordinary row → delete its addressed archive entry and omit it from active history.
- Chart row → delete its addressed snapshot and omit it from active history.
