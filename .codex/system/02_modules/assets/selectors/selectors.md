# Assets Module — Selectors

> Module-specific selectors for the Assets module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Asset List | Grid pattern | Standard | All assets |
| Add Asset Button | `.aut-button-add` or `button:has-text("Add Asset")` | Combined | New asset |
| Asset Detail | Flyout pattern | Combined | Asset information |

<!-- TODO: Add more selectors as they are discovered during test automation -->
