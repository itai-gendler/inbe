---
appliesTo:
- type: entity
  id: custom-appearance
  effect: changes
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
permits:
- actors:
  - user
---

# User performs Custom appearance change

User previews, saves, discards, undoes, formats or resets the selected draft. Invalid source preserves the last valid applied preview, and known saved source reconciles only after successful readback.
