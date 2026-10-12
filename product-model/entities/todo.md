---
domain: lists
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
---

# Todo

An item in a List.

## Information kept

- **Identity** — Address distinguishing this item within retained Lists.
- **Scope** — Current local account data context used to load and change this item.
- **Parent List** — The existing addressed List containing the item.
- **Title** — Trimmed nonblank item title.
- **Comment** — Saved comment attached to the item.
- **Order** — Saved position within its parent List.
- **Completion** — Whether the item is incomplete or complete.

## States

### Incomplete

The item remains open in its parent and participates in incomplete-item filtering.

### Complete

Saved completion marks the item done and changes completion filtering.
