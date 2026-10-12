---
domain: account
references:
- kind: code
  role: implementation
  target: src/storage/sync_account.zi
- kind: code
  role: implementation
  target: src/app/app_sync.zi
---

# Sync node

An independently addressed configured synchronization node.

## Information kept

- **Scope** — Current account context containing this configured node and its exchange state.
- **Address** — Normalized configured node URL.
- **Order** — Saved position in the bounded configured node list.
- **Preferred** — Whether this address is the selected preferred node.
- **Active** — Whether exchange currently uses this node.
- **Cursor** — Node-specific applied or seen exchange position.
- **Clock** — Node-specific exchange clock used by the implemented protocol.
- **Hash** — Node-specific server-state hash retained for exchange.
