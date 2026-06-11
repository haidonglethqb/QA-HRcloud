# Data Generators — Utility Patterns

> Patterns for generating unique test data. These are framework-agnostic — adapt the logic to your language/tool.

---

## Unique ID Generators

### Short ID (For names, emails)

Generate a short, human-readable unique string based on timestamp + random characters.

```
Pattern:  {base36_timestamp}{random_5_chars}
Example:  "lc3g4h8kf2a"
Length:   ~11 characters
```

**Usage:**
```
firstName = "Test" + shortID()        → "Testlc3g4h8kf2a"
email     = "test" + shortID() + "@example.com"  → "testlc3g4h8kf2a@example.com"
```

### GUID (For unique identifiers)

Standard UUID v4 format.

```
Pattern:  xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx
Example:  "550e8400-e29b-41d4-a716-446655440000"
```

### Timestamp ID (For record names)

Human-readable timestamp for naming portals, checklists, channels.

```
Pattern:  YYYYMMDDHHmmss
Example:  "20260611143025"
```

**Usage:**
```
portalName    = "Portal_" + timestamp()     → "Portal_20260611143025"
checklistName = "CL_" + timestamp()         → "CL_20260611143025"
```

---

## Employee Data Patterns

### Standard Employee

```
{
  firstName:  "Test" + shortID(),
  lastName:   "Employee" + shortID(),
  email:      "test" + shortID() + "@example.com",
  phone:      randomDigits(9),
  startDate:  today(),
  department: "Engineering",
  position:   "QA Engineer"
}
```

### Prehire Employee (Future Start Date)

```
{
  firstName:  "Prehire" + shortID(),
  lastName:   "Test" + shortID(),
  email:      "prehire" + shortID() + "@example.com",
  startDate:  today() + 30 days,
  status:     "Prehire"
}
```

---

## Date Generators

| Function | Format | Example | Use Case |
|----------|--------|---------|----------|
| `today()` | `MM/DD/YYYY` | `06/11/2026` | Start dates, due dates |
| `pastDate(daysBack)` | `MM/DD/YYYY` | `03/15/2026` | Termination dates, historical data |
| `futureDate(daysAhead)` | `MM/DD/YYYY` | `07/11/2026` | Prehire start dates |

---

## Password Generator

```
Pattern:  "Test1@" + random(2 chars)
Example:  "Test1@a7"
```

Meets typical password requirements: uppercase, lowercase, digit, special character, 8+ chars.

---

## Data Cleanup Strategies

### Automatic (After Each Test)

```
afterEach:
  - Delete created employees (if bulk delete available)
  - Delete created portals/checklists
  - Revert any status changes
```

### Manual (Periodic Cleanup)

```
cleanup script:
  - Find all records with "[TEST]" prefix
  - Delete records older than 7 days
  - Log what was cleaned up
```

### In-Memory State Sharing (Serial Tests)

For test suites that run in sequence, share state via suite-level variables:

```
suite "Employee Lifecycle":
  let employeeId
  
  test "Create employee":
    employeeId = createEmployee(...)
  
  test "Terminate employee":
    terminateEmployee(employeeId)
  
  test "Rehire employee":
    rehireEmployee(employeeId)
```

> ⚠️ Only use state sharing in **serial** test suites. Independent tests must NOT share state.
