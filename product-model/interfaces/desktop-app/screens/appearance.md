---
entities:
- entity: appearance-settings
  shows:
  - Theme
  - Source selection
  - Mode
  - Scale
  collects:
  - Theme
  - Source selection
  - Mode
  - Scale
- entity: custom-appearance
  shows:
  - Scope
  - Draft source
  - Saved source
  - Applied source
  - Diagnostics
  - Undo information
  collects:
  - Draft source
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
---

# Appearance

Appearance preferences and one selected custom-source slot, including draft, saved/applied source, validation diagnostics and editor history.
