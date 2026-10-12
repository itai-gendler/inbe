---
entities:
- entity: profile
  shows:
  - Local data context
  - Display name
  - Intention
  - Picture
  - Setup progress
  - Local counts
  - Account access mode
- entity: friend
  shows:
  - Identity
  - Relationship
  - Display identity
  - Practice statistics
references:
- kind: code
  role: implementation
  target: src/screens/leaderboard_screen.zi
---

# Leaderboard

Derived comparisons of available personal and friend practice statistics, including the no-data outcome.
