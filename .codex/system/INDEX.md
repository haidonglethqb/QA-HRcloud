# INDEX â€” HRcloud System Knowledge Base

Concise map of all files in the `.codex/system/` directory.

## Entry Points

- `Guidance.md` â€” main router for full-context tasks
- `MINIMAL_QUICKSTART.md` â€” low-token bootstrap for simple browsering and bug verification
- `INDEX.md` â€” this file

## File Tree

```text
.codex/system/
â”œâ”€â”€ Guidance.md
â”œâ”€â”€ MINIMAL_QUICKSTART.md
â”œâ”€â”€ INDEX.md
â”œâ”€â”€ 00_setup/
â”‚   â”œâ”€â”€ README.md
â”‚   â”œâ”€â”€ env_config.md
â”‚   â””â”€â”€ playwright_setup.md
â”œâ”€â”€ 01_navigation/
â”‚   â”œâ”€â”€ README.md
â”‚   â”œâ”€â”€ common_selectors.md
â”‚   â””â”€â”€ url_map.md
â”œâ”€â”€ 02_modules/
â”‚   â”œâ”€â”€ advanced/
â”‚   â”œâ”€â”€ assets/
â”‚   â”œâ”€â”€ hr_cloud_settings/
â”‚   â”œâ”€â”€ integrations/
â”‚   â”œâ”€â”€ mobile_app/
â”‚   â”œâ”€â”€ offboard/
â”‚   â”œâ”€â”€ onboard/
â”‚   â”œâ”€â”€ people/
â”‚   â”œâ”€â”€ perform/
â”‚   â”œâ”€â”€ recruit/
â”‚   â”œâ”€â”€ security/
â”‚   â”œâ”€â”€ shift_planner/
â”‚   â”œâ”€â”€ time_clock/
â”‚   â”œâ”€â”€ time_off/
â”‚   â”œâ”€â”€ user_management/
â”‚   â””â”€â”€ workmates_kudos/
â”œâ”€â”€ 03_workflows/
â”‚   â”œâ”€â”€ README.md
â”‚   â”œâ”€â”€ employee_lifecycle.md
â”‚   â”œâ”€â”€ performance_cycle.md
â”‚   â””â”€â”€ time_and_attendance.md
â”œâ”€â”€ 04_roles_permissions/
â”‚   â”œâ”€â”€ README.md
â”‚   â””â”€â”€ role_matrix.md
â””â”€â”€ 05_testing_guidelines/
    â”œâ”€â”€ README.md
    â”œâ”€â”€ bug_verification_rules.md
    â””â”€â”€ test_execution_rules.md
```

## Module Folder Pattern

Every folder in `02_modules/` follows the same shape:

```text
02_modules/<module>/
â”œâ”€â”€ README.md
â”œâ”€â”€ topics/
â”‚   â””â”€â”€ core.md
â””â”€â”€ appendix/
    â””â”€â”€ articles.md
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

