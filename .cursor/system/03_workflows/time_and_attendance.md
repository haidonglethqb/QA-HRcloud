# Time and Attendance Workflow

**Modules Involved**: Time Off, Time Clock, Payroll Integration

---

## Time Off Request Flow

### Employee Self-Service Request

| Step | Actor | Action | Location |
|------|-------|--------|----------|
| 1 | Employee | Click "Request Time Off" | Time Off → "My Time Off" |
| 2 | Employee | Select time off type | Dropdown (Vacation, Sick, etc.) |
| 3 | Employee | Set start + end dates (or hourly) | Date picker |
| 4 | Employee | Add note (optional) | Text field |
| 5 | Employee | Submit request | "Submit" button |
| 6 | Manager | Receives email notification | Email alert |
| 7 | Manager | Reviews request | Time Off → "Requests" → Pending |
| 8 | Manager | Approves or Denies | "Approve" / "Deny" button |
| 9 | Employee | Receives decision notification | Email |
| 10 | System | Calendar updates | Time Off calendar + personal calendar (if integrated) |
| 11 | System | Balance deducted | On the request dates |

### Manager Override (Admin submits on behalf)
1. Admin navigates to Employee profile → Time Off tab
2. Clicks "Add Time Off" or "Request on behalf"
3. Fills same fields as self-service
4. Submits → auto-approved (no approval needed since admin initiated)

### Verification Points
- ✅ Request shows in "Pending" until approved
- ✅ Calendar shows pending time off (typically grayed out or different style)
- ✅ Balance does NOT deduct until approved (for accrual policies)
- ✅ After approval: balance deducts correctly
- ✅ Manager receives email within a few minutes of request submission
- ✅ Employee receives decision email

---

## Blackout Date Behavior

**Rule**: If an employee tries to submit a request that falls on or overlaps a blackout date:
- Request is **automatically blocked** (employee sees an error message)
- Employee cannot submit the request
- Admin/manager can override if permission allows

### Verification Points
- ✅ Blackout dates visually highlighted in date picker
- ✅ Error message shown when trying to select blackout date
- ✅ Admin can still create a request during blackout if they have override permission

---

## Time Clock Flow

### Employee Clock-in / Clock-out

| Step | Actor | Action |
|------|-------|--------|
| 1 | Employee | Opens Time Clock on browser or kiosk |
| 2 | Employee | Clicks "Clock In" button |
| 3 | System | Records timestamp + optionally GPS location |
| 4 | Employee | Works shift |
| 5 | Employee | Clicks "Clock Out" |
| 6 | System | Records duration + creates timesheet entry |
| 7 | Employee | Adds project code / notes if needed |
| 8 | At period end | Employee submits timesheet |
| 9 | Manager | Reviews + approves timesheet |
| 10 | System | Syncs to payroll integration |

### Kiosk Mode Flow
1. Admin sets up a shared device as kiosk
2. Employees tap/enter their PIN to clock in
3. Display shows "Clocked In" confirmation with employee name
4. Clock-out same way

### Overlapping with Time Off
- If an employee is on approved paid time off, Time Clock entries still count (if they work)
- System does not automatically block Time Clock access during Time Off

### Verification Points
- ✅ Clock-in records exact timestamp
- ✅ Clock-out closes the entry correctly
- ✅ Timesheet shows all entries for the period
- ✅ After manager approval, timesheet is locked (no more edits)
- ✅ Payroll sync triggers after approval

---

## Balance Accrual Flow

**Every accrual period** (weekly/biweekly/monthly):
1. System calculates how many hours/days to add per policy
2. System applies waiting period check (employee must have worked X days)
3. System adds accrued amount to balance (up to max cap)
4. Balance visible to employee and admin

**Year-end carryover**:
1. On the configured reset date (Jan 1 or hire anniversary)
2. System carries over up to the configured max carryover limit
3. Any balance above the limit is forfeited

### Verification Points
- ✅ Balance increases after each accrual period (check next day)
- ✅ Balance does not exceed max balance cap
- ✅ Carryover happens on the correct date
- ✅ Excess balance above carryover limit is removed
