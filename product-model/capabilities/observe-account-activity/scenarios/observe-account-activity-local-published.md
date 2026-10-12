---
kind: primary
routes:
  desktop: Native desktop
steps:
- text: Enabled account activity reaches a local progress boundary or the ten-second publication interval
  kind: condition
  entities:
  - entity: wim-hof-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: meditation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: patterns-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: sun-salutation-practice
    effect: reads
    facts:
    - Origin
    - Activity identity
    - Publication
    - Revision
  - entity: sync-settings
    effect: reads
    facts:
    - Enabled
    - Exchange status
    - Retry status
    - Pending review
  - entity: account
    effect: reads
    facts:
    - Identity
  contexts:
    desktop:
      place: desktop-app
  unattended: true
- text: When wim hof is the active originating family, attempt its boundary or ten-second publication
  kind: product
  entities:
  - entity: wim-hof-practice
    effect: changes
    facts:
    - Publication
    - Revision
  contexts:
    desktop:
      place: desktop-app
- text: When meditation is the active originating family, attempt its boundary or ten-second publication
  kind: product
  entities:
  - entity: meditation-practice
    effect: changes
    facts:
    - Publication
    - Revision
  contexts:
    desktop:
      place: desktop-app
- text: When patterns is the active originating family, attempt its boundary or ten-second publication
  kind: product
  entities:
  - entity: patterns-practice
    effect: changes
    facts:
    - Publication
    - Revision
  contexts:
    desktop:
      place: desktop-app
- text: When sun salutation is the active originating family, attempt its boundary or ten-second publication
  kind: product
  entities:
  - entity: sun-salutation-practice
    effect: changes
    facts:
    - Publication
    - Revision
  contexts:
    desktop:
      place: desktop-app
references:
- kind: code
  role: implementation
  target: src/app/account_activity.zi
- kind: code
  role: implementation
  target: src/app/account_activity_model.zi
---

# Observe account activity — local published

## Trigger

Read observed activity or publish the local origin.

## Outcome

The active origin attempts publication at boundaries and ten-second intervals; only that active family publishes. No remote observer creates a duplicate saved result.

## Decision points

### Active practice family

Which originating process is active?

- wim hof → attempt publication of that one process.
- meditation → attempt publication of that one process.
- patterns → attempt publication of that one process.
- sun salutation → attempt publication of that one process.
