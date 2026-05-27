# Test Execution Rules â€” For AI Agent Using Playwright MCP

> Rules the agent MUST follow when executing test steps against HRcloud.

---

## Pre-Execution Checklist

Before starting any test:

```
[ ] 1. Read Guidance.md
[ ] 2. Read the relevant module file from 02_modules/
[ ] 3. Check 04_roles_permissions/role_matrix.md â†’ determine the required role
[ ] 4. Confirm a test account exists with that role
[ ] 5. Confirm required test data exists (employee, checklist, policy, etc.)
[ ] 6. Know the test environment URL (from 00_setup/env_config.md)
```

---

## Step-by-Step Execution Protocol

### Step 1 â€” Login
```
1.  browser_navigate  â†’ https://app.hrcloud.com/login
2.  browser_snapshot  â†’ confirm login form is visible
3.  browser_screenshot â†’ save as "01_login_page"
4.  browser_click     â†’ email input
5.  browser_type      â†’ [email]
6.  browser_click     â†’ password input
7.  browser_type      â†’ [password]
8.  browser_click     â†’ Login / Sign In button
9.  browser_wait_for  â†’ dashboard element appears
10. browser_screenshot â†’ save as "02_dashboard_logged_in"
```

### Step 2 â€” Navigate to Module
```
1. browser_navigate  â†’ [module URL from url_map.md]
2. browser_wait_for  â†’ page finishes loading
3. browser_snapshot  â†’ confirm correct page
4. browser_screenshot â†’ save as "03_module_home"
```

### Step 3 â€” Perform Action
```
1. browser_snapshot  â†’ read state before action
2. browser_click / browser_type / browser_select_option ...
3. browser_wait_for  â†’ loading spinner disappears
4. browser_snapshot  â†’ read state after action
```

### Step 4 â€” Verify Result
```
1. browser_screenshot â†’ save as "04_after_action"
2. Check via browser_snapshot:
   - Is a success toast/message visible?
   - Did the URL change as expected?
   - Has the data updated in the UI?
   - Is there an error message?
3. Record result using the output format below
```

---

## Wait Strategy â€” Most Important Rule

| Situation | How to wait |
|-----------|------------|
| After click Save/Submit | browser_wait_for spinner disappears â†’ then snapshot |
| After navigating to new page | browser_wait_for main element of new page |
| After submitting a form | browser_wait_for toast/message appears |
| Modal opens | browser_wait_for [role="dialog"] visible |
| Modal closes | browser_wait_for [role="dialog"] hidden |
| Dropdown opens | browser_snapshot â†’ confirm options are visible |

> âŒ **NEVER** assume a fixed time (no hardcoded 3-second sleeps)
> âœ… **ALWAYS** verify via snapshot or wait_for before the next action

---

## Form Interaction Rules

### Text Input
```
browser_click â†’ field
browser_type  â†’ [value]
# Then: browser_snapshot to confirm input was accepted
```

### Custom Dropdown (common in HRcloud)
```
browser_click    â†’ dropdown trigger
browser_snapshot â†’ confirm menu is open
browser_click    â†’ option to select
browser_snapshot â†’ confirm selection applied
```

### Search + Autocomplete (e.g., finding employee, manager)
```
browser_click    â†’ search field
browser_type     â†’ [keyword]
browser_wait_for â†’ autocomplete list appears
browser_snapshot â†’ confirm results visible
browser_click    â†’ desired result
```

### Date Picker
```
browser_click â†’ date field
browser_type  â†’ [YYYY-MM-DD]
# If custom date picker:
browser_click    â†’ calendar icon
browser_snapshot â†’ view months/days
browser_click    â†’ the target day
```

---

## Test Data Naming Convention

When creating records during a test, use clear names for easy cleanup:

| Record type | Pattern | Example |
|------------|---------|---------|
| Test employee | `[TEST] First Last` | `[TEST] John Smith` |
| Test job posting | `[TEST] Job Title` | `[TEST] QA Engineer` |
| Test checklist | `[TEST] Checklist Name` | `[TEST] QA Onboard` |
| Test channel | `[TEST] Channel Name` | `[TEST] QA Channel` |

---

## Output Format Per Step

After each test step, report:

```
STEP [n]: [Step description]
ACTION: [MCP tool used + element interacted with]
RESULT: âœ… PASS / âŒ FAIL / âš ï¸ BLOCKED
SCREENSHOT: [screenshot filename]
NOTES: [Anything unusual observed]
```

---

## Post-Test Checklist

```
[ ] All steps executed?
[ ] Screenshot taken at each key step?
[ ] Test data cleaned up (or documented what was created)?
[ ] PASS/FAIL result clearly recorded per step?
[ ] If FAIL: URL, error message, and screenshot captured?
```

