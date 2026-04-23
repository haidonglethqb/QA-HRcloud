# People Module

**Support URL**: https://support.hrcloud.com/en/help-center/people  
**Total Articles**: 44  
**App URL**: `/people`

---

## Overview

The People module is HRcloud's **core HR database** - the central record for all employees. It manages employee profiles, employment information, documents, notes, and org chart visualization.

### Key Capabilities
- Employee directory and profiles
- Add, edit, inactivate, and rehire employees
- Manage employment info (position, department, manager, start date, status)
- Documents and forms management
- Notes (private/shared)
- Tasks (assign ad-hoc tasks)
- Org chart / Company hierarchy
- Reports and custom views
- Audit trail for profile changes
- Bulk changes for multiple employees

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| Employee List | Sidebar -> People OR `/people` |
| View Employee Profile | People -> Click employee name -> `/people/:id` |
| Add New Employee | People -> "Add Employee" button (top right) |
| Org Chart | People -> "Org Chart" tab OR `/people/orgchart` |
| Reports | People -> "Reports" tab |
| Bulk Changes | People -> Select employees -> "Bulk Actions" dropdown |
| Employment Info | Employee Profile -> "Employment" tab |
| Documents | Employee Profile -> "Documents" tab |
| Notes | Employee Profile -> "Notes" tab |
| Tasks | Employee Profile -> "Tasks" tab |
| Profile Settings | Employee Profile -> "..." menu or gear icon |

---

## Key Features & Business Rules

### Employee States
- **Active**: Currently employed, has full access
- **Prehire**: Start date in the future, limited access (onboarding portal visible)
- **Inactive**: Employment ended (terminated, resigned)
- **Rehired**: Previously terminated, rehired

### Employee Profile Sections
1. **Personal Info**: Name, contact info, social networks, emergency contacts, profile photo
2. **Employment**: Job title, position, department, division, location, manager, start date, employment type, status
3. **Documents**: Files uploaded by admin/HR (private or shared with employee)
4. **Tasks**: Ad-hoc or checklist tasks assigned to the employee
5. **Notes**: Private notes (only visible to note creator) or shared
6. **Forms**: Completed e-forms (I-9, W-4, etc.)

### Important Business Rules
- **Employment changes** (position, location, department, manager): require a **change request** if using "People Full" version. Changes can be immediate or future-dated.
- **Start Date editing**: can only be changed within the allowed window
- **Inactivating**: different from terminating through Offboard - inactivating just disables the account
- **Termination**: triggered through Offboard module, not directly in People
- **Rehiring**: use "Rehire" action on inactive employee via Offboard/People
- **Impersonating**: Admins can log in as an employee to see their view (testing/debugging)
- **Audit trail**: every field change is logged with who changed, when, and what changed
- **Email change**: requires confirmation from the employee
- **Password reset**: admin can send reset email or force password reset

### Profile Completeness
- System tracks profile completeness % 
- Key fields to fill: photo, phone, address, emergency contact, social networks, and job info

### Document Privacy
- Documents can be set as: Admin-only, HR Manager visible, Employee-visible
- Each document has individual privacy settings

### Reports
- **Snapshot reports**: point-in-time view of employee data
- **Activity reports**: changes over a time period
- Custom views can be saved and set as default
- Export to CSV/Excel
- Print reports

### Global Folder Tree
- Documents can be organized in a shared folder structure
- Applies across all employees

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

