# Role â†’ Module â†’ Permission Matrix

> Use this to determine which account to use for a given test.

## Role Definitions

| Role | Description |
|------|-------------|
| **Admin** | Full system access, all modules, all employees, all settings |
| **HR Manager** | Full HR access, all employees, no billing/security settings |
| **Manager** | Limited to direct reports' data + approval actions |
| **Employee** | Own data only â€” own profile, own time off, own tasks |
| **Recruit User** | Recruit module only |
| **Custom** | Configurable â€” depends on company setup |

---

## Module Access Matrix

| Module | Admin | HR Manager | Manager | Employee | Recruit User |
|--------|-------|-----------|---------|----------|-------------|
| **Dashboard** | âœ… | âœ… | âœ… | âœ… | âœ… |
| **Workmates Feed** | âœ… | âœ… | âœ… | âœ… | âœ… |
| **Workmates Admin** | âœ… | âš ï¸ partial | âŒ | âŒ | âŒ |
| **Kudos Settings** | âœ… | âš ï¸ partial | âŒ | âŒ | âŒ |
| **People - View All** | âœ… | âœ… | âš ï¸ own team | âŒ | âŒ |
| **People - Edit** | âœ… | âœ… | âš ï¸ own team | âŒ | âŒ |
| **People - Add Employee** | âœ… | âœ… | âŒ | âŒ | âŒ |
| **Onboard - View** | âœ… | âœ… | âš ï¸ own team | âœ… own tasks | âŒ |
| **Onboard - Create Checklists** | âœ… | âœ… | âŒ | âŒ | âŒ |
| **Offboard** | âœ… | âœ… | âŒ | âŒ | âŒ |
| **Recruit** | âœ… | âœ… | âŒ | âŒ | âœ… |
| **Time Off - View Team** | âœ… | âœ… | âœ… own team | âŒ | âŒ |
| **Time Off - Approve/Deny** | âœ… | âœ… | âœ… own team | âŒ | âŒ |
| **Time Off - Request (Own)** | âœ… | âœ… | âœ… | âœ… | âŒ |
| **Time Off - Policies** | âœ… | âœ… | âŒ | âŒ | âŒ |
| **Perform - View Cycle** | âœ… | âœ… | âœ… | âœ… own | âŒ |
| **Perform - Create Cycle** | âœ… | âœ… | âŒ | âŒ | âŒ |
| **Perform - Complete Review** | âœ… | âœ… | âœ… for direct reports | âœ… self only | âŒ |
| **Perform - Analytics** | âœ… | âœ… | âš ï¸ own team | âŒ | âŒ |
| **Time Clock - View Team** | âœ… | âœ… | âœ… own team | âŒ | âŒ |
| **Time Clock - Approve Timesheets** | âœ… | âœ… | âœ… own team | âŒ | âŒ |
| **Time Clock - Clock In/Out** | âœ… | âœ… | âœ… | âœ… | âŒ |
| **Assets** | âœ… | âœ… | âŒ | âŒ | âŒ |
| **Shift Planner** | âœ… | âœ… | âœ… | âœ… view only | âŒ |
| **Settings - Company** | âœ… | âŒ | âŒ | âŒ | âŒ |
| **Settings - Users** | âœ… | âŒ | âŒ | âŒ | âŒ |
| **Settings - Integrations** | âœ… | âŒ | âŒ | âŒ | âŒ |
| **Settings - Security** | âœ… | âŒ | âŒ | âŒ | âŒ |
| **Settings - Each Module** | âœ… | âœ… | âŒ | âŒ | âš ï¸ Recruit only |
| **Reports** | âœ… | âœ… | âš ï¸ own team | âŒ | âŒ |
| **Org Chart - View** | âœ… | âœ… | âœ… | âœ… (if enabled) | âŒ |
| **Employee Directory** | âœ… | âœ… | âœ… | âœ… (if enabled) | âŒ |

**Legend**: âœ… Full Access | âš ï¸ Partial/Conditional | âŒ No Access

---

## Key Role-Based Behaviors

### Manager Role â€” Critical Notes
- Manager sees **ONLY their direct reports** in all modules
- If a manager has no direct reports, the "Team" view is empty
- Manager CANNOT see employees from other departments UNLESS they have been added to an Employee Group that includes those employees
- Manager approval for time off is only for **their direct reports** â€” another employee's request won't appear in their queue

### Employee Role â€” Important Limitations
- Employee sees ONLY their own profile data
- Employee CANNOT see other employees' Time Off requests (only their own)
- Employee CAN see the employee directory (unless directory is disabled)
- Employee's Workmates access depends on settings (can be restricted)
- Employee can request Time Off but NOT approve their own requests

### HR Manager Role â€” Key Differences from Admin
- Cannot access billing/subscription settings
- Cannot manage user roles (in some configurations)
- Full access to all employee data across all departments

---

## Actions Requiring Specific Roles (Test Preconditions)

| Action | Minimum Role Needed |
|--------|-------------------|
| Add a new employee | HR Manager |
| Terminate employee | HR Manager or Admin |
| Create onboard checklist | HR Manager |
| Approve time off | Manager (for their team) or HR Manager/Admin |
| Create performance cycle | HR Manager or Admin |
| Change settings | Admin |
| Manage integrations | Admin |
| Create user roles | Admin |
| View all employees | HR Manager |
| Add a job posting | Recruit User or HR Manager |
| Run reports | HR Manager (own team: Manager) |
| Adjust Time Off balance | HR Manager or Admin |

---

## Test Account Setup Recommendations

| Test Scenario | Account to Use |
|---------------|---------------|
| Testing admin-only settings | Admin account |
| Testing employee self-service (time off request, profile editing) | Employee account |
| Testing manager approval workflows | Manager account WITH configured direct reports |
| Testing Recruit features | Recruit User OR HR Manager account |
| Testing cross-module flows (hire â†’ onboard) | Admin account |
| Testing role-based visibility (what employee can/cannot see) | Employee account + Admin to verify |

