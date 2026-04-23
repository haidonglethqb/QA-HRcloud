# INDEX — HRcloud System Knowledge Base

Concise map of all files in the `.cursor/system/` directory.

## Entry Points

- `Guidance.md` — main router for full-context tasks
- `MINIMAL_QUICKSTART.md` — low-token bootstrap for simple browsering and bug verification
- `INDEX.md` — this file

## File Tree

```text
.cursor/system/
├── Guidance.md
├── MINIMAL_QUICKSTART.md
├── INDEX.md
├── 00_setup/
│   ├── README.md
│   ├── env_config.md
│   └── playwright_setup.md
├── 01_navigation/
│   ├── README.md
│   ├── common_selectors.md
│   └── url_map.md
├── 02_modules/
│   ├── advanced/
│   ├── assets/
│   ├── hr_cloud_settings/
│   ├── integrations/
│   ├── mobile_app/
│   ├── offboard/
│   ├── onboard/
│   ├── people/
│   ├── perform/
│   ├── recruit/
│   ├── security/
│   ├── shift_planner/
│   ├── time_clock/
│   ├── time_off/
│   ├── user_management/
│   └── workmates_kudos/
├── 03_workflows/
│   ├── README.md
│   ├── employee_lifecycle.md
│   ├── performance_cycle.md
│   └── time_and_attendance.md
├── 04_roles_permissions/
│   ├── README.md
│   └── role_matrix.md
└── 05_testing_guidelines/
    ├── README.md
    ├── bug_verification_rules.md
    └── test_execution_rules.md
```

## Module Folder Pattern

Every folder in `02_modules/` follows the same shape:

```text
02_modules/<module>/
├── README.md
├── topics/
│   └── core.md
└── appendix/
    └── articles.md
```

Use `README.md` as the module entry point. Read `topics/core.md` for business rules and test-critical behavior. Read `appendix/articles.md` only when you need the full Help Center article list.

## Module Article Counts (from HRcloud Help Center)

| Module | Entry point | Articles | Support URL |
|--------|-------------|----------|-------------|
| Workmates & Kudos | `02_modules/workmates_kudos/README.md` | 58 | https://support.hrcloud.com/en/help-center/workmates-kudos |
| People | `02_modules/people/README.md` | 44 | https://support.hrcloud.com/en/help-center/people |
| Onboard | `02_modules/onboard/README.md` | 46 | https://support.hrcloud.com/en/help-center/onboard |
| Offboard | `02_modules/offboard/README.md` | 4 | https://support.hrcloud.com/en/help-center/offboard |
| Recruit | `02_modules/recruit/README.md` | 32 | https://support.hrcloud.com/en/help-center/recruit |
| Time Off | `02_modules/time_off/README.md` | 17 | https://support.hrcloud.com/en/help-center/time-off |
| Perform | `02_modules/perform/README.md` | 14 | https://support.hrcloud.com/en/help-center/perform |
| Time Clock | `02_modules/time_clock/README.md` | 4 | https://support.hrcloud.com/en/help-center/time-clock |
| Assets | `02_modules/assets/README.md` | 6 | https://support.hrcloud.com/en/help-center/assets |
| Shift Planner | `02_modules/shift_planner/README.md` | 3 | https://support.hrcloud.com/en/help-center/shift-planner |
| User Management | `02_modules/user_management/README.md` | 13 | https://support.hrcloud.com/en/help-center/user-management |
| HR Cloud Settings | `02_modules/hr_cloud_settings/README.md` | 35 | https://support.hrcloud.com/en/help-center/hr-cloud-settings |
| Integrations | `02_modules/integrations/README.md` | 56 | https://support.hrcloud.com/en/help-center/integrations |
| Mobile App | `02_modules/mobile_app/README.md` | 4 | https://support.hrcloud.com/en/help-center/mobile-app |
| Advanced | `02_modules/advanced/README.md` | 18 | https://support.hrcloud.com/en/help-center/advanced |
| Security | `02_modules/security/README.md` | 1 | https://support.hrcloud.com/en/help-center/security |
| **TOTAL** |  | **355** | |

Centralized module article appendices are no longer used. Appendix article lists now live under each module folder.
