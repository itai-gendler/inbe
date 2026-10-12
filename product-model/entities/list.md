---
domain: lists
relations:
- entity: todo
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: src/storage/storage_elist.zi
---

# List

An independently named List.

## Information kept

- **Identity** — Address distinguishing the named List.
- **Scope** — Current local account data context used to load and change the List.
- **Title** — Trimmed nonblank displayed List title.
- **Order** — Saved position among Lists.
