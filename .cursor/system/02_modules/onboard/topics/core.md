# Onboard Module

**Support URL**: https://support.hrcloud.com/en/help-center/onboard  
**Total Articles**: 46  
**App URL**: `/onboard`

---

## Overview

The Onboard module manages the **new hire onboarding process** through checklists and tasks. It ensures new employees complete required forms, e-signatures, document reviews, and training steps before and after their start date.

### Key Capabilities
- Checklist templates (triggered automatically or manually)
- Task types: plain tasks, form tasks, document download, video, e-signature
# Onboard Module

**Support URL**: https://support.hrcloud.com/en/help-center/onboard  
**Total Articles**: 46  
**App URL**: `/onboard`

---

## Overview

The Onboard module manages the **new hire onboarding process** through checklists and tasks. It ensures new employees complete required forms, e-signatures, document reviews, and training steps before and after their start date.

### Key Capabilities
- Checklist templates (triggered automatically or manually)
- Task types: plain tasks, form tasks, document download, video, e-signature
- Prehire portal (employee-facing onboarding portal)
- Multiple portals for different employee types
- Bulk onboarding (multiple prehires at once)
- Smartflow (advanced conditional workflow builder)
- Watchers (additional notified parties)
- Chained tasks (sequential task dependencies)
- Buddy Program (assign a buddy to new hires)
- I-9 management (including unlock and E-Verify)

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Onboard Dashboard | Sidebar -> Onboard OR `/onboard` |
| Checklist Templates | Onboard -> "Checklists" tab |
| Create New Checklist | Onboard -> Checklists -> "Create Checklist" button |
| View Employee's Tasks | Onboard -> Click employee name OR `/onboard/employees/:id` |
| Portals | Onboard -> "Portals" tab |
| Smartflow | Onboard -> "Smartflow" tab |
| Onboard Settings | Settings -> Onboard |

---

## Topic Files

- [checklists and tasks](./checklists_and_tasks.md): checklist types, task types, task states, assignment rules, due dates, reminders, and chained task behavior.
- [portals, I-9, and Smartflow](./portals_i9_and_smartflow.md): portal behavior, I-9 flow, E-Verify, Smartflow, buddy program, watchers, and bulk onboarding.

## Test-Critical Rules

- Checklists can auto-trigger from hire date, rehire date, or recurring schedule.
- Individual tasks can be manually assigned outside automated checklist flows.
- Chained tasks do not unlock until the previous task is completed.
- `Pending` can also mean the task is blocked by a prior chained task or waiting for a countersignature.
- I-9 unlock can be requested by the employee or performed by an admin.
- Smartflow can add tasks conditionally based on employee attributes.

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).
| **Optional / Skipped** | Task was optional and employee skipped |


