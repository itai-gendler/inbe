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
  - Orientation
  - Fullscreen
  - Keyboard
  - Startup
  - Close action
  - Background play
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_device.zi
---

# Device

Preferred or system language and native device preferences for orientation, fullscreen, keyboard, startup, closing and supported background behavior.
