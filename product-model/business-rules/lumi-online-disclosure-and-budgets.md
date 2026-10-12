---
appliesTo:
- type: entity
  id: lumi-message
- type: entity
  id: apps-settings
- type: entity
  id: account
references:
- kind: code
  role: implementation
  target: src/cells/lumi_store.zi
- kind: code
  role: implementation
  target: src/app/app_launcher_state.zi
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
---

# Online Lumi uses bounded enabled context and tool rounds

Enabled online preference, local key, idle state and nondelegated mode precede the outbound model request. The last four messages and permitted app context can leave the device; bounded tool rounds, twelve-call budgets and repeated-call handling constrain execution.
