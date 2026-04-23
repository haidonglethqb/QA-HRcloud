# HRcloud Agent - Guidance

Read this file first. It is the router for the HRcloud knowledge base.

## Start Here

For low-token browsering tasks, start with `MINIMAL_QUICKSTART.md`.

For deeper investigations, use the read order below.

## Read Order

1. Read `00_setup/env_config.md`
2. Read `00_setup/playwright_setup.md`
3. Read `01_navigation/url_map.md`
4. Read the relevant module entry in `02_modules/<module>/README.md`
5. Read `04_roles_permissions/role_matrix.md`
6. Read the relevant file in `05_testing_guidelines/`
7. If the task crosses modules, read the relevant file in `03_workflows/`

## Module Routing

| If the task involves... | Start with... |
|-------------------------|---------------|
| Feed, Kudos, Channels, Chat | `02_modules/workmates_kudos/README.md` |
| Employee profiles, org chart, documents | `02_modules/people/README.md` |
| Checklists, tasks, portals, I-9 | `02_modules/onboard/README.md` |
| Termination, offboarding | `02_modules/offboard/README.md` |
| Applicants, jobs, offers | `02_modules/recruit/README.md` |
| Leave requests, balances, policies | `02_modules/time_off/README.md` |
| Reviews, goals, performance cycles | `02_modules/perform/README.md` |
| Clock in/out, timesheets | `02_modules/time_clock/README.md` |
| Equipment tracking | `02_modules/assets/README.md` |
| Shift scheduling | `02_modules/shift_planner/README.md` |
| Users, roles, SSO, 2FA | `02_modules/user_management/README.md` |
| Company settings, forms, imports | `02_modules/hr_cloud_settings/README.md` |
| Payroll, calendar, SSO, and third-party integrations | `02_modules/integrations/README.md` |
| Mobile behavior | `02_modules/mobile_app/README.md` |
| E-forms, e-signatures, and advanced automations | `02_modules/advanced/README.md` |
| Security settings | `02_modules/security/README.md` |

## Cross-Module Routing

| Flow | Read |
|------|------|
| Hire -> onboard -> offboard | `03_workflows/employee_lifecycle.md` |
| Time off + time clock | `03_workflows/time_and_attendance.md` |
| Performance cycles | `03_workflows/performance_cycle.md` |

## Reference Map

| Need | Read |
|------|------|
| Minimal bootstrap | `MINIMAL_QUICKSTART.md` |
| Full file tree | `INDEX.md` |
| URLs | `01_navigation/url_map.md` |
| Common selectors | `01_navigation/common_selectors.md` |
| Roles | `04_roles_permissions/role_matrix.md` |
| Test execution rules | `05_testing_guidelines/test_execution_rules.md` |
| Bug verification rules | `05_testing_guidelines/bug_verification_rules.md` |

## Missing Documentation Policy

If a user asks for an exact UI procedure and it cannot be found in `.cursor/system/` after checking this read order:

1. `Guidance.md`
2. Relevant module `README.md` and topic files
3. `01_navigation/url_map.md`
4. `04_roles_permissions/role_matrix.md`
5. Relevant file in `05_testing_guidelines/`

Then the agent must:

- Explicitly state: **"Not documented in system knowledge base."**
- List the files that were checked.
- Avoid inventing an "official" step-by-step procedure.
- Optionally provide an **exploratory** fallback and label it clearly as exploratory.
