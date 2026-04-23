# HRcloud Minimal Quickstart

Use this path for simple browsering, smoke checks, and bug verification where you do not need the full knowledge base.

Scope note: this quickstart covers UI/browsering categories from Help Center. The separate `HR Cloud API` category is intentionally excluded.

## Minimal Read Order

1. Decide the mode:
- Test execution -> read [test_execution_rules](c:/Users/linhl/Documents/GitHub/QA-HRcloud/.cursor/system/05_testing_guidelines/test_execution_rules.md)
- Bug verification -> read [bug_verification_rules](c:/Users/linhl/Documents/GitHub/QA-HRcloud/.cursor/system/05_testing_guidelines/bug_verification_rules.md)
2. Read [env_config](c:/Users/linhl/Documents/GitHub/QA-HRcloud/.cursor/system/00_setup/env_config.md)
3. Read [url_map](c:/Users/linhl/Documents/GitHub/QA-HRcloud/.cursor/system/01_navigation/url_map.md)
4. Read the relevant module README in `02_modules/<module>/README.md`
5. Read [role_matrix](c:/Users/linhl/Documents/GitHub/QA-HRcloud/.cursor/system/04_roles_permissions/role_matrix.md)
6. If the task crosses modules, read the relevant workflow in `03_workflows/`

## Module Entry Points

| Task area | Read first |
|-----------|------------|
| Feed, Kudos, Channels, Chat | `02_modules/workmates_kudos/README.md` |
| Employee profiles, org chart, documents | `02_modules/people/README.md` |
| Checklists, tasks, portals, I-9 | `02_modules/onboard/README.md` |
| Termination, offboarding | `02_modules/offboard/README.md` |
| Applicants, jobs, offers | `02_modules/recruit/README.md` |
| Leave requests, balances, policies | `02_modules/time_off/README.md` |
| Reviews, goals, performance cycles | `02_modules/perform/README.md` |
| Clock in/out, timesheets | `02_modules/time_clock/README.md` |
| Assets and returns | `02_modules/assets/README.md` |
| Schedules and shifts | `02_modules/shift_planner/README.md` |
| Users, roles, SSO, 2FA | `02_modules/user_management/README.md` |
| Company settings, forms, imports | `02_modules/hr_cloud_settings/README.md` |
| Payroll, calendar, SSO, other integrations | `02_modules/integrations/README.md` |
| Mobile behavior | `02_modules/mobile_app/README.md` |
| E-forms, e-signatures | `02_modules/advanced/README.md` |
| Security settings | `02_modules/security/README.md` |

## Escalate Beyond Minimal Path When

- The task spans multiple modules.
- A role restriction is unclear.
- The module README points to deeper topic files.
- The issue appears to involve downstream sync or workflow behavior.