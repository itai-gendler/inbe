---
domain: diary
relations:
- entity: diary-photo
  verb: references
  cardinality: many-to-many
references:
- kind: code
  role: implementation
  target: src/cells/diary_store.zi
- kind: code
  role: implementation
  target: src/cells/diary_records.zi
---

# Diary entry

A date-addressed Diary document.

## Information kept

- **Date** — Selected local calendar date addressing the entry; future dates are not editable through the mapped path.
- **Text** — Text content read from or written to this dated entry.
- **Document** — Versioned document containing the entry content and attachment references.
- **Photo references** — Safe names identifying retained photo content referenced by the document.
- **Document validity** — Whether the loaded document has the supported structure and complete record content needed for editing.
- **Save outcome** — Observed save success or failure; it does not imply atomic rollback.
