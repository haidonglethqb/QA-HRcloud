# User Management Roles and Access

Use this topic for built-in roles, custom roles, access hierarchy, and employee-group visibility.

## Built-in Roles

| Role | Access Level |
|------|-------------|
| **Admin** | Full access to everything - all modules, all settings, all employees |
| **HR Manager** | Access to HR-focused modules such as People, Onboard, Offboard, Time Off, Perform, and Recruit |
| **Manager** | Access to direct reports and approval workflows |
| **Employee** | Access to own profile, own time off, own tasks, and Workmates |
| **Recruit User** | Access to Recruit only |
| **Time Clock Manager** | Access to Time Clock management |

## Custom Roles

- Admins can create custom roles with per-module and per-action permissions.
- Example: `Payroll Specialist` can get Time Clock and People reporting access only.
- Permissions are granular: view, add, edit, and delete by module.

## Access Control Hierarchy

1. Role defines accessible modules and actions.
2. Employee Group restricts which employees' data can be seen.
3. The final result is the intersection of role permissions and group scope.

## Employee Groups

- Employees can be grouped by department, location, employment type, or custom criteria.
- Managers or HR users can be limited to a specific group.
- Example: a regional HR manager sees only employees in that region.
