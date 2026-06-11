# Mobile App Module — Selectors

> Module-specific selectors for the Mobile App module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Mobile viewport | Viewport resize | N/A | Test at 375×812 (iPhone) or 390×844 |
| Hamburger Menu | Mobile nav pattern | Combined | Replaces sidebar on mobile |
| Bottom Navigation | Mobile tab bar | Combined | Module switching on mobile |

<!-- TODO: Add more selectors as they are discovered during mobile testing -->
