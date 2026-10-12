---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Read practice comparisons
  kind: actor
  entities: []
  contexts:
    desktop:
      place: desktop-app::leaderboard
  actor: user
- text: Available local and friend practice statistics determine comparisons; absence of usable statistics produces
    the no-data result.
  kind: condition
  entities:
  - entity: friend
    effect: reads
    facts:
    - Identity
    - Relationship
    - Display identity
    - Practice statistics
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
      place: desktop-app::leaderboard
  actor: user
- text: Without usable statistics, a no-data comparison result is shown instead of fabricated rankings.
  kind: product
  entities: []
  contexts:
    desktop:
      place: desktop-app::leaderboard
  actor: user
references:
- kind: code
  role: implementation
  target: src/screens/profile_social.zi
- kind: code
  role: implementation
  target: src/screens/leaderboard_screen.zi
---

# Browse leaderboard — no data

## Trigger

Read practice comparisons.

## Outcome

Without usable statistics, a no-data comparison result is shown instead of fabricated rankings.
