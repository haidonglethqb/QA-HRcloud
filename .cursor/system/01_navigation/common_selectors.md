# Common Selectors — HRcloud UI Elements

> Reusable CSS selectors and Playwright locator patterns for common HRcloud UI elements.
> Always try selectors in priority order: data-testid → aria → text → class.

---

## Global / Layout

```css
/* Top navigation bar */
.top-nav, .navbar, header[class*="nav"]

/* Left sidebar */
.sidebar, .left-nav, nav[class*="sidebar"]

/* Main content area */
.main-content, .content-wrapper, main[class*="content"]

/* Loading spinner / overlay */
.spinner, .loading-overlay, [class*="loading"], [class*="spinner"]

/* Modal/Dialog */
[role="dialog"], .modal, .modal-container, [class*="modal"]

/* Modal overlay (backdrop) */
.modal-backdrop, .overlay, [class*="overlay"]

/* Toast notifications */
.toast, .notification, [class*="toast"], [class*="notification"]

/* Success toast */
.toast-success, [class*="success"][class*="toast"]

/* Error toast */
.toast-error, [class*="error"][class*="toast"]

/* Page title / H1 */
h1, .page-title, [class*="page-title"]

/* Breadcrumb */
.breadcrumb, [aria-label="breadcrumb"], [class*="breadcrumb"]

/* Action button bar */
.action-bar, .header-actions, [class*="action-bar"]
```

---

## Authentication

```css
/* Login page */
input[type="email"], input[name="email"], #email-input
input[type="password"], input[name="password"], #password-input
button[type="submit"], button:has-text("Log In"), .login-button

/* Forgot password link */
a:has-text("Forgot"), a[href*="forgot"]

/* Profile avatar (top right - for logout) */
.avatar, .user-avatar, [class*="avatar"], img[class*="profile"]

/* Logout option */
a:has-text("Log Out"), button:has-text("Sign Out")
```

---

## Common Form Elements

```css
/* Text inputs */
input[type="text"]
input[type="email"]
input[type="number"]
input[placeholder]

/* Search input */
input[type="search"], input[placeholder*="Search"], .search-input

/* Textarea */
textarea, [class*="text-area"]

/* Standard dropdown (select) */
select

/* Custom dropdown trigger */
.dropdown-toggle, [class*="dropdown-trigger"], [aria-haspopup="listbox"]

/* Dropdown menu items */
.dropdown-menu li, [role="option"], [class*="dropdown-item"]

/* Checkbox */
input[type="checkbox"], [role="checkbox"]

/* Radio button */
input[type="radio"], [role="radio"]

/* Date picker input */
input[type="date"], .date-input, [class*="date-picker"] input

/* Date picker calendar */
.date-picker-calendar, [class*="datepicker"], [class*="calendar-popup"]

/* Toggle/Switch */
.toggle, [class*="toggle"], [role="switch"]
```

---

## Buttons

```css
/* Primary action button */
button[type="submit"]
.btn-primary, [class*="btn-primary"]
button:has-text("Save")
button:has-text("Submit")
button:has-text("Create")
button:has-text("Add")

/* Secondary / Cancel button */
.btn-secondary, [class*="btn-secondary"]
button:has-text("Cancel")
button:has-text("Close")

/* Delete / Danger button */
.btn-danger, [class*="btn-danger"], [class*="delete"]
button:has-text("Delete")
button:has-text("Remove")
button:has-text("Terminate")

/* Icon-only buttons */
button[aria-label="Edit"]
button[aria-label="Delete"]
button[aria-label="Close"]
button[title="Edit"]

/* "..." or kebab menu button */
button[aria-label="More options"], .kebab-menu, [class*="more-options"]
```

---

## Tables & Lists

```css
/* Data table */
table, .data-table, [class*="data-table"]

/* Table header */
thead, th, .table-header

/* Table rows */
tbody tr, .table-row, [class*="table-row"]

/* Table cell */
td, .table-cell

/* Pagination */
.pagination, [class*="pagination"]

/* Pagination next button */
button[aria-label="Next"], .page-next, [class*="page-next"]

/* Items per page selector */
select[name="perPage"], .per-page-select
```

---

## Employee / People Module Selectors

```css
/* Employee list/directory */
.employee-list, .people-list, [class*="employee-list"]

/* Employee card */
.employee-card, [class*="employee-card"]

/* Employee name in list */
.employee-name, [class*="employee-name"]

/* Profile tabs */
.profile-tabs, [role="tablist"]

/* Profile tab item */
[role="tab"], .profile-tab, [class*="tab-item"]

/* Active profile tab */
[role="tab"][aria-selected="true"], .tab-active

/* Add employee button */
button:has-text("Add Employee"), button:has-text("New Employee")
```

---

## Onboard / Checklist Selectors

```css
/* Checklist list */
.checklist-list, [class*="checklists"]

/* Checklist card */
.checklist-card, [class*="checklist-card"]

/* Task list */
.task-list, [class*="task-list"]

/* Task item */
.task-item, [class*="task-item"]

/* Task status indicator */
.task-status, [class*="task-status"]

/* Complete task button */
button:has-text("Complete"), button:has-text("Mark Complete")

/* Task checkbox */
input[type="checkbox"][class*="task"]
```

---

## Perform / Review Selectors

```css
/* Performance cycle list */
.cycle-list, [class*="cycle-list"]

/* Review form */
.review-form, [class*="review-form"]

/* Rating stars/scale */
.rating-stars, [class*="rating"], input[type="range"]

/* Goal list */
.goal-list, [class*="goal-list"]

/* Submit review button */
button:has-text("Submit Review")
```

---

## Time Off Selectors

```css
/* Time off request button */
button:has-text("Request Time Off"), button:has-text("New Request")

/* Calendar view */
.calendar-view, [class*="calendar"]

/* Time off type dropdown */
select[name="timeOffType"], [class*="time-off-type"]

/* Date range picker */
.date-range-picker, [class*="date-range"]

/* Approve button (manager view) */
button:has-text("Approve")

/* Deny/Reject button */
button:has-text("Deny"), button:has-text("Reject")
```

---

## Workmates Selectors

```css
/* Company feed */
.company-feed, [class*="feed"]

/* Post card */
.post-card, [class*="post-card"]

/* Create post button */
button:has-text("Create Post"), button:has-text("New Post")

/* Post input area */
.post-input, textarea[placeholder*="post"]

/* Like/React button */
button[aria-label*="react"], button[aria-label*="like"], .reaction-btn

/* Comment input */
input[placeholder*="comment"], textarea[placeholder*="comment"]

/* Channel list */
.channel-list, [class*="channel-list"]

/* Kudos button */
button:has-text("Kudos"), .kudos-button
```
