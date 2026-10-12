---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Accept the first language choice
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::language
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
      place: desktop-app::language
  actor: user
- text: Language preference is saved and the Product carries User into initial Apps selection.
  kind: product
  entities:
  - entity: device-settings
    effect: changes
    facts:
    - Preferred language
    - System language
  contexts:
    desktop:
      place: desktop-app::apps
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_device.zi
- kind: code
  role: implementation
  target: src/screens/language_screen.zi
---

# Change device settings — first language

## Trigger

Accept the first language choice.

## Outcome

Language preference is saved and the Product carries User into initial Apps selection.
