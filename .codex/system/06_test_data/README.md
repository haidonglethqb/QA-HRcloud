# Test Data — Overview

> AI Agent: Read this folder when you need test accounts, data generation patterns, or naming rules for test records.

## Read Order

1. Read [`test_accounts.md`](./test_accounts.md) — role-based test accounts and when to use each.
2. Read [`data_generators.md`](./data_generators.md) — utility patterns for creating unique test data.
3. Read [`naming_conventions.md`](./naming_conventions.md) — how to name test records for easy cleanup.

## When to Use This Folder

| Situation | Read |
|-----------|------|
| Need a test account with specific role | `test_accounts.md` |
| Need to create unique employee/record names | `data_generators.md` |
| Need to name a test record (employee, checklist, job) | `naming_conventions.md` |
| Need environment URLs | `../00_setup/env_config.md` (not in this folder) |

## Relationship to Other Folders

- **00_setup/env_config.md** — environment URLs and browser settings (stay there for infra).
- **04_roles_permissions/role_matrix.md** — which modules each role can access. Cross-reference with `test_accounts.md` to pick the right account.
- **05_testing_guidelines/test_execution_rules.md** — execution protocol. Naming conventions here extend the naming section in that file.
