---
appliesTo:
- type: entity
  id: apps-settings
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
---

# Activated packages pass release checks and trial handling

Publisher trust/signature, nondecreasing sequence, equal-sequence hash, host API compatibility, dependencies and payload checks precede activation. Unproved/failed cached trials fall back to known working content; no stronger cryptographic operational guarantee is asserted.
