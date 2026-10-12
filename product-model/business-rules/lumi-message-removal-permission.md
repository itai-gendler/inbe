---
appliesTo:
- type: entity
  id: lumi-message
  effect: removes
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
permits:
- actors:
  - user
  when:
  - entity: profile
    fact: Account access mode
    is-not: Delegated
- unattended: true
  when:
  - entity: profile
    fact: Account access mode
    is-not: Delegated
---

# User and applicable Product processing perform Lumi message removal

User removes an addressed retained non-chart row from active history; the synthetic greeting is not a stored row. Applicable archive application preserves its deletion marker, and delegated native tool mode does not expose interactive deletion.
