# Offboard Module — Selectors

> Module-specific selectors for the Offboard module.
> For shared selectors (navbar, sidebar, modals, toasts), see `../../01_navigation/common_selectors.md`.

---

## Selector Strategy

1. **Role-based** (Preferred) — `getByRole('button', { name: 'Save' })`
2. **Data attributes** — `[data-test-id="..."]`
3. **Automation class** — `.aut-*` prefix
4. **XPath** (Last resort)

---

## Offboard Dashboard

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Employees Tab | Tab role selector | Role | View employees in offboarding (default) |
| Checklists Tab | Tab role selector | Role | Offboard checklist templates |

---

## Termination Flow (Initiated from People Module)

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Change Status Button | Actions dropdown in employee profile | Combined | Opens status change menu |
| Terminate Option | Menu item with text "Terminate" | Text | In the actions dropdown |
| Termination Date Field | Date picker pattern | Combined | Required field |
| Termination Reason Dropdown | Standard dropdown pattern | Standard | Resignation, Termination, Retirement, etc. |
| Revoke Access Toggle | Toggle/Checkbox | Combined | Immediately or on termination date |
| Confirm Button | `getByRole('button', { name: 'Confirm' })` | Role | Finalize termination |

---

## Offboarding Checklist

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Checklist List | `.checklist-list`, `[class*="checklists"]` | Class | All checklist templates |
| Checklist Card | `.checklist-card`, `[class*="checklist-card"]` | Class | Individual checklist |
| Task List | `.task-list`, `[class*="task-list"]` | Class | Tasks within a checklist |
| Complete Task | `button:has-text("Complete")` | Text | Mark offboard task as done |

---

## Rehire Flow (from Inactive Employees)

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Inactive Filter | Filter/dropdown in People grid | Combined | Show inactive employees |
| Rehire Button | `button:has-text("Rehire")` | Text | On inactive employee profile |
| New Start Date Field | Date picker pattern | Combined | Required for rehire |
| Confirm Rehire | `getByRole('button', { name: 'Save' })` | Role | Finalize rehire |

---

## Module-Specific Gotchas

### Termination starts in People, not Offboard
The termination action is triggered from the **People module** (Employee Profile → Actions → Terminate), not from the Offboard dashboard directly.

### Access revocation timing
Access revocation can be set to "immediately" or "on termination date". If testing post-termination login behavior, check which option was selected.

### Offboard tasks assigned after confirmation
Offboarding checklist tasks are only assigned **after** termination is confirmed. Do not look for tasks before completing the termination flow.

### Rehire creates new onboarding flow
When rehiring, a new onboarding checklist triggers (if configured). The employee's historical data is preserved.
