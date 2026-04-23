# Shift Planner Module

**Support URL**: https://support.hrcloud.com/en/help-center/shift-planner  
**Total Articles**: 3  
**App URL**: `/shift-planner`

---

## Overview

The Shift Planner module enables **schedule management** for hourly and shift-based workforces - creating shift schedules, managing open shifts, and tracking coverage.

### Key Capabilities
- Visual weekly/monthly shift schedule
- Create and assign shifts to employees
- Open shifts (no specific assignment - employees claim them)
- Shift templates for recurring patterns
- Shift swaps between employees
- Manager approval for swaps
- Notifications for upcoming shifts
- Integration with Time Clock

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Shift Planner Home | Sidebar -> Shift Planner OR `/shift-planner` |
| Schedule View | Shift Planner -> "Schedule" tab |
| Open Shifts | Shift Planner -> "Open Shifts" tab |
| Create Shift | Schedule view -> Click empty slot -> "Create Shift" |
| Shift Settings | Settings -> Shift Planner |

---

## Key Features & Business Rules

### Schedule Types
- **Assigned shifts**: specific employee assigned to a shift
- **Open shifts**: any eligible employee can claim the shift
- **Recurring shifts**: same pattern repeats weekly/daily

### Shift Details
Each shift has:
- Start time, end time
- Break duration
- Position/role requirement
- Location
- Notes

### Open Shift Flow
1. Manager creates an open shift (no specific person assigned)
2. Eligible employees see the open shift and can "Claim" it
3. Manager approves or denies the claim request
4. Once approved, shift appears on employee's schedule

### Shift Swap Flow
1. Employee requests a swap with another employee
2. Both employees confirm the swap willingness
3. Manager approves or denies the swap
4. Schedule updates accordingly

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

