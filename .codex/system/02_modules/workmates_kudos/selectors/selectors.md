# Workmates & Kudos Module — Selectors

> Module-specific selectors for the Workmates & Kudos module.
> For shared selectors (navbar, sidebar, modals, toasts), see `../../01_navigation/common_selectors.md`.

---

## Selector Strategy

1. **Role-based** (Preferred)
2. **Data attributes**
3. **Automation class** (`.aut-*`)
4. **XPath** (Last resort)

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Company Feed | `.company-feed`, `[class*="feed"]` | Class | Main feed area |
| Post Card | `.post-card`, `[class*="post-card"]` | Class | Individual post |
| Create Post Button | `button:has-text("Create Post")` | Text | New post action |
| Post Input | `.post-input`, `textarea[placeholder*="post"]` | Class | Post text area |
| Like/React Button | `button[aria-label*="react"]`, `.reaction-btn` | Attribute | React to a post |
| Comment Input | `input[placeholder*="comment"]` | Attribute | Add comment |
| Channel List | `.channel-list`, `[class*="channel-list"]` | Class | All channels |
| Kudos Button | `button:has-text("Kudos")`, `.kudos-button` | Text | Give kudos |

---

<!-- TODO: Add more selectors as they are discovered during test automation -->
