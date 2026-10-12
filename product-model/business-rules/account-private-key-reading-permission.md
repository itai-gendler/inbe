---
appliesTo:
- type: entity
  id: account
  effect: reads
  facts:
  - Private key
  contexts:
  - place: desktop-app::account
references:
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
permits:
- actors:
  - user
  when:
  - entity: profile
    fact: Account access mode
    is: Account key
---

# User in account-key mode reads the local private key

Local key export discloses the available private key; delegated loading supplies no owner private key. Key presence is a precondition, not verified human ownership.
