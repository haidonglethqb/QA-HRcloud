---
name: bug_posting
description: Post bug tickets to the CHR Jira project using the Atlassian MCP. Use this skill whenever the user asks to log, report, or create a bug ticket. It documents all required and commonly used field IDs for the CHR project.
---

# Bug Posting Skill

## Overview

This skill handles creating Bug issues in the **CHR (Core HR)** Jira project via the Atlassian MCP tool `createJiraIssue`.

- **Cloud ID:** `74329b01-42ee-45dd-83ac-93ecd9651e5b`
- **Project Key:** `CHR`
- **Issue Type:** `Bug`

---

## MANDATORY RULE

Never post a bug directly. Always present a draft first and wait for explicit user approval before calling `createJiraIssue`. Always ask the user to review and confirm before posting.

---

## Context Requirement

Before writing a bug report, check if a related Jira story or feature link is available.

- If the user has NOT provided a story link and the bug depends on feature behavior: ask for the related Jira story link before proceeding.
- If the user provides a story link: use MCP tools to retrieve the full story details (description, acceptance criteria, comments) and align expected behavior with the story before writing.

If any required information is missing (test account, environment, steps), ask for clarification first.

---

## Step-by-Step Instructions

### Step 1 - Gather Required Information

Before creating the bug, collect the following from the user or context:

| Info Needed | Example |
| --- | --- |
| Bug summary/title | `[Module] Short description of issue` |
| Environment where bug was found | `Staging`, `Production`, `QA`, etc. |
| Affected component(s) | `Time Clock`, `Onboard`, `Perform`, etc. |
| Test account | email / password |
| Preconditions | Any required setup before reproducing |
| Steps to reproduce | Clear numbered steps |
| Expected vs Actual behavior | Based on story/requirement |
| Frequency | Always / Sometimes / Rarely |
| OS & Browser observed on | `iOS (Phone) - Chrome`, `All Browsers & OS`, etc. |
| Story link (optional) | e.g., `https://hrcloud.atlassian.net/browse/CHR-12345` |

---

### Step 2 - Look Up Sprint and Version

Always use the latest active sprint and unreleased version. Use JQL to confirm:

```
JQL: project = CHR AND sprint in openSprints() ORDER BY created DESC
```

Current values as of April 2026:
- **Sprint:** `CHR 6.54 (Active)` - sprint ID: `623`
- **Affects Version:** `CHR 6.54` - version ID: `14664`

---

### Step 3 - Map Jira Fields

#### Required Custom Fields

| Field Name | Field Key | Type | Common Values & IDs |
| --- | --- | --- | --- |
| **Reported Environment** | `customfield_10109` | Single Select | `Dev`->10119, `QA`->10120, `Staging`->10218, `Production`->10123, `UAT`->10253 |
| **Issue found in** | `customfield_10123` | Radio Button | `New Functionality`->10155, `Existing Functionality`->10156 |
| **Reported Testing Phase** | `customfield_10124` | Single Select | `Development`->10157, `Functional`->10158, `Regression`->10159, `UAT`->10160, `Post Deployment`->10161, `Existing Production Issue`->10163 |
| **Identified in OS & Browser** | `customfield_10125` | Multi Select | `All Browsers & OS`->10164, `iOS (Phone) - Chrome`->10244, `iOS (Phone) - Safari`->10254, `Android (Phone) - Chrome`->10252, `Windows 10 - Chrome`->10165, `Mac OS - Chrome`->10225 |
| **Components** | `components` | Array | See Component IDs below |
| **Affects Version** | `versions` | Array | Current: `{"id": "14664"}` (CHR 6.54) |
| **Sprint** | `customfield_10020` | Array | Current: `[{"id": 623}]` (CHR 6.54 Active) |

#### Optional But Commonly Used Fields

| Field Name | Field Key | Type | Common Values & IDs |
| --- | --- | --- | --- |
| **Issue Category** | `customfield_10122` | Single Select | `Functionality`->10144, `UI Related`->10152, `Browser Compatibility`->10147, `Data Issue`->10148, `Performance`->10149 |
| **Reproducible Environments** | `customfield_10110` | Multi Select | `Staging`->10129, `QA`->10127, `Production`->10130, `Not Verified`->10125 |

#### Assignee

Leave `assignee` unset. Jira will assign automatically based on project defaults.

---

### Component IDs (Most Common)

| Component Name | ID |
| --- | --- |
| Time Clock | 10291 |
| Mobile Web | 10260 |
| Mobile App | 10187 |
| Onboard | 10145 |
| Perform | 10258 |
| Time Off | 10194 |
| Dashboard | 10141 |
| Reports | 10150 |
| Employee | 10153 |
| Settings | 10182 |
| UI Issues | 10165 |
| Tasks | 10143 |
| Notifications | 10149 |
| Login | 10206 |

---

### Step 4 - Present Draft for Review (REQUIRED)

Before calling any Jira tool, present a full draft for user review. STOP and wait for explicit approval before posting.

---

**Bug Draft - Please review before I post:**

**Jira Fields:**

| Field | Value |
| --- | --- |
| **Summary** | `[Module] Short description` |
| **Component(s)** | e.g., Time Clock, Mobile Web |
| **Affects Version** | CHR 6.54 |
| **Sprint** | CHR 6.54 (Active) |
| **Assignee** | Automatic |
| **Reported Environment** | Staging / Production / etc. |
| **Issue Category** | UI Related / Functionality / etc. |
| **Issue Found In** | Existing Functionality / New Functionality |
| **Testing Phase** | Regression / UAT / etc. |
| **OS & Browser** | iOS (Phone) - Chrome / All Browsers & OS / etc. |
| **Linked Story** | CHR-XXXXX (if provided) |

**Description:**

```text
[Full description content - see template below]
```

Reply "post it" / "ok" / "approve" to submit, or tell me what to change.

---

Accepted approval phrases: `ok`, `post it`, `go ahead`, `approved`, `dang di`, `oke`, `duoc`, `post bug`, `xac nhan`.

If the user asks for changes, update the draft and re-present it. Repeat until approved.

---

### Step 5 - Post the Bug

Only after user approval, call `createJiraIssue`:

```json
{
  "cloudId": "74329b01-42ee-45dd-83ac-93ecd9651e5b",
  "projectKey": "CHR",
  "issueTypeName": "Bug",
  "contentFormat": "markdown",
  "summary": "[Module] Short description of the bug",
  "description": "...",
  "additional_fields": {
    "components": [{"id": "COMPONENT_ID"}],
    "versions": [{"id": "14664"}],
    "customfield_10020": [{"id": 623}],
    "customfield_10109": {"id": "10218"},
    "customfield_10123": {"id": "10156"},
    "customfield_10124": {"id": "10159"},
    "customfield_10125": [{"id": "10164"}],
    "customfield_10122": {"id": "10152"},
    "customfield_10110": [{"id": "10129"}]
  }
}
```

**If user provided a story link**, after creating the bug call `createIssueLink`:

```json
{
  "cloudId": "74329b01-42ee-45dd-83ac-93ecd9651e5b",
  "type": "Relates",
  "inwardIssue": "CHR-XXXXX",
  "outwardIssue": "CHR-BUGKEY"
}
```

---

### Step 6 - Confirm Creation

After posting, report:
- Ticket key (e.g., `CHR-48733`)
- Link: `https://hrcloud.atlassian.net/browse/CHR-XXXXX`
- Summary of fields used
- Whether the bug was linked to a story

---

## Description Template (MANDATORY FORMAT)

Severity and environment are already captured in Jira fields — do NOT repeat them in the description. Use this structure:

```markdown
## Description
[What is the issue and why it matters. Be clear and concise.]

## Preconditions
- [Required login state, role, or data setup]
- [Any configuration needed before testing]

## Steps to Reproduce
1. [Step 1 - specific action with exact field/button names]
2. [Step 2]
3. [Step 3]

## Expected Behavior
[What should happen, aligned with the story/requirement]

## Actual Behavior
[What actually happens - be precise, include error messages if any]

## Frequency
[Always / Sometimes / Rarely]
```

### Severity Reference (for Issue Category field only, not in description)

| Severity | When to use |
| --- | --- |
| Critical | System crash, data loss, security issue, complete feature blockage |
| High | Major functionality broken, affecting many users |
| Medium | Partial functionality issue, noticeable usability problem |
| Low | Minor issue with limited impact |
| Trivial | Cosmetic only, no functional impact |

---

## Notes

- Always use `contentFormat: "markdown"` for the description
- Do not set `assignee` - leave it out so Jira auto-assigns
- Always include `customfield_10020` (Sprint) with the current active sprint ID
- Do NOT put severity or environment inside the description - they belong in Jira fields
- If the bug is a mobile issue, always include both `Mobile Web` (10260) and the relevant module component
- For UI-related bugs, set `customfield_10122` to `UI Related` (id: 10152)
- If version or sprint is unclear, search using JQL before proceeding
- If user provides a story URL, extract the key and call `createIssueLink` after bug creation
- Always read the related story (if provided) before writing expected behavior
