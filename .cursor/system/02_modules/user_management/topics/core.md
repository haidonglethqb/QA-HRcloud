# User Management Module

**Support URL**: https://support.hrcloud.com/en/help-center/user-management  
**Total Articles**: 13  
**App URL**: `/settings/users`

---

## Overview

User Management controls **who has access to HRcloud and what they can do**. This is where admins manage access levels, roles, and permissions for all users in the system.

### Key Capabilities
- Invite new users
- Assign and manage roles (Admin, HR Manager, Manager, Employee, Custom)
- Create custom roles with granular permissions
- Manage which modules each user or role can access
- Employee Groups for department or location-based access control
- SSO (Single Sign-On) configuration
- 2FA (Two-Factor Authentication) enforcement
- Password policy configuration
- Activity log and access audit

---

## Navigation Paths

| Action | Navigation |
|--------|-----------|
| User Management | Settings -> "Users" section OR `/settings/users` |
| Roles & Permissions | Settings -> "Security" -> "Roles" |
| Invite User | Settings -> Users -> "Invite User" button |
| Create Custom Role | Settings -> Security -> Roles -> "Create Role" |
| Employee Groups | Settings -> "Employee Groups" |
| SSO Settings | Settings -> Security -> SSO |
| 2FA Settings | Settings -> Security -> 2FA |

---

## Topic Files

- [roles and access](./roles_and_access.md): built-in roles, custom roles, access hierarchy, and employee groups.
- [identity and security](./identity_and_security.md): invitations, employee vs. user rules, SSO, 2FA, and password policy.

## Test-Critical Rules

- Roles define module and action access, but Employee Groups further restrict visible employee data.
- Custom roles can combine granular permissions across modules.
- `Employee` and `User` are related but not identical concepts.
- SSO can disable password login unless admin explicitly re-enables it.
- 2FA and password policy settings change login and recovery behavior system-wide.

---

## Appendix

- Full article list moved to keep this module focused on test-critical behavior and business rules.
- Article index: [article appendix](../appendix/articles.md).

