---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Edit the display name and intention
  kind: actor
  entities: []
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
- text: Name and intention commit or focus-loss save uses their byte/codepoint limits (63/40 and 127/90).
  kind: product
  entities:
  - entity: profile
    effect: changes
    facts:
    - Display name
    - Intention
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

# Edit profile — name and intention

## Trigger

Edit the display name and intention.

## Outcome

Name and intention commit or focus-loss save uses their byte/codepoint limits (63/40 and 127/90).
