---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read friends, requests and available practice statistics
  kind: actor
  entities:
  - entity: friend
    effect: reads
    facts: []
  contexts:
    desktop:
      place: desktop-app::friends
  actor: user
- text: The current relationship cache supplies displayed identities, incoming and outgoing requests and available
    practice statistics before refresh completes.
  kind: condition
  entities:
  - entity: friend
    effect: reads
    facts:
    - Identity
    - Relationship
    - Display identity
    - Practice statistics
  - entity: friend-request
    effect: reads
    facts:
    - Identity
    - Direction
    - Display identity
  contexts:
    desktop:
      place: desktop-app::friends
  actor: user
- text: Cached relationship and incoming/outgoing request identities are shown and accepted refreshed statistics
    update their presentation.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::friends
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/profile_social.zi
- kind: code
  role: implementation
  target: src/screens/leaderboard_screen.zi
---

# Browse friends — friends and requests

## Trigger

Read friends, requests and available practice statistics.

## Outcome

Cached relationship and incoming/outgoing request identities are shown and accepted refreshed statistics update their presentation.
