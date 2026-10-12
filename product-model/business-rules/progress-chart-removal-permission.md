---
appliesTo:
- type: entity
  id: progress-chart
  effect: removes
references:
- kind: code
  role: implementation
  target: src/cells/lumi_progress.zi
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

# User and applicable Product processing perform Progress chart removal

User deletes the selected retained chart in nondelegated tool mode. Applicable archive deletion markers exclude the snapshot from active history.
