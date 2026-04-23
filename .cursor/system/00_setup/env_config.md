# Environment Configuration

> Update this file with actual test credentials and environment details before running tests.

## Base URLs

| Environment | URL |
|-------------|-----|
| **Production App** | `https://hrcloud.corehr.hrcloud.com/#/Workmates/HomePage` |
| **Support / Docs** | `https://support.hrcloud.com/en/help-center` |
| **Login Page** | `https://hrcloud.corehr.hrcloud.com/Start/#/Authentication/Login?returnUrl=%23%2FMyPortal%2Fonboard%2Fcff948965812a074` |

> [!NOTE]
> If your company uses a custom subdomain (e.g., `https://yourcompany.hrcloud.com`), update the BASE_URL here.

---

## Test Accounts

| Role | Purpose | Update with actual credentials |
|------|---------|-------------------------------|
| **Admin** | Full access to all modules and settings | `admin@[company].hrcloud.com` |
| **HR Manager** | Access to People, Onboard, Time Off, Perform | `hr@[company].hrcloud.com` |
| **Department Manager** | Access to team members' data, approval workflows | `manager@[company].hrcloud.com` |
| **Employee** | Standard employee — personal profile, time off requests | `employee@[company].hrcloud.com` |

> [!IMPORTANT]
> Store credentials securely. Never commit real passwords to git. Use environment variables or a secure vault.

### Default Password Pattern

```
# Set these as environment variables before running tests
HRCLOUD_ADMIN_EMAIL=admin@yourcompany.hrcloud.com
HRCLOUD_ADMIN_PASS=YourSecurePassword
HRCLOUD_MANAGER_EMAIL=manager@yourcompany.hrcloud.com
HRCLOUD_MANAGER_PASS=YourSecurePassword
HRCLOUD_EMPLOYEE_EMAIL=employee@yourcompany.hrcloud.com
HRCLOUD_EMPLOYEE_PASS=YourSecurePassword
```

---

## Browser Settings

| Setting | Value | Notes |
|---------|-------|-------|
| Browser | Chromium | Playwright default |
| Viewport Width | 1440px | Minimum recommended |
| Viewport Height | 900px | Minimum recommended |
| Language | `en-US` | HRcloud is primarily English |
| Timezone | `America/Los_Angeles` | HRcloud default timezone |
| Headless | `false` for debug, `true` for CI | |

---

## Test Data Setup Requirements

### For People Module Tests

- At least 1 active employee record
- At least 1 inactive employee record
- Departments: HR, Engineering, Sales (or equivalent)
- Positions: Manager, Contributor (or equivalent)

### For Onboard Tests

- At least 1 prehire (employee with future start date)
- Checklists available: Standard New Hire, IT Setup (or equivalent)
- Forms: I-9 form must be available

### For Time Off Tests

- At least 1 active Time Off policy assigned
- At least 1 employee with Time Off balance > 0

### For Perform Tests

- At least 1 active Performance Cycle
- At least 1 employee with a manager assigned

### For Recruit Tests

- At least 1 active job posting
- At least 1 applicant in the pipeline

---

## Navigation Patterns

### Standard Login Flow

```
1. Navigate to: https://app.hrcloud.com/login
2. Enter email → Tab → Enter password → Click "Login"
3. Wait for dashboard to load (network idle)
4. Verify: URL contains "/dashboard" or "/home"
```

### Module Access Pattern

```
1. Click the app grid/waffle icon OR use the left sidebar
2. Modules appear as cards or sidebar items
3. Click the module name to enter
4. Wait for module home page to load
```

### Logout Flow

```
1. Click profile avatar (top right corner)
2. Click "Log Out"
3. Wait for redirect to login page
```
