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
  collects:
  - Display name
  - Intention
  - Picture
- entity: account
  shows:
  - Identity
  - Alias
references:
- kind: code
  role: implementation
  target: src/screens/profile_screen.zi
---

# Profile

Local display name, intention, picture and derived counts together with available public account identity.
