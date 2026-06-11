# Test Accounts — Role-Based

> Use this file to select the correct test account for a given test scenario.
> Cross-reference with `../04_roles_permissions/role_matrix.md` for detailed module access.

---

## Account Template

All credentials are stored as environment variables. **Never hardcode passwords in test files or documentation.**

```bash
# .env or environment variable pattern
HRCLOUD_<ROLE>_EMAIL=user@company.hrcloud.com
HRCLOUD_<ROLE>_PASS=<secure password>
```

---

## HR Admin Accounts

| Variable | Display Name | Role | Permissions | Use Case |
|----------|-------------|------|-------------|----------|
| `HRCLOUD_ADMIN` | Primary Admin | Admin | Full system access, all modules, all settings | Admin-only settings, integrations, security |
| `HRCLOUD_HR_MANAGER` | HR Manager | HR Manager | Full HR access, all employees, no billing/security | Standard HR operations, employee management |

---

## Manager Accounts

| Variable | Display Name | Role | Permissions | Use Case |
|----------|-------------|------|-------------|----------|
| `HRCLOUD_MANAGER` | Department Manager | Manager | Direct reports only, approval actions | Approval workflows, team view testing |
| `HRCLOUD_MANAGER_NO_REPORTS` | Manager (No Reports) | Manager | Manager role but no direct reports | Edge case: empty team view |

---

## Employee Accounts

| Variable | Display Name | Role | Permissions | Use Case |
|----------|-------------|------|-------------|----------|
| `HRCLOUD_EMPLOYEE` | Standard Employee | Employee | Own data only — profile, time off, tasks | Self-service testing, employee portal |
| `HRCLOUD_PREHIRE` | Prehire Employee | Employee (Prehire) | Onboarding portal only | Prehire portal, onboarding task completion |

---

## Recruit Accounts

| Variable | Display Name | Role | Permissions | Use Case |
|----------|-------------|------|-------------|----------|
| `HRCLOUD_RECRUIT_USER` | Recruit User | Recruit User | Recruit module only | Job posting, applicant management |

---

## Special-Purpose Accounts

| Variable | Display Name | Purpose | Notes |
|----------|-------------|---------|-------|
| `HRCLOUD_IMPERSONATE_TARGET` | Impersonation Target | Target for impersonation tests | Must be an active employee |
| `HRCLOUD_PASSWORD_RESET` | Password Reset Target | Password reset flow testing | `password: undefined` — no stored password |

---

## Which Account to Use?

| Test Scenario | Account to Use | Why |
|---------------|---------------|-----|
| Admin-only settings (security, billing) | `HRCLOUD_ADMIN` | Only Admin has Settings access |
| Creating/editing employees | `HRCLOUD_HR_MANAGER` | HR Manager has full People access |
| Approving time off requests | `HRCLOUD_MANAGER` | Manager approves for direct reports |
| Requesting time off (self) | `HRCLOUD_EMPLOYEE` | Employee self-service |
| Completing onboarding tasks | `HRCLOUD_PREHIRE` | Prehire sees onboarding portal |
| Recruit/hiring flow | `HRCLOUD_RECRUIT_USER` | Dedicated recruit role |
| Testing role visibility (what employee sees vs admin) | Both `HRCLOUD_EMPLOYEE` + `HRCLOUD_ADMIN` | Compare views |
| Cross-module flows (hire → onboard → offboard) | `HRCLOUD_ADMIN` | Needs access across all modules |
| Impersonation testing | `HRCLOUD_ADMIN` → impersonate `HRCLOUD_IMPERSONATE_TARGET` | Admin impersonates employee |

---

## Credential Security Rules

1. **Never commit `.env` files** to Git — add to `.gitignore`.
2. **Use `.env.example`** with placeholder values as a template for the team.
3. **Rotate test passwords** periodically.
4. **Do not reuse production credentials** in test environments.
5. Load credentials via environment variables or a secure vault.
