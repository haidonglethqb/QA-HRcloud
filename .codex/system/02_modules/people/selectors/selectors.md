# People Module — Selectors

> Module-specific selectors for the People module. Use these when writing automation code or browsing this module.
> For shared selectors (navbar, sidebar, modals, toasts), see `../../01_navigation/common_selectors.md`.

---

## Selector Strategy

Follow this priority order when identifying elements:

1. **Role-based** (Preferred) — `getByRole('button', { name: 'Save' })`
2. **Data attributes** — `[data-test-id="..."]`
3. **Automation class** — `.aut-button-add` (`.aut-*` prefix)
4. **XPath** (Last resort) — Document why other strategies failed

---

## People Grid (Employee List)

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Add Employee Button | `.aut-button-add` | Class | Top-right toolbar |
| Employee Name Links | `.aut-button-xEmployeeDetail` | Class | First and last name are separate `<a>` elements |
| Grid Rows | `getByRole('row')` | Role | Filter for data rows using label check |
| Employee Checkbox | `row.locator('label').first()` | Combined | Label wraps checkbox input |
| Master Checkbox (Select All) | First row with label | Combined | Row 0 in data rows |
| Bulk Actions Dropdown | Standard dropdown pattern | Standard | Uses shared dropdown selectors |

---

## Add Employee Flyout

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| First Name Field | `getByRole('textbox', { name: 'First Name*' })` | Role | Required field (asterisk) |
| Last Name Field | `getByRole('textbox', { name: 'Last Name*' })` | Role | Required field |
| Email Field | `getByRole('textbox', { name: 'Email*' })` | Role | Required field |
| Save Button | `getByRole('button', { name: 'Save' })` | Role | Submit form |
| Cancel Button | `getByRole('button', { name: 'Cancel' })` | Role | Close without saving |
| Flyout Container | `.ngv-flyout` | Class | Parent container |

---

## Employee Profile Flyout

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Overview Tab | Tab role selector | Role | Default tab |
| Employment Tab | Tab role selector | Role | Position, department, manager |
| Documents Tab | Tab role selector | Role | Uploaded files |
| Tasks Tab | Tab role selector | Role | Assigned tasks |
| Actions Dropdown Button | `.btn-primary.dropdown-toggle.aut-dropdown` | Class | Opens actions menu |

---

## Actions Flyouts (from Employee Profile)

**Applies to:** ChangeSalary, ChangePosition, ChangeStartDate, AddBonus, Terminate, ChangeEmploymentStatus

| Component | Selector Pattern | Type | Notes |
|-----------|------------------|------|-------|
| Input Fields | `getByRole('textbox', { name: 'Field Label*' })` | Role | Label-based identification |
| Dropdowns | `getByRole('combobox', { name: 'Field Label*' })` | Role | Select fields |
| Date Pickers | Date picker pattern | Combined | May require calendar navigation |
| Save/Submit Button | `getByRole('button', { name: 'Save' })` | Role | Consistent across flyouts |
| Cancel Button | `getByRole('button', { name: 'Cancel' })` | Role | Consistent across flyouts |

---

## Organizational Tabs (Department, Location, Position, Division)

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Add Button | `.aut-button-add` | Class | Standard across all org pages |
| Grid Rows | `getByRole('row')` | Role | Department/Location/Position grids |
| Edit Button | Row-specific | Combined | Per-row action |
| Delete Button | Row-specific | Combined | Per-row action |

---

## Module-Specific Gotchas

### Employee name links are split
Employee first name and last name are rendered as **separate `<a>` elements**. When capturing the full name, concatenate both text contents.

### Selecting employees skips HR Admin row
Row 0 = select-all checkbox, Row 1 = HR Admin account. When selecting test employees for bulk actions, start from Row 2.

### Bulk actions require explicit selection
Always select employees via checkboxes **before** opening the bulk actions dropdown. The dropdown options are disabled if no employees are selected.

### Delete requires Super Admin
The "Delete" option in bulk actions is only visible to Super Admin accounts. Use `HRCLOUD_ADMIN` with delete permissions.
