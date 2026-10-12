---
appliesTo:
- type: entity
  id: feedback-proposal
  effect: creates
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

# User performs Feedback proposal creation

User-attributed feedback drafting retains bounded title, message and context for a later human decision in nondelegated tool mode; no report is sent by drafting.
