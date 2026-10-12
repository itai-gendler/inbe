---
acts: external
kind: person
relations:
- entity: profile
  verb: uses
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: src/screens/profile_screen.zi
---

# User

A person using the local application context.
