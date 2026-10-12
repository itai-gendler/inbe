---
references:
- kind: code
  role: implementation
  target: src/screens/profile_screen.zi
---

# Friend

Cached friend information; it does not act through this interface.

## Information kept

- **Identity** — Public identity distinguishing the cached friend.
- **Relationship** — Cached friend relationship in the current account context.
- **Display identity** — Available public identifier or alias displayed for this friend.
- **Practice statistics** — Fetched practice statistics used for friend comparisons; refresh failure retains the available cache.
