# Time Off Module

**Support URL**: https://support.hrcloud.com/en/help-center/time-off  
**Total Articles**: 17  
**App URL**: `/timeoff`

---

## Overview

The Time Off module manages **employee leave and absence** - from request submission to manager approval, accrual, and balance tracking.

### Key Capabilities
- Multiple time off types (vacation, sick, personal, etc.)
- Accrual policies with rules (monthly, weekly, per pay period)
- Employee self-service time off requests
- Manager approval workflow
- Calendar view (all employee time off visible)
- Balance tracking and adjustment
- Carryover and expiration rules
- Blackout dates (prevent time off during specific periods)
- Holiday calendar
- Reports and exports
- Integration with payroll (sync days off)
- FMLA / leave of absence tracking

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Time Off Home | Sidebar -> Time Off OR `/timeoff` |
| My Time Off | Time Off -> "My Time Off" tab (employee view) |
| Team's Requests | Time Off -> "Requests" tab (manager/admin) |
| Time Off Calendar | Time Off -> "Calendar" tab OR global Calendar |
| Time Off Policies | Time Off -> "Policies" tab (admin only) |
| Time Off Types | Time Off -> "Types" tab (admin only) |
| Balance/Grid | Time Off -> "Balance" tab (admin view) |
| Request Time Off | Time Off -> "Request" button / "+" button |
| Approve Requests | Time Off -> Requests -> Click "Approve" |
| Adjust Balance | Employee Profile -> Time Off tab -> "Adjust balance" |

---

## Key Features & Business Rules

### Time Off Types
- Examples: Vacation, Sick, Personal Day, Bereavement, FMLA
- Each type has: name, color, icon, and accrual policy
- Types can be **paid** or **unpaid**
- Types can be **carryover** (unused days roll to next year) or **use-it-or-lose-it**
- Types can be visible or hidden from employees
- Admin can create unlimited custom types

### Accrual Policies
- **Accrual schedule**: how often days accumulate (weekly, biweekly, monthly, per pay period)
- **Accrual amount**: how many hours/days per period
- **Waiting period**: employee must work X days before accrual begins
- **Max balance cap**: limit on how many days can be held at once
- **Carryover limit**: max days that carry over to next year
- **Carryover date**: when the year resets (Jan 1, hire anniversary, etc.)

### Request Flow
1. Employee clicks "Request Time Off"
2. Selects: time off type, start date, end date (or specific hours)
3. Adds optional note
4. Clicks "Submit"
5. Manager (or admin) receives notification
6. Manager approves or declines with optional comment
7. Employee receives notification of decision
8. Calendar and balance update

### Half-day and Hourly Requests
- Can request partial days (e.g., half-day, or specific hours)
- Requires the time off type to allow hourly/partial requests

### Blackout Dates
- Admin can set dates where no time off is allowed for specific groups
- Requests submitted during blackout dates are automatically blocked

### Balance Adjustments
- Admins can manually add or subtract time off balance
- Useful for one-time grants or corrections
- Each adjustment is logged with reason

### Manager Approval Delegation
- If manager is away, they can delegate approval authority to another user
- Automatic approval option: configure to auto-approve without manager action

### Holiday Calendar
- Define company holidays (no deduction from balance on holidays)
- Holidays excluded from time off day count when spanning a holiday

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

