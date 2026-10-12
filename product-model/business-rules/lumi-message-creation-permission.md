---
appliesTo:
- type: entity
  id: lumi-message
  effect: creates
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
permits:
- actors:
  - user
- unattended: true
---

# User and applicable Product processing perform Lumi message creation

User input and applicable Product replies or practice summaries create current-scope archived rows. Valid history and current identity are checked separately; outbound online failure retains input without fabricating a completed answer.
