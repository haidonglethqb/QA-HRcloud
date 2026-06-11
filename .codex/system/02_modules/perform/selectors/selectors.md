# Perform Module — Selectors

> Module-specific selectors for the Perform module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Cycle List | `.cycle-list`, `[class*="cycle-list"]` | Class | Performance cycles |
| Review Form | `.review-form`, `[class*="review-form"]` | Class | Review submission |
| Rating Stars | `.rating-stars`, `[class*="rating"]` | Class | Rating scale |
| Goal List | `.goal-list`, `[class*="goal-list"]` | Class | Employee goals |
| Submit Review Button | `button:has-text("Submit Review")` | Text | Finalize review |

<!-- TODO: Add more selectors as they are discovered during test automation -->
