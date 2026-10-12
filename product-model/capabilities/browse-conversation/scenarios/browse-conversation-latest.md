---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Browse conversation for the current conversation
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Current archive scope and row validity determine which chronological text and interactive payloads are loaded.
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
- text: Current-context archived rows are loaded. Delegated rendering preserves ordinary text and strips interactive
    tool payloads.
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

# Browse conversation — latest

## Trigger

Browse conversation for the current conversation.

## Outcome

Current-context archived rows are loaded. Delegated rendering preserves ordinary text and strips interactive tool payloads.
