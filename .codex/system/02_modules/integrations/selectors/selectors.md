# Integrations Module — Selectors

> Module-specific selectors for the Integrations module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Integration List | Grid/card pattern | Combined | All configured integrations |
| Add Integration Button | `.aut-button-add` | Class | New integration |
| Integration Logs | Log viewer pattern | Combined | Sync history |
| Sync Now Button | `button:has-text("Sync")` | Text | Manual sync trigger |

<!-- TODO: Add more selectors as they are discovered during test automation -->
