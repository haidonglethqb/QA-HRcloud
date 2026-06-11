# HR Cloud Settings Module — Selectors

> Module-specific selectors for the HR Cloud Settings module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Company Info Form | Settings form pattern | Combined | Company details |
| Positions Grid | Grid pattern | Standard | Position management |
| Departments Grid | Grid pattern | Standard | Department management |
| Locations Grid | Grid pattern | Standard | Location management |
| Import Data Button | `button:has-text("Import")` | Text | Data import tool |
| Save Settings Button | `getByRole('button', { name: 'Save' })` | Role | Save changes |

<!-- TODO: Add more selectors as they are discovered during test automation -->
