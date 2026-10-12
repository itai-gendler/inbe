---
kind: validation
routes:
  desktop: Native desktop
steps:
- text: Ask Lumi to reopen the referenced item
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: If current mode, installed Lumi or the required target app makes this tool unavailable, refuse before
    reading protected target data. An unresolved request with available tools follows only its permitted lookup
    branch and still performs no mutation.
  kind: condition
  entities:
  - entity: profile
    effect: reads
    facts:
    - Account access mode
  - entity: apps-settings
    effect: reads
    facts:
    - Lumi installed
    - Lists available
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
- text: Only with nondelegated tool mode, installed Lumi and the required target app available, attempt the
    bounded target lookup; an absent or unresolved target stops the action without mutation.
  kind: condition
  actor: user
  entities:
  - entity: todo
    effect: reads
    facts:
    - Identity
    - Title
    - Completion
  contexts:
    desktop:
      place: desktop-app::lumi
- text: The referenced target is unresolved or the mapped tool path is unavailable; no requested item operation
    is performed.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::lumi
  actor: user
references:
- kind: code
  role: implementation
  target: apps/lists/lists.zi
- kind: code
  role: implementation
  target: src/screens/elist_screen.zi
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi
- kind: code
  role: implementation
  target: src/screens/lumi_screen.zi#LumiPerform
---

# Reopen todo — lumi target or tools unavailable

## Trigger

Reopen todo in the selected List.

## Outcome

The referenced target is unresolved or the mapped tool path is unavailable; no Todo operation is performed.
