---
domain: appearance
references:
- kind: code
  role: implementation
  target: src/screens/settings/settings_appearance.zi
---

# Custom appearance

The custom source being edited and its saved and applied forms.

## Information kept

- **Scope** — The custom-source slot currently selected in the appearance editor.
- **Draft source** — Editable source that can differ from the saved and applied versions.
- **Saved source** — Source last persisted and reconciled by successful readback.
- **Applied source** — Last valid source currently applied as the preview.
- **Diagnostics** — Parse or validation diagnostics for the draft.
- **Undo information** — Available earlier draft text used by Undo; it does not itself commit the source.
