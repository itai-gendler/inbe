---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Change general notification preferences
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
- text: General preferences for incoming relationship requests and scheduled day prompts are selected independently
    of platform delivery.
  kind: condition
  entities:
  - entity: notifications-settings
    effect: reads
    facts:
    - Friend requests
    - Habit reminders
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
- text: General general notification preferences persist; actual notification delivery is separate.
  kind: product
  entities:
  - entity: notifications-settings
    effect: changes
    facts:
    - Friend requests
    - Habit reminders
  contexts:
    desktop:
      place: desktop-app::notifications
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_notifications.zi
---

# Change notifications settings — general

## Trigger

Change general notification preferences.

## Outcome

General friend-request and Habit-reminder preferences persist; actual notification delivery is separate.
