---
appliesTo:
- type: entity
  id: custom-appearance
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
---

# Invalid appearance source preserves the valid preview

Preview, save/readback, discard, undo, formatting and empty reset have distinct draft/applied/saved effects. Invalid input retains the prior valid preview; readback failure does not pretend known saved source changed.
