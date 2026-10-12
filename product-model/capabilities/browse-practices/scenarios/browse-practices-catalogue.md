---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Browse practices — catalogue
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::practices
  actor: user
- text: The installed practice choice exposes the four shipped practice families; selecting a family reaches its
    guide and saved configuration.
  kind: condition
  entities:
  - entity: apps-settings
    effect: reads
    facts:
    - Practices available
  contexts:
    desktop:
      place: desktop-app::practices
  actor: user
- text: Wim Hof, Meditation, Breathing Patterns and Sun Salutation are available as the shipped choices.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::practices
  actor: user
references:
- kind: code
  role: implementation
  target: src/practices/practice_actions.zi
- kind: code
  role: implementation
  target: src/app/activity_start.zi
- kind: code
  role: implementation
  target: src/practices/session_results.zi
- kind: code
  role: implementation
  target: src/practices/whm/whm_session.zi
---

# Browse practices — catalogue

## Trigger

Browse practices — catalogue.

## Outcome

Wim Hof, Meditation, Breathing Patterns and Sun Salutation are available as the shipped choices.
