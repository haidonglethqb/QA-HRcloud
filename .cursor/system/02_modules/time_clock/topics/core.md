# Time Clock Module

**Support URL**: https://support.hrcloud.com/en/help-center/time-clock  
**Total Articles**: 4  
**App URL**: `/timeclock`

---

## Overview

The Time Clock module tracks **employee working hours** - clock-in/clock-out, timesheets, project time tracking, and approval workflows.

### Key Capabilities
- Employee clock-in/clock-out (web, mobile, kiosk)
- Break tracking
- Project/job code time logging
- Timesheet management with approval workflow
- Overtime tracking and alerts
- Geofencing (location-based restrictions for clocking in)
- Integration with payroll systems
- Reports and exports

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Time Clock Home | Sidebar -> Time Clock OR `/timeclock` |
| My Timesheets | Time Clock -> "My Timesheets" tab |
| Team Timesheets | Time Clock -> "Team" tab (manager view) |
| Projects | Time Clock -> "Projects" tab |
| Kiosk | Time Clock -> "Kiosk" setup |
| Time Clock Settings | Settings -> Time Clock |

---

## Key Features & Business Rules

### Clock In/Out
- Employees clock in via: web browser, mobile app, or kiosk mode
- Kiosk mode: a shared device (tablet/computer) where employees use PIN to clock in
- **Geofencing**: restrict clock-in to a specific location radius
- **IP restriction**: only allow clock-in from specific IP addresses
- Managers can clock in/out on behalf of an employee

### Timesheets
- Each pay period generates a timesheet
- Timesheet shows all clock-in/out entries for the period
- Employees can add notes, projects to each entry
- Managers must **approve** timesheets before payroll sync
- **Approval flow**: Employee submits -> Manager reviews -> Approves or requests corrections

### Payroll Integration
- Approved timesheets sync to integrated payroll (ADP, Paychex, etc.)
- Only approved timesheets are synced
- Workers need to be matched between HRcloud and payroll system

### Overtime
- Overtime rules configured per employee or group
- Alerts when employee approaches or exceeds overtime threshold
- Daily and weekly overtime calculations

### Projects
- Time can be tracked against specific projects/job codes
- Multiple projects per timesheet entry
- Project reports show time spent per project

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

