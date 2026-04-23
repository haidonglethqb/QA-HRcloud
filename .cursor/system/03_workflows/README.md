# Workflow Overview

> This folder documents common end-to-end user flows in HRcloud that span multiple modules.

## Why Workflows Matter for Testing

Many bugs occur at **module boundaries** — when data flows from one module to another. Understanding key workflows helps agents:
- Set up the correct test preconditions
- Verify data propagates correctly between modules
- Identify which modules need to be checked after an action

## Workflow Files

| File | Workflow | Modules Involved |
|------|---------|-----------------|
| [`employee_lifecycle.md`](./employee_lifecycle.md) | Hire → Onboard → Offboard | People, Onboard, Offboard, Recruit |
| [`time_and_attendance.md`](./time_and_attendance.md) | Time Off request + Time Clock | Time Off, Time Clock, Payroll |
| [`performance_cycle.md`](./performance_cycle.md) | Performance review cycle | Perform, People |

## Cross-Module Data Dependencies

```
Recruit (Hire applicant)
    ↓
People (Employee record created)
    ↓
Onboard (Checklist auto-triggered)
    ↓ (runs in parallel with)
Time Off (Policy auto-assigned)
    ↓
Perform (Added to performance cycle)
    ↓
Offboard (On termination)
    ↓
Payroll Integration (Termination synced)
```
