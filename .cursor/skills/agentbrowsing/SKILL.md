---
name: agentbrowsing
description: Agent browsing skill for executing test cases and verifying bugs on HRcloud using Playwright MCP. Use when the user asks to execute test steps, verify a bug, test a feature by browsing, or when in browsering mode. Loads the HRcloud system knowledge base from .cursor/system/ before any browser action.
---

# AgentBrowsing Skill

## Overview

This skill activates when the agent must **interact with the HRcloud browser** to:
- Execute test case steps
- Verify / reproduce a reported bug
- Check UI behavior by browsing the system

The agent uses **Playwright MCP tools** (`browser_navigate`, `browser_click`, `browser_type`, `browser_snapshot`, `browser_screenshot`, etc.) — NOT writing code.

---

## MANDATORY FIRST STEP — Load Knowledge Base

Before opening any browser or clicking anything, the agent MUST read the knowledge base:

### Step 1: Read Guidance.md
```
File: .cursor/system/Guidance.md
Purpose: Understand the full structure of the knowledge base and reading order
```

### Step 2: Read Setup Files
```
File: .cursor/system/00_setup/env_config.md
Purpose: Get the correct base URL, test accounts, and environment config

File: .cursor/system/00_setup/playwright_setup.md
Purpose: Know which Playwright MCP tools to use and how
```

### Step 3: Read Navigation Files
```
File: .cursor/system/01_navigation/url_map.md
Purpose: Get the correct URL for the module being tested

File: .cursor/system/01_navigation/common_selectors.md
Purpose: Get reusable selectors for common UI elements
```

### Step 4: Read ONLY the Relevant Module Entry File(s)
> ⚠️ **Read ONLY the module entry file(s) related to the current task. Do NOT read all 16 modules.**
> Identify the module from the test case or bug report, read only that module README first, then follow its topic or appendix links only when needed:

| If testing... | Read... |
|--------------|---------|
| Workmates feed, Kudos, Channels | `02_modules/workmates_kudos/README.md` |
| Employee profiles, directory | `02_modules/people/README.md` |
| Onboarding checklists, tasks, portals | `02_modules/onboard/README.md` |
| Offboarding, termination | `02_modules/offboard/README.md` |
| Recruit, ATS, job postings | `02_modules/recruit/README.md` |
| Time Off requests, policies | `02_modules/time_off/README.md` |
| Performance reviews, goals | `02_modules/perform/README.md` |
| Time Clock, timesheets | `02_modules/time_clock/README.md` |
| Asset tracking | `02_modules/assets/README.md` |
| Shift schedules | `02_modules/shift_planner/README.md` |
| Users, roles, permissions | `02_modules/user_management/README.md` |
| Settings, forms, templates | `02_modules/hr_cloud_settings/README.md` |
| Third-party integrations | `02_modules/integrations/README.md` |
| Mobile app behavior | `02_modules/mobile_app/README.md` |
| E-forms, e-signatures | `02_modules/advanced/README.md` |
| Security, 2FA, SSO | `02_modules/security/README.md` |

> Scope note: Help Center has a separate "HR Cloud API" category, but API docs are intentionally excluded from this UI browsing workflow.

### Step 5: Check Role Matrix
```
File: .cursor/system/04_roles_permissions/role_matrix.md
Purpose: Confirm which user role is required for the test
```

### Step 6: Read Testing Rules
```
For test execution → .cursor/system/05_testing_guidelines/test_execution_rules.md
For bug verification → .cursor/system/05_testing_guidelines/bug_verification_rules.md
```

### Step 7 (Optional): Read Workflow if Cross-Module
```
.cursor/system/03_workflows/employee_lifecycle.md    → hire/onboard/offboard tests
.cursor/system/03_workflows/time_and_attendance.md   → time off / time clock tests
.cursor/system/03_workflows/performance_cycle.md     → perform review tests
```

---

## Execution Protocol

### For Test Case Execution

1. **Parse the test case** — identify: preconditions, steps, expected result
2. **Load knowledge** (steps above)
3. **Login** with the correct role account from `env_config.md`
4. **Execute each step** using Playwright MCP tools, referencing `test_execution_rules.md`
5. **Screenshot at key checkpoints** — before and after each major action
6. **Compare actual vs expected** at each verification point
7. **Report** PASS/FAIL per step using the output format in `test_execution_rules.md`

### For Bug Verification

1. **Read the bug report** — extract: module, steps to reproduce, expected, actual
2. **Load knowledge** (steps above)
3. **Login** with the role mentioned in the bug report
4. **Reproduce exactly** — follow the steps from the bug report precisely
5. **Document observations** — screenshots, error messages, URLs at each step
6. **Classify**: REPRODUCED / NOT REPRODUCED / PARTIALLY REPRODUCED
7. **Report** using the template in `bug_verification_rules.md`
8. **Note locators used** — record all selectors found for later automation use

---

## Playwright MCP Tools Reference

| Tool | Use for |
|------|---------|
| `browser_navigate` | Go to a URL |
| `browser_snapshot` | Read current page state (accessibility tree) |
| `browser_screenshot` | Capture screenshot |
| `browser_click` | Click any element |
| `browser_type` | Type into input fields |
| `browser_select_option` | Select from native `<select>` dropdown |
| `browser_wait_for` | Wait for element to appear/disappear |
| `browser_hover` | Hover over element |
| `browser_check` | Check/uncheck checkbox |
| `browser_press_key` | Press keyboard keys |
| `browser_scroll` | Scroll the page |

---

## Hard Rules

1. **READ Guidance.md FIRST** — no exceptions
2. **NEVER ask the user** how to navigate — use `url_map.md`
3. **NEVER hardcode waits** — use `browser_wait_for` with element conditions
4. **ALWAYS snapshot before action** — know the state before clicking
5. **ALWAYS screenshot after action** — capture the result
6. **CHECK role_matrix.md** before reporting a missing element as a bug
   (it may simply be hidden for that role)
7. **RECORD all locators** used during the session for reuse in automation
8. **DO NOT skip steps** from the test case — follow them exactly

---

## Output Format

### Test Execution Report
```
## Test Execution Report
**Test Case**: [ID + Title]
**Date**: [date]
**Role Used**: [Admin / HR Manager / Manager / Employee]
**Environment**: [URL]

| Step | Action | Expected | Actual | Result |
|------|--------|----------|--------|--------|
| 1 | [what was done] | [expected] | [actual] | ✅ / ❌ |
| 2 | ... | ... | ... | ... |

**Overall**: PASS ✅ / FAIL ❌ / BLOCKED ⚠️

**Screenshots**: [list]
**Locators Found**: [list of selectors used]
**Notes**: [anything unusual]
```

### Bug Verification Report
```
## Bug Verification Report
**Bug/Ticket**: [ID]
**Date**: [date]
**Role Used**: [role]
**Environment**: [URL]

**Steps Executed**: [numbered list]

**Status**: REPRODUCED ✅ / NOT REPRODUCED ❌ / PARTIAL ⚠️

**Observed Behavior**: [exact description]
**Screenshots**: [list]
**Error Messages**: [any exact text]
**Locators Found**: [selectors used]
**Severity Assessment**: [Critical/High/Medium/Low + reason]
```
