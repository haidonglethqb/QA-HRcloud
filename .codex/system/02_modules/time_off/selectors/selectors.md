# Time Off Module — Selectors

> Module-specific selectors for the Time Off module.
> For shared selectors (navbar, sidebar, modals, toasts), see `../../01_navigation/common_selectors.md`.

---

## Selector Strategy

1. **Role-based** (Preferred) — `getByRole('button', { name: 'Save' })`
2. **Data attributes** — `[data-test-id="..."]`
3. **Automation class** — `.aut-*` prefix
4. **XPath** (Last resort)

---

## Time Off Dashboard

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| My Time Off Tab | Tab role selector | Role | Employee view |
| Requests Tab | Tab role selector | Role | Manager/Admin view |
| Policies Tab | Tab role selector | Role | Admin only |
| Balance Grid Tab | Tab role selector | Role | Admin view |
| Request Time Off Button | `button:has-text("Request Time Off")`, `button:has-text("New Request")` | Text | Opens request form |

---

## Time Off Request Form

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Time Off Type Dropdown | `select[name="timeOffType"]`, `[class*="time-off-type"]` | Attribute | Select leave type |
| Start Date | Date picker pattern | Combined | First day of leave |
| End Date | Date picker pattern | Combined | Last day of leave |
| Date Range Picker | `.date-range-picker`, `[class*="date-range"]` | Class | Combined start+end picker |
| Notes/Reason Textarea | `textarea`, `[class*="text-area"]` | Tag | Optional reason field |
| Submit Button | `getByRole('button', { name: 'Submit' })` | Role | Submit request |

---

## Manager Approval View

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Approve Button | `button:has-text("Approve")` | Text | Approve request |
| Deny/Reject Button | `button:has-text("Deny")`, `button:has-text("Reject")` | Text | Deny request |
| Request Details Flyout | `.ngv-flyout` | Class | Opens when clicking a request |
| Employee Name | Request row content | Combined | Shows who requested |
| Date Range | Request row content | Combined | Shows requested dates |

---

## Calendar View

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Calendar Container | `.calendar-view`, `[class*="calendar"]` | Class | Main calendar |
| Day Cell | Calendar day pattern | Combined | Click to see events |
| Event Entry | Calendar event pattern | Combined | Time off entries shown as blocks |

---

## Policies (Admin)

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Create Policy Button | `.aut-button-add` or `button:has-text("Add Policy")` | Combined | New time off policy |
| Policy Grid | Grid pattern | Standard | List of all policies |
| Accrual Settings | Form fields within policy detail | Combined | Balance accrual configuration |

---

## Module-Specific Gotchas

### Balance not deducted immediately
Time Off balance is deducted **after approval**, not after request submission. This is expected behavior.

### Manager sees only direct reports
A Manager account only sees Time Off requests from their direct reports. Other employees' requests do NOT appear in their queue.

### Employee cannot approve own request
An employee can request Time Off but cannot approve their own request. A manager or admin must approve.

### Calendar shows approved only
The shared calendar only shows **approved** time off entries by default. Pending requests may not appear.
