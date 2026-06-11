# Recruit Module — Selectors

> Module-specific selectors for the Recruit module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Job Listings Grid | Grid pattern | Standard | All job postings |
| Create Job Button | `.aut-button-add` or `button:has-text("Create Job")` | Combined | New job posting |
| Applicant List | Grid pattern | Standard | All applicants |
| Applicant Status | Dropdown pattern | Standard | Move through pipeline stages |
| Hire Button | `button:has-text("Hire")` | Text | Convert applicant to employee |

<!-- TODO: Add more selectors as they are discovered during test automation -->
