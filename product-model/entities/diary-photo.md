---
domain: diary
references:
- kind: code
  role: implementation
  target: src/cells/diary_store.zi
---

# Diary photo

Retained original attachment content; removing an entry reference retains these bytes.

## Information kept

- **Name** — Safe identifiable name under which the original attachment is retained.
- **Content** — Retained original selected-image bytes.
- **Format** — Detected supported image format used to validate attachment input.
- **Byte size** — Size of selected image content, limited to sixteen MB through the mapped attachment path.
