---
appliesTo:
- type: entity
  id: feedback-proposal
  effect: changes
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

# User performs Feedback proposal change

User accepts or dismisses the selected draft in nondelegated tool mode. Acceptance queues its stable report identity before the decision write; a marker failure can leave queued work and the still-proposed draft.
