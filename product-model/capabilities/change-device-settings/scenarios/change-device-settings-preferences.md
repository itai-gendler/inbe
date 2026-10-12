---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Change the exposed native preferences
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::device
  actor: user
- text: The language/system-language choice and native orientation, fullscreen, keyboard, startup, close and background
    preferences identify the fields to save.
  kind: condition
  entities:
  - entity: device-settings
    effect: reads
    facts:
    - Preferred language
    - System language
    - Orientation
    - Fullscreen
    - Keyboard
    - Startup
    - Close action
    - Background play
  contexts:
    desktop:
      place: desktop-app::device
  actor: user
- text: The exposed native orientation/fullscreen/keyboard/startup/close/background preferences persist.
  kind: product
  entities:
  - entity: device-settings
    effect: changes
    facts:
    - Preferred language
    - System language
    - Orientation
    - Fullscreen
    - Keyboard
    - Startup
    - Close action
    - Background play
  contexts:
    desktop:
      place: desktop-app::device
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_device.zi
- kind: code
  role: implementation
  target: src/screens/language_screen.zi
---

# Change device settings — preferences

## Trigger

Change the exposed native preferences.

## Outcome

The exposed native orientation/fullscreen/keyboard/startup/close/background preferences persist.
