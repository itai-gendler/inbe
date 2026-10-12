---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Show progress chart for the current conversation
  kind: actor
  entities:
  - entity: progress-chart
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: The requested metric is unsupported or the day count lies outside one through thirty-one.
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
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: An unsupported metric or out-of-range day count prevents chart creation.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
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

# Show progress chart — metric or range

## Trigger

Show progress chart for the current conversation.

## Outcome

An unsupported metric or out-of-range day count prevents chart creation.
