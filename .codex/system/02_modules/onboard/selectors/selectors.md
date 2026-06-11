# Onboard Module — Selectors

> Module-specific selectors for the Onboard module.
> For shared selectors (navbar, sidebar, modals, toasts), see `../../01_navigation/common_selectors.md`.

---

## Selector Strategy

1. **Role-based** (Preferred) — `getByRole('button', { name: 'Save' })`
2. **Data attributes** — `[data-test-id="..."]`
3. **Automation class** — `.aut-*` prefix
4. **XPath** (Last resort)

---

## Onboard Dashboard

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Checklists Tab | Tab role selector | Role | View checklist templates |
| Employees Tab | Tab role selector | Role | View employees in onboarding (default) |
| Portals Tab | Tab role selector | Role | Configure onboarding portals |
| Create Checklist Button | `.aut-button-add` | Class | Opens checklist builder |

---

## Checklist Builder

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Schedule Section | Section pattern | Combined | Step 1 of 3: configure trigger |
| Tasks Section | Section pattern | Combined | Step 2 of 3: add/order tasks |
| Assignment Rules Section | Section pattern | Combined | Step 3 of 3: define recipients |
| Add Task Button | `getByRole('button', { name: 'Add Task' })` | Role | Opens task selector |
| Timeline Preview | Timeline component | Combined | Shows task sequence visually |
| Save Button | `getByRole('button', { name: 'Save' })` | Role | Save checklist |

---

## Task List & Task Items

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Task List | `.task-list`, `[class*="task-list"]` | Class | Container of all tasks |
| Task Item | `.task-item`, `[class*="task-item"]` | Class | Individual task row |
| Task Status | `.task-status`, `[class*="task-status"]` | Class | Status indicator (Pending/Completed/Overdue) |
| Complete Task Button | `button:has-text("Complete")`, `button:has-text("Mark Complete")` | Text | Mark task as done |
| Task Checkbox | `input[type="checkbox"][class*="task"]` | Attribute | Toggle task completion |
| Optional Checkbox | `getByRole('checkbox', { name: 'Optional' })` | Role | Mark task skippable |

---

## Task Detail Flyout

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Task Type Dropdown | Standard dropdown pattern | Standard | Plain, Video, Form, Document, E-signature |
| Due Date Field | Date picker pattern | Combined | Relative or fixed date |
| Chain Task Checkbox | Checkbox pattern | Role | Create sequential dependency |
| Assignee Field | Search + autocomplete | Combined | Employee search pattern |

---

## Onboarding Portal

| Component | Selector | Type | Notes |
|-----------|----------|------|-------|
| Portal Widget Area | Portal container | Combined | Displays portal content |
| Task Checklist (Employee View) | Checklist pattern | Combined | Employee sees their assigned tasks |
| Document Upload | File upload pattern | Combined | Employee uploads required docs |
| E-signature Field | Signature pad | Combined | Employee signs documents |

---

## Module-Specific Gotchas

### Checklist triggers based on hire date
Checklists auto-trigger when an employee's start date matches the configured trigger. If testing checklist assignment, ensure the employee has the correct start date.

### Task types affect UI
Different task types (Plain, Video, Form, Document, E-signature, Chained) render different UI components. Check task type before asserting on specific UI elements.

### I-9 Section 2 dependency
I-9 Section 2 (employer) is NOT visible until the employee completes Section 1. This is expected behavior, not a bug.

### Prehire portal access
Prehire employees can only see the onboarding portal, not the full application. Test portal functionality with a prehire account.
