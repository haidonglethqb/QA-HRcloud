# Offboard Module

**Support URL**: https://support.hrcloud.com/en/help-center/offboard  
**Total Articles**: 4  
**App URL**: `/offboard`

---

## Overview

The Offboard module manages the **employee separation process** - from triggering termination to managing the offboarding checklist tasks. It ensures all exit steps are completed (equipment return, account deactivation, final documentation).

### Key Capabilities
- Offboarding checklist templates
- Terminate individual employees
- Bulk terminate multiple employees
- Tracks what happens post-termination

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Offboard Dashboard | Sidebar -> Offboard OR `/offboard` |
| Offboard Checklists | Offboard -> "Checklists" tab |
| Terminate Employee | People -> Employee Profile -> "Change Status" -> "Terminate" |
| Bulk Terminate | People -> Select employees -> "Bulk Actions" -> "Terminate" |

---

## Termination Process

### Step-by-step Termination Flow
1. Navigate to the employee's profile in **People** module
2. Click the **"Change Employment Status"** or **"..."** menu  
3. Select **"Terminate"**
4. Fill in:
   - **Termination Date**
   - **Termination Reason** (resignation, termination, retirement, etc.)
   - Whether to **revoke system access immediately** or on termination date
5. Confirm termination
6. Offboard checklist (if configured) triggers automatically

### What Happens After Termination
- Employee account is deactivated on the specified date
- Employee cannot log in after termination date
- Employee's data is retained in the system (not deleted)
- Offboarding tasks are assigned to the employee and/or HR/manager
- Employee appears in "Inactive" list in People module
- If the employee has pending Time Off requests, they need to be resolved
- Integration sync (e.g., ADP, payroll) may be triggered

### Bulk Termination
- Select multiple employees from People list
- Choose "Terminate" from bulk actions
- Each employee gets the same termination reason/date
- CSV upload also supported for bulk termination data

---

## Offboarding Checklists

- Similar structure to Onboard checklists
- Can include tasks for: equipment return, exit interview, account deactivation, final pay documents
- Trigger: automatically on termination OR manually
- Tasks assigned to: the departing employee, their manager, HR, IT
- The employee can still access their offboard portal until their termination date

---

## Rehiring After Termination

- Go to People -> Inactive employees -> Find the employee
- Click **"Rehire"** action
- Fill in new start date and employment details
- A **Rehire checklist** (if configured in Onboard) is triggered automatically

---

## Key Business Rules

- **Access revocation**: Can be set to happen immediately or on the exact termination date
- **Offboard portal**: The employee gets access to the offboard portal with their assigned tasks
- **Data retention**: Terminated employees' records are kept (GDPR compliance settings in Settings -> Privacy)
- **Pay stubs**: If payroll is integrated, final pay information syncs with the payroll system
- **I-9**: I-9 records are retained as required by law

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

