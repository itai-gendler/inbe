---
appliesTo:
- type: entity
  id: feedback-proposal
  effect: reads
references:
- kind: code
  role: implementation
  target: src/cells/feedback_store.zi
permits:
- actors:
  - user
  when:
  - entity: profile
    fact: Account access mode
    is-not: Delegated
---

# User in nondelegated mode reads feedback proposal

Interactive payloads are absent from delegated row rendering; ordinary archived text can remain visible.
