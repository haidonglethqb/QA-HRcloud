# Testing Guidelines Overview

> This folder provides rules and protocols for AI agents executing tests or verifying bugs in HRcloud using Playwright MCP.

## Contents

| File | Purpose |
|------|---------|
| [`test_execution_rules.md`](./test_execution_rules.md) | Rules for executing test steps accurately |
| [`bug_verification_rules.md`](./bug_verification_rules.md) | Protocol for verifying reported bugs |

## Golden Rules for the Agent

1. **ALWAYS take screenshots** at critical steps — before AND after major actions
2. **NEVER use `page.waitForTimeout()`** — use element-based or network-based waits
3. **CHECK role first** — if a UI element isn't visible, check the role matrix before calling it a bug
4. **LOG everything** — capture URLs, element states, and error messages in your output
5. **VERIFY state changes** — after clicking "Save", confirm the data actually saved
6. **CLEAN UP after tests** — reverse any data changes you made (or note what data was created)
