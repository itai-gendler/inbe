---
appliesTo:
- type: entity
  id: progress-chart
  effect: creates
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

# User and applicable Product processing perform Progress chart creation

User requests a supported stored-progress metric over one through thirty-one days in nondelegated tool mode. Applicable archive application retains the snapshot rather than recomputing an online answer.
