# Setup Overview & Preconditions

> AI Agent: Read this file BEFORE attempting any action on HRcloud.

## Pre-conditions Checklist

Before executing any test or verification:

- [ ] **Browser**: Chromium/Chrome (Playwright default), viewport 1440x900 minimum
- [ ] **Network**: Stable internet connection to reach `app.hrcloud.com`
- [ ] **Account**: At least one test account with appropriate role loaded (see `env_config.md`)
- [ ] **Module Access**: Confirm the test account has access to the module under test (see `../04_roles_permissions/role_matrix.md`)
- [ ] **Clean State**: Start each test from logged-out state or from a fresh navigation to base URL

## Environment Files

| File | Purpose |
|------|---------|
| [`env_config.md`](./env_config.md) | All environment URLs, account details, and settings |
| [`playwright_setup.md`](./playwright_setup.md) | How to configure and use Playwright MCP |

## Critical Gotchas

1. **Session Timeout**: HRcloud auto-logs out idle sessions. Check session validity before long test sequences.
2. **Role-based UI**: Different roles see different menus and options. Always note which role you're logged in as.
3. **Module Availability**: Not all modules are enabled for all accounts. The agent should check module visibility before testing.
4. **ADP/Integration Screens**: Some screens have overlapping UI with integration partner systems. These behave differently.
5. **Prehire vs Employee**: There's a distinction between "prehire" (pre-start date) and active "employee" states — many forms differ.
