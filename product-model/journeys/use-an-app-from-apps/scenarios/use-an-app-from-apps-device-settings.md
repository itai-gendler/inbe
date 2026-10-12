---
kind: primary
result: achieved
routes:
  desktop: Native desktop
steps:
- text: Choose the app catalogue entry to open
  kind: actor
  actor: user
  capability: open-app
  entities: []
  contexts:
    desktop:
      place: desktop-app::apps
- text: Activate the selected destination and carry User into its working context
  kind: product
  actor: user
  capability: open-app
  entities: []
  contexts:
    desktop:
      place: desktop-app::device
- text: Change a native device preference in the selected Device section
  kind: actor
  actor: user
  capability: change-device-settings
  entities: []
  contexts:
    desktop:
      place: desktop-app::device
- text: Save the chosen native device preference without resetting the selected settings section
  kind: product
  actor: user
  capability: change-device-settings
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
references:
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/app/app_nav_state.zi
- kind: code
  role: implementation
  target: src/app/app_launcher.zi
- kind: code
  role: implementation
  target: src/screens/settings/settings_device.zi
---

# Use an app from Apps — device settings

## Trigger

User opens Settings from Apps while Device is the selected section or its initial default. The selected/default Settings section is Device.

## Outcome

User reaches device and completes the change device settings operation.
