# User Management Module — Selectors

> Module-specific selectors for the User Management module.
> For shared selectors, see `../../01_navigation/common_selectors.md`.

## Selector Strategy

1. **Role-based** → 2. **Data attributes** → 3. **`.aut-*`** → 4. **XPath**

---

## Known Selectors

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| User List Grid | Grid pattern | Standard | All users |
| Add User Button | `.aut-button-add` | Class | Create new user |
| Role Dropdown | Dropdown pattern | Standard | Assign roles |
| SSO Settings | Settings form pattern | Combined | SSO configuration |
| 2FA Toggle | Toggle pattern | Combined | Enable/disable 2FA |

<!-- TODO: Add more selectors as they are discovered during test automation -->
