# Test Data Naming Conventions

> Use these patterns when creating records during tests. Clear naming enables easy identification and cleanup.

---

## Record Naming Pattern

All test records **must** use the `[TEST]` prefix followed by a descriptive name and unique suffix.

```
Pattern:  [TEST] {Description} {UniqueID}
```

---

## Per-Record-Type Rules

| Record Type | Pattern | Example |
|-------------|---------|---------|
| Test employee | `[TEST] First Last` | `[TEST] John Smith` |
| Test job posting | `[TEST] Job Title` | `[TEST] QA Engineer` |
| Test checklist | `[TEST] Checklist Name` | `[TEST] QA Onboard` |
| Test channel | `[TEST] Channel Name` | `[TEST] QA Channel` |
| Test portal | `[TEST] Portal_{timestamp}` | `[TEST] Portal_20260611143025` |
| Test time off policy | `[TEST] Policy Name` | `[TEST] Vacation Policy` |
| Test performance cycle | `[TEST] Cycle Name` | `[TEST] Q2 Review` |
| Test asset | `[TEST] Asset Name` | `[TEST] Laptop Dell XPS` |
| Test shift template | `[TEST] Shift Name` | `[TEST] Morning Shift` |

---

## Email Pattern for Test Employees

```
Pattern:  test{shortID}@example.com
Example:  testlc3g4h8kf2a@example.com
```

> Use `@example.com` domain — it is an IANA-reserved domain that will never receive real email.

---

## When Using Timestamps

For records that need to be unique across multiple test runs:

```
Pattern:  {RecordType}_{YYYYMMDDHHmmss}
Example:  Portal_20260611143025
          CL_20260611143025
          Channel_20260611143025
```

---

## Cleanup Rules

1. **Before each test suite**: Search for `[TEST]` records older than 7 days → delete.
2. **After each test**: Delete records created during the test (or document what was created).
3. **Never delete** records without the `[TEST]` prefix — those may be real data.

---

## ✅ DO / ❌ DON'T

### ✅ DO:
- Use `[TEST]` prefix for all test records
- Use unique suffixes (shortID or timestamp) to avoid conflicts
- Use `@example.com` for test email addresses
- Document any test data that was NOT cleaned up

### ❌ DON'T:
- Reuse the same employee name across tests (causes conflicts)
- Use real employee names or emails
- Skip cleanup of test data
- Use production data in test environments
- Create records without `[TEST]` prefix (impossible to identify for cleanup)
