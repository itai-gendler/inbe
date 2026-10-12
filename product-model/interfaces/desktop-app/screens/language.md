---
entities:
- entity: device-settings
  shows:
  - Preferred language
  - System language
  - Orientation
  - Fullscreen
  - Keyboard
  - Startup
  - Close action
  - Background play
  collects:
  - Preferred language
  - System language
references:
- kind: code
  role: implementation
  target: src/screens/language_screen.zi
---

# Language

Initial language acceptance, including explicit shipped locale or system-language selection, before app selection.
