# Roles & Permissions Overview

> This folder documents who can access what in HRcloud — critical for test setup and bug verification.

## Why This Matters for Testing

Before executing a test:
1. **Identify which role** the test is written for (Admin? Manager? Employee?)
2. **Log in with the correct account** (see `../00_setup/env_config.md`)
3. **Verify module visibility** — some modules are hidden if the role doesn't have access

## Role Matrix

See [`role_matrix.md`](./role_matrix.md) for the complete permission grid.

## Key Principles

- **Admin** can do everything
- **HR Manager** is similar to Admin but may lack billing/security settings access
- **Manager** can only see/manage their **direct reports** (controlled by org chart)
- **Employee** sees only their own data
- **Custom roles** can be anything in between

## Common Test Traps

> [!WARNING]
> If a test step says "Click X" and the button isn't visible — the role may not have permission. Don't report as a bug without first verifying with Admin role.

> [!NOTE]
> The **Manager** role only sees data for their **direct reports**. If a manager test account has no direct reports configured, many manager features will appear empty.
