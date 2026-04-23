# Onboard Checklists and Tasks

Use this topic for checklist structure, assignment logic, task behavior, and completion states.

## Checklist Types

| Type | Trigger | Notes |
|------|---------|-------|
| **Standard** | Employee start date | Auto-triggered when hire date arrives |
| **Recurring** | Calendar-based | Repeats on schedule (quarterly, annual) |
| **Mandatory** | Always runs | Cannot be skipped |
| **No Trigger** | Manual only | Admin must manually assign |
| **Rehire** | On rehire event | Triggered when terminated employee is rehired |

## Task Types

| Type | Description |
|------|-------------|
| **Plain Task** | Simple to-do item, mark complete |
| **Form Task** | Employee must fill out and submit an e-form |
| **Download Document** | Employee must download a document |
| **E-Signature** | Employee must sign a form/document |
| **Upload Document** | Employee must upload a file |
| **Video** | Employee must watch a video |
| **Chained Task** | Sequence of tasks - next unlocks when previous is done |

## Task States

| Status | Meaning |
|--------|---------|
| **Pending** | Assigned but not yet started/completed |
| **In Progress** | Actively being worked on |
| **Completed** | Employee marked done (or was auto-completed) |
| **Overdue** | Past due date and not completed |
| **Cancelled** | Admin cancelled the task |
| **Optional / Skipped** | Task was optional and employee skipped |

`Pending` specifically means the task has been assigned but is waiting on a previous chained task, or is a countersignature waiting on the first signer.

## Checklist Assignment

- Checklists auto-trigger based on hire date, rehire date, or recurring schedule.
- Admin can also manually assign a checklist to any employee.
- Individual tasks from a checklist can be manually assigned outside the automated flow.

## Task Management

- Due dates can be relative to hire date or fixed dates.
- Reminders and overdue alerts can be configured.
- Tasks can be reassigned to a different employee.
- Individual tasks or entire checklists can be cancelled.
- Chained tasks enforce sequence; task B stays hidden until task A is completed.
