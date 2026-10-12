---
appliesTo:
- type: entity
  id: meditation-practice
  effect: reads
  facts:
  - Origin
  - Activity identity
  - Publication
  - Revision
  - Duration
  - Remaining time
  - Elapsed progress
  - Extension state
  - Waiting state
  - Pause
  - Result values
  - Save outcome
  - Pending control
  - Control outcome
references:
- kind: code
  role: implementation
  target: src/app/account_activity.zi#ActivityAvailable
- kind: code
  role: implementation
  target: src/app/account_activity_view.zi#ActivityDrawRemote
permits:
- actors:
  - user
  when:
  - fact: Origin
    is: Local ordinary
- actors:
  - user
  when:
  - fact: Origin
    is: Local Lumi
- actors:
  - user
  when:
  - entity: sync-settings
    fact: Enabled
    is: true
- unattended: true
  when:
  - fact: Origin
    is: Local ordinary
- unattended: true
  when:
  - fact: Origin
    is: Local Lumi
- unattended: true
  when:
  - entity: sync-settings
    fact: Enabled
    is: true
---

# User and Product read local activity and enabled observed activity

Local originating activity remains available offline. Reading the observed device’s activity requires the enabled activity feature; request credentials and identity are checked separately. Origin distinguishes the local ordinary or Lumi process from the observed device.
