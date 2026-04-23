# Bug Verification Rules

> Protocol for AI agents to verify reported bugs in HRcloud using Playwright MCP.

---

## Bug Verification Framework

When given a bug report to verify, follow this structured protocol:

### Step 1: Understand the Bug

Read the bug report carefully and extract:
- **Module**: Which HRcloud module is affected?
- **Feature**: Which specific feature/action?
- **Steps to Reproduce**: Exact steps listed in the bug
- **Expected Result**: What should happen
- **Actual Result**: What actually happens (the bug)
- **Role Required**: Which user role triggers the bug? (Admin? Employee? Manager?)
- **Test Data Required**: What records need to exist first?

### Step 2: Verify Preconditions Exist

```
[ ] Required test accounts exist with correct roles
[ ] Required test data exists (employees, checklists, time off policies, etc.)
[ ] Browser is fresh (clear cache if needed, or use incognito mode)
[ ] Start from the login page
```

### Step 3: Execute Reproduction Steps

Follow the exact steps from the bug report:
- **Log in as the specified role**
- **Navigate exactly as described** (use the URL map if needed)
- **Take screenshot at each step**
- **Document exactly what you see** — don't interpret, record facts

### Step 4: Compare Expected vs. Actual

| Item | Document |
|------|---------|
| URL at the time of bug | Record the full URL |
| Error messages | Capture exact text |
| Missing elements | Note what should be there but isn't |
| Wrong data | Note what was shown vs. what was expected |
| UI glitch | Screenshot clearly showing the visual issue |

### Step 5: Attempt Workarounds

Test optional variations:
- Different browsers (if browser-specific)
- Different accounts (same role, different user)
- Refreshing the page after the bug appears
- Trying a different approach to the same action

---

## Bug Severity Classification

Use these criteria when reporting your verification result:

| Severity | Criteria | Example |
|----------|---------|---------|
| **Critical** | System unusable, data loss, security issue | Login fails, employee records deleted |
| **High** | Core feature broken, no workaround | Cannot submit Time Off request |
| **Medium** | Feature partially broken, workaround exists | Sort order wrong but data still accessible |
| **Low** | UI/UX issue, cosmetic | Label truncated, icon misaligned |

---

## Verification Output Template

After completing verification, report:

```markdown
## Bug Verification Report

**Bug ID**: [Jira ticket number, e.g., CHR-12345]
**Verified On**: [Date and time]
**Environment**: [URL used, e.g., https://app.hrcloud.com]
**Browser**: [Chromium, version X]
**Role Used**: [Admin / HR Manager / Manager / Employee]
**Test Account**: [email used]

### Reproduction Steps Executed
1. [Step 1 — what I did]
2. [Step 2 — what I did]
3. [Step 3 — what I did]

### Result
**Status**: REPRODUCED ✅ / NOT REPRODUCED ❌ / PARTIALLY REPRODUCED ⚠️

**What I Observed**:
[Describe exactly what happened]

**Screenshots**:
- Step 3: [screenshot filename]
- Error visible: [screenshot filename]

### Additional Notes
[Any observations about frequency, conditions, or related issues]

### Suggested Severity
[Critical / High / Medium / Low] — [reason]
```

---

## Common Bug Categories & Verification Approach

### 1. UI Display Bug
**How to verify**:
- Navigate to the affected page
- Check if element is present/correct at multiple viewport sizes
- Screenshot the issue
- Check if it's role-dependent (test with different roles)

### 2. Form Validation Bug
**How to verify**:
- Navigate to the form
- Try submitting with: empty required field, invalid format, boundary values (max length, special chars)
- Document which validation is missing or wrong

### 3. Data Not Saving Bug
**How to verify**:
```
1. browser_navigate  → [form page URL]
2. browser_click     → field to fill
3. browser_type      → "Test Value"
4. browser_click     → Save / Submit button
5. browser_wait_for  → success indicator
6. browser_navigate  → another page
7. browser_navigate  → back to original page
8. browser_snapshot  → check if field still shows "Test Value"
   - If field is empty → data did not persist → bug confirmed
   - If field shows correct value → data saved correctly
```

### 4. Permission / Access Bug
**How to verify**:
```
1. Login as Employee → browser_snapshot → note which elements are visible
2. Login as Manager  → browser_snapshot → note which elements are visible
3. Login as Admin    → browser_snapshot → note which elements are visible
4. Compare: does each role see only what role_matrix.md says they should?
5. Document: exact role, exact element present/absent, screenshot per role
```

### 5. Integration Sync Bug
**How to verify**:
- Make a change in HRcloud (e.g., terminate employee)
- Note the timestamp
- Check the integration provider system (e.g., ADP) after expected sync delay
- Check HRcloud's integration logs: Settings → Integrations → [Provider] → Logs

### 6. Notification Bug
**How to verify**:
- Trigger the event (submit time off request, etc.)
- Check: did the notification email arrive? (if you have access to the email)
- Check: did the in-app notification appear? (bell icon in top nav)
- Document the time taken (if delayed) or if missing

---

## NOT A BUG — Common Misidentifications

> [!WARNING]
> These are behaviors that might look like bugs but are actually expected behavior:

| Scenario | Explanation |
|----------|------------|
| Manager can't see all employees | Expected — managers see only direct reports |
| Time Off balance not deducted immediately after request | Expected — balance deducts after approval |
| Prehire can't access all modules | Expected — prehire portal is restricted by design |
| Offboard tasks not assigned yet | Only assigned after termination is confirmed |
| Payroll sync not instant | Integration syncs run on scheduled intervals (hourly/nightly) |
| Changes not taking effect (People Full) | May be a future-dated change — check the effective date |
| Email not arriving immediately | Expected delay of up to 5 minutes |
| I-9 Section 2 not visible | Expected — can only fill after employee completes Section 1 |
