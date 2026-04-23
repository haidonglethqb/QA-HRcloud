# Role → Module → Permission Matrix

> Use this to determine which account to use for a given test.

## Role Definitions

| Role | Description |
|------|-------------|
| **Admin** | Full system access, all modules, all employees, all settings |
| **HR Manager** | Full HR access, all employees, no billing/security settings |
| **Manager** | Limited to direct reports' data + approval actions |
| **Employee** | Own data only — own profile, own time off, own tasks |
| **Recruit User** | Recruit module only |
| **Custom** | Configurable — depends on company setup |

---

## Module Access Matrix

| Module | Admin | HR Manager | Manager | Employee | Recruit User |
|--------|-------|-----------|---------|----------|-------------|
| **Dashboard** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Workmates Feed** | ✅ | ✅ | ✅ | ✅ | ✅ |
| **Workmates Admin** | ✅ | ⚠️ partial | ❌ | ❌ | ❌ |
| **Kudos Settings** | ✅ | ⚠️ partial | ❌ | ❌ | ❌ |
| **People - View All** | ✅ | ✅ | ⚠️ own team | ❌ | ❌ |
| **People - Edit** | ✅ | ✅ | ⚠️ own team | ❌ | ❌ |
| **People - Add Employee** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Onboard - View** | ✅ | ✅ | ⚠️ own team | ✅ own tasks | ❌ |
| **Onboard - Create Checklists** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Offboard** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Recruit** | ✅ | ✅ | ❌ | ❌ | ✅ |
| **Time Off - View Team** | ✅ | ✅ | ✅ own team | ❌ | ❌ |
| **Time Off - Approve/Deny** | ✅ | ✅ | ✅ own team | ❌ | ❌ |
| **Time Off - Request (Own)** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Time Off - Policies** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Perform - View Cycle** | ✅ | ✅ | ✅ | ✅ own | ❌ |
| **Perform - Create Cycle** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Perform - Complete Review** | ✅ | ✅ | ✅ for direct reports | ✅ self only | ❌ |
| **Perform - Analytics** | ✅ | ✅ | ⚠️ own team | ❌ | ❌ |
| **Time Clock - View Team** | ✅ | ✅ | ✅ own team | ❌ | ❌ |
| **Time Clock - Approve Timesheets** | ✅ | ✅ | ✅ own team | ❌ | ❌ |
| **Time Clock - Clock In/Out** | ✅ | ✅ | ✅ | ✅ | ❌ |
| **Assets** | ✅ | ✅ | ❌ | ❌ | ❌ |
| **Shift Planner** | ✅ | ✅ | ✅ | ✅ view only | ❌ |
| **Settings - Company** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Settings - Users** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Settings - Integrations** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Settings - Security** | ✅ | ❌ | ❌ | ❌ | ❌ |
| **Settings - Each Module** | ✅ | ✅ | ❌ | ❌ | ⚠️ Recruit only |
| **Reports** | ✅ | ✅ | ⚠️ own team | ❌ | ❌ |
| **Org Chart - View** | ✅ | ✅ | ✅ | ✅ (if enabled) | ❌ |
| **Employee Directory** | ✅ | ✅ | ✅ | ✅ (if enabled) | ❌ |

**Legend**: ✅ Full Access | ⚠️ Partial/Conditional | ❌ No Access

---

## Key Role-Based Behaviors

### Manager Role — Critical Notes
- Manager sees **ONLY their direct reports** in all modules
- If a manager has no direct reports, the "Team" view is empty
- Manager CANNOT see employees from other departments UNLESS they have been added to an Employee Group that includes those employees
- Manager approval for time off is only for **their direct reports** — another employee's request won't appear in their queue

### Employee Role — Important Limitations
- Employee sees ONLY their own profile data
- Employee CANNOT see other employees' Time Off requests (only their own)
- Employee CAN see the employee directory (unless directory is disabled)
- Employee's Workmates access depends on settings (can be restricted)
- Employee can request Time Off but NOT approve their own requests

### HR Manager Role — Key Differences from Admin
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
| Testing cross-module flows (hire → onboard) | Admin account |
| Testing role-based visibility (what employee can/cannot see) | Employee account + Admin to verify |
