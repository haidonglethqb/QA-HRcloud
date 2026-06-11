# Advanced Module — Selectors

> Module-specific selectors for the Advanced module (E-forms, E-signatures, Automations).
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| E-form Builder | Form builder pattern | Combined | Create/edit e-forms |
| E-signature Pad | Signature pad component | Combined | Signing interface |
| Automation Rules List | Grid pattern | Standard | All automation rules |
| Create Rule Button | `.aut-button-add` | Class | New automation rule |

<!-- TODO: Add more selectors as they are discovered during test automation -->
