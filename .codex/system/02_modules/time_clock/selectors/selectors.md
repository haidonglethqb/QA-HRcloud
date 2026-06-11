# Time Clock Module — Selectors

> Module-specific selectors for the Time Clock module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Clock In Button | `button:has-text("Clock In")` | Text | Start time entry |
| Clock Out Button | `button:has-text("Clock Out")` | Text | End time entry |
| Timesheet Grid | Grid pattern | Standard | Manager approval view |
| Approve Timesheet | `button:has-text("Approve")` | Text | Manager approves |

<!-- TODO: Add more selectors as they are discovered during test automation -->
