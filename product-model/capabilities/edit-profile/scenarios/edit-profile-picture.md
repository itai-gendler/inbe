---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Edit the profile picture
  kind: actor
  entities:
  - entity: profile
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::profile
  actor: user
- text: The selected local name, intention or picture identifies the preference being edited; name and intention
    use the exposed byte and codepoint bounds.
  kind: condition
  entities:
  - entity: profile
    effect: reads
    facts:
    - Local data context
    - Display name
    - Intention
    - Picture
    - Setup progress
    - Local counts
    - Account access mode
  contexts:
    desktop:
      place: desktop-app::profile
  actor: user
- text: The selected native picture updates local profile preferences through the image picker.
  kind: product
  entities:
  - entity: profile
    effect: changes
    facts:
    - Picture
  contexts:
    desktop:
      place: desktop-app::profile
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/profile_screen.zi
- kind: code
  role: implementation
  target: src/app/profile_image_picker.zi
---

# Edit profile — picture

## Trigger

Edit the profile picture.

## Outcome

The selected native picture updates local profile preferences through the image picker.
